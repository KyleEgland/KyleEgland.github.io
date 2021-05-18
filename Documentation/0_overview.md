# KyleEgland Github Page - Overview

- See credits for proper attribution, this project is a fork of Jekyll now
- This project is "open" so that others may see it and learn from it and not contribute to it

## Local Development

This project is maintained on a Linux machine and therefore all commands in this documenation will be for Linux systems - specifically Debian based systems.  Reference the Jekyll site to find instruction for [Windows](https://jekyllrb.com/docs/installation/windows/), [Mac](https://jekyllrb.com/docs/installation/macos/), or [Other Linux systems](https://jekyllrb.com/docs/installation/other-linux/).

### Quick Start

_Note: This is a reference to myself, not an invitation to participate in my blog. However, feel free to fork this for your own purposes if you like._

Serving the site locally requires a Ruby environment and the Jekyll package.  See the __Ruby Quick Start__ section and the credits below for assistance.

Serve the blog locally:

`user@machine:~/workspace/project$ bundle exec jekyll serve`

## Content Updates

Reference to myself on how to change the content and presentation of the site.

### Style changes

Modify the file `style.scss` in the root.

## Ruby Quick Start

After beginning this blog I found the project [rbenv](https://github.com/rbenv/rbenv) - which influenced one of my _favorite_ projects [pyenv](https://github.com/pyenv/pyenv) - and have been using it instead of a system wide installation.  This allows for the replication of the environment on any of my Linux machines.  Below are the basic steps to get `rbenv` up-and-running on a Debian based machine:

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

`$ rbenv install 3.0.0`

_Set global or local environment - use local when in the target directory_

`$ rbenv global 3.0.0`

`user@machine:~/workspace/project$ rbenv local 3.0.0`
