# KyleEgland.github.io

What I've learned (and my general thoughts) made with Jekyll, stored in GitHub, and served by Pages.

## Synopsis

This blog is an applied learning project for myself, a display of what I've done/learned, and an outlet for my thoughts.  It has been changed in style and content with as much of the original left as possible (obviously the changes can be seen in the log, if you want to know that is).  This project utilizes [Jekyll](https://github.com/jekyll/jekyll) and [GitHub Pages](https://pages.github.com/) to serve the content.  Please see the __Credits__ section for attribution of the hardwork that went into this original repository before added my tweaks as well as resources to start your own blog.

## Local Development

This project is maintained on a Linux machine and therefore all commands in this `README.md` file will be for Linux systems - specifically Debian based systems.  Reference the Jekyll site to find instruction for [Windows](https://jekyllrb.com/docs/installation/windows/), [Mac](https://jekyllrb.com/docs/installation/macos/), or [Other Linux systems](https://jekyllrb.com/docs/installation/other-linux/).

### Quick Start

_Note: This is a reference to myself, not an invitation to participate in my blog.  However, feel free to fork this for your own purposes if you like._

Serving the site locally requires a Ruby environment and the Jekyll package.  See the __Ruby Quick Start__ section and the credits below for assistance.

Serve the blog locally:

`user@machine:~/workspace/project$ exec jekyll serve`

## Content Updates

Reference to myself on how to change the content and presentation of the site.

### Style changes

Modify the file `style.scss` in the root.

## Ruby Quick Start

After beginning this blog initially I've found the project [rbenv](https://github.com/rbenv/rbenv) - which is the basis for one of my _favorite_ projects [pyenv](https://github.com/pyenv/pyenv) - and have been using it instead of a system wide installation.  This allows for the replication of the environment on any of my Linux machines.  Below are the basic steps to get `rbenv` up-and-running on a Debian based machine:

1. Run the installer

`user@machine:~$ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-installer | bash`

2. Set path - may not be necessary but the installer did not do this for me

`user@machine:~$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`

3. Set `rbenv` automatically

`user@machine:~$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc`

_Restart shell; replace existing shell with a new one (to evaluate the changes to `~/.bashrc`)_

`user@machine:~$ exec "$SHELL"`

4. Check installation with the `rbenv-doctor` script

`user@machine:~$ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash`

5. Install an environment

_Show available versions_

`user@machine:~$ rbenv install -list`

_Install a given version - Jekyll supports 2.5.0+_

`$ rbenv install 2.7.1`

_Set global or local environment - use local when in the target directory_

`$ rbenv global 2.7.1`

`user@machine:~/workspace/project$ rbenv local 2.7.1`

## Credits

This page was made by forking [this](https://github.com/barryclark/jekyll-now) repository.  Additionally, original attribution from that repository is listed below.

- [jekyll-now](https://github.com/barryclark/jekyll-now) - best place to start if you want your own blog
- [Jekyll](https://github.com/jekyll/jekyll) - Thanks to its creators, contributors and maintainers.
- [Jekyll QuickStart](https://jekyllrb.com/docs/)
- [rbenv](https://github.com/rbenv/rbenv) - highly recommended if you are able to use it
- [Ruby Installation Guides](https://jekyllrb.com/docs/installation/)

_These are the original credits from the forked repo - I also wish to thank them_ :)

- [SVG icons](https://github.com/neilorangepeel/Free-Social-Icons) - Thanks, Neil Orange Peel. They're beautiful.
- [Solarized Light Pygments](https://gist.github.com/edwardhotchkiss/2005058) - Thanks, Edward.
- [Joel Glovier](http://joelglovier.com/writing/) - Great Jekyll articles. I used Joel's feed.xml in this repository.
- [David Furnes](https://github.com/dfurnes), [Jon Uy](https://github.com/jonuy), [Luke Patton](https://github.com/lkpttn) - Thanks for the design/code reviews.
- [Bart Kiers](https://github.com/bkiers), [Florian Simon](https://github.com/vermluh), [Henry Stanley](https://github.com/henryaj), [Hun Jae Lee](https://github.com/hunjaelee), [Javier Cejudo](https://github.com/javiercejudo), [Peter Etelej](https://github.com/etelej), [Ben Abbott](https://github.com/jaminscript), [Ray Nicholus](https://github.com/rnicholus), [Erin Grand](https://github.com/eringrand), [Léo Colombaro](https://github.com/LeoColomb), [Dean Attali](https://github.com/daattali), [Clayton Errington](https://github.com/cjerrington), [Colton Fitzgerald](https://github.com/coltonfitzgerald), [Trace Mayer](https://github.com/sunnankar) - Thanks for your [fantastic contributions](https://github.com/barryclark/jekyll-now/commits/master) to the project!

## Contributing

N/A - This repository is intended to be a static site about me, not looking for contributions.  Feel free to fork it if you like though, or go to the source for this (see link at top) and fork the source for yourself!  Thank you for viewing, I do appreciate it!
