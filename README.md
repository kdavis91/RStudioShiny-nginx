# RStudioShiny-nginx
## Wrapper script for installing R, RStudio Server, Shiny Server all behind an nginx reverse proxy

This script assumes you have a pretty clean Ubuntu 20.04 LTS install.

We will:
* Add the official R 4.0 respository
* Add the APT keys for this repository
* Install R (r-base and r-base-dev)
* Download and install RStudio Server
* Install and configure nginx (more on this below)
* Install the shiny R package
* Download and install Shiny Server
* Configure Shiny Server (more on this below)


Once complete you'll have:
* nginx default home page being served on port 80 (http://127.0.0.1)
* RStudio Server being served on port 8787 and also as a subdirectory (http://127.0.0.1:8787 & http://127.0.0.1/rstudio)
* Shiny Server being served on port 3838 and also as a subdirectory (http://127.0.0.1:3838 & http://127.0.0.1/shiny)
* Shiny Server is being run as the user that installed it (little bit weird but makes it easy for the user)
* Shiny Server is being run out of the users home directory (~/shiny) (little bit weird but makes it easy for the user)
* Shiny Server can host multiple apps and will present an initial index page, an index entry gets created for every folder in ~/shiny (If you only want to host a single app then just delete the sample app folder in ~/shiny and publish your application directly into there)

## Instructions
Simply download and run the rstudioshinynginxwrapper.sh script. This should be as simple as:
```
wget https://raw.githubusercontent.com/jb2cool/RStudioShiny-nginx/master/rstudioshinynginxwrapper.sh
bash rstudioshinynginxwrapper.sh
```

## Cautions
* The install script will overwrite your /etc/nginx/sites-enabled/default file, if you have already made customisations to this file ensure you have a backup.
* The install script manually creates your R personal library, this shouldn't have any impact if you already have a personal library but it's untested.
* This is designed for ease-of-use on a single-user machine, if this is a multi-user machine then this is probably not the approach to take.
