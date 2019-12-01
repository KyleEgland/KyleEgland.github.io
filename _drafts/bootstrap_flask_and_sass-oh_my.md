# Bootstrap, Flask, and Sass - oh my!

Learning to use Sass while leveraging Bootstrap to re-skin a Flask project.

## The Beginning
I've been getting deeper and deeper into web development - it's been quite fun to create things that can be used anywhere on any platform - and have been roughly bending Bootstrap to my will through custom CSS files imported after Bootstrap:

__My typical `base.html` header__

```html
{# Bootstrap #}
<link rel="stylesheet" href="{{ url_for('static', filename='css/bootstrap/bootstrap.min.css') }}">
{# FontAwesome #}
<link rel="stylesheet" href="{{ url_for('static', filename='css/fontawesome/css/all.css') }}">
{# Global Stylesheet #}
<link rel="stylesheet" href="{{ url_for('static', filename='css/global/style.css') }}">
{# favicon inclusion - Should you have one #}
<link rel="shortcut icon" href="{{ url_for('static', filename='favicon/favicon.ico') }}">
{# Website manifest - Should you have one #}
<link rel="manifest" href="{{ url_for('static', filename='favicon/site.webmanifest')}}">
```

While this works ok it is rather cumbersome (not all the overrides are obvious...), Bootstrap 4 is written in Sass, and can be re-compiled with different values to provide different styling customized to a project.  After some searching I came across a tutorial to explain how to achieve this and a Python module with which to execute (see credits below for attribution).  The tutorial found wasn't written with Python/Flask in mind so this is my assimilation of the material (the below documentation), please to enjoy :)

## Getting Started
Assumptions made:

* You understand and have installed Python 3
* You have a Flask project
    * You already have an understanding of Flask
* You have some knowledge of HTML/CSS and how to use Bootstrap

What you'll need:

* [Bootstrap]("https://getbootstrap.com/docs/4.3/getting-started/download/")'s source
* [libsass-python]("https://sass.github.io/libsass-python/") (`pip install libsass`)

That's really it; I would also recommend reading the credited tutorial as I don't wish to simply copy and their explanations are wonderful.  Once the requirements are satisfied the project structure can setup.

### Directory Structure
The first thing to do is setup the project structure - or modify it a litle in my case.  Below, is an example directory tree of what my Flask projects look like.  I have a file in the root of the project that is called in order to run the application.  Most of the application (save for configuration - config.py and .flaskenv) is in the `app/` directory.  Inside here (`app/`) is where static assets are kept - this is also where the rest of the "action" will happen.

```
./project_dir/
├── app/
│   ├── app_package/
│   │   ├── __init__.py
│   │   ├── forms.py
│   │   └── views.py
│   ├── errors/
│   │   ├── __init__.py
│   │   ├── handlers.py
│   ├── main/
│   │   ├── __init__.py
│   │   └── views.py
│   ├── static/
│   │   ├── css/
│   │   │   ├── bootstrap/
│   │   ├── favicon/
│   │   ├── javascript/
│   ├── templates/
│   │   ├── errors/
│   │   ├── base.html
│   │   └── index.html
│   ├── __init__.py
│   ├── models.py
├── .flaskenv
├── config.py
├── README.md
├── requirements.txt
└── run_app.py
```

Normally, I put compiled bootstrap into its own directory within `~/static/css` and my CSS overrides are placed in directories for their corresponding app part (e.g. `app/static/main/style.css`, `app/static/errors/style.css`, etc.).  However, we'll be changing the structure slightly to accommodate the use of Sass - inside static, we create a `sass` directory and inside here we place our custom `.scss` file(s) and the bootstrap source (`bootstrap` from now on is a reference to the source).

```
...
├── app/
│   ├── static/
│   │   ├── sass/
│   │   │   ├── bootstrap/
│   │   │   ├── custom.scss
│   │   ├── css/
...
```

Ensure your file directory looks like this also, create the `custom.scss` file (doesn't have to be named that), and continue on to customize!

### Editing custome.scss to Customize Bootstrap
There is a ton you can do with Bootstrap to get it to look the way you like, however, this documentation will not be that in depth.  Please check out the resources listed out in the credits for more detail on what you may need for your specific project.  Here, we're simply going to add a few colors because all I want to do is change my available color palette.

Open (or create and open) the `custome.scss` file and enter in the following:

```sass
/* Import only the necessary Bootstrap files */
/* These should be relative to the file */
@import "bootstrap/scss/functions"; 
@import "bootstrap/scss/variables";

/* -------begin customization-------- */
/* change the primary theme color to red */
$theme-colors: (
  bgprim: #eb942d;
  txtprim: #443a2d;
);
/* -------end customization-------- */

/* finally, import Bootstrap to set the changes! */
@import "bootstrap";
```

So...what's going on here?  The first thing we need to do is import the parts of Bootstrap that we wish to modify.  Here, we're bringing in the functions and variables so we may add additional colors.  In the `begin customization` is where we specify that we would like to add a new theme-color (e.g. primary, secondary, etc.) called `bgprim` and `txtprim` set to the given hex values.  The document is closed out by importing the entirity of bootstrap so that it may be compiled with our overrides.

### Compiling Modified CSS

## Credits
The following links are for attribution to those that made this post possible.  Should you find this information useful, please visit these resources for further information.

* [How to Customize Bootstrap]("https://uxplanet.org/how-to-customize-bootstrap-b8078a011203") by [Carol Skelly]("https://uxplanet.org/@carolskelly")
    * This article provided the basis for "how" to customize bootstrap
* [libsass-python - Using with Flask]("https://sass.github.io/libsass-python/frameworks/flask.html")
* [Bootstrap]("https://getbootstrap.com/")
* [Sass Basics]("https://sass-lang.com/guide")
* [Bootstrap Sass Variables]("https://github.com/twbs/bootstrap/blob/v4-dev/scss/_variables.scss")

