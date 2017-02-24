# nzbhydra  [![Build Status](https://travis-ci.org/theotherp/nzbhydra.svg?branch=master)](https://travis-ci.org/theotherp/nzbhydra) [![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/theotherp/nzbhydra.svg)](http://isitmaintained.com/project/theotherp/nzbhydra "Average time to resolve an issue") [![Percentage of issues still open](http://isitmaintained.com/badge/open/theotherp/nzbhydra.svg)](http://isitmaintained.com/project/theotherp/nzbhydra "Percentage of issues still open")
NZBHydra is a meta search for NZB indexers. It provides easy access to a number of raw and newznab based indexers. You can search all your indexers from one place and use it as indexer source for tools like Sonarr or CouchPotato.


## Features
* Searches Binsearch, NZBIndex, NZBClub,  Womble and all newznab compatible indexers (see https://github.com/theotherp/nzbhydra/issues/20 and https://github.com/theotherp/nzbhydra/wiki/Supported-Search-Types-And-Indexer-Hosts )
* Search by IMDB, TMDB, TVDB, TVRage and TVMaze ID (including season and episode) and filter by age and size. If an ID is not supported by an indexer it is attempted to be converted (e.g. TMDB to IMDB)
* Query generation, meaning when you search for a movie using e.g. an IMDB ID a query will be generated for raw indexers. Searching for a series season 1 episode 2 will also generate queries for raw indexers, like s01e02 and 1x02
* Grouping of results with the same title and of duplicate results, accounting for result posting time, size, group and poster. By default only one of the duplicates is shown. You can provide an indexer score to influence which one that might be
* Compatible with Sonarr, CP, NZB 360, SickBeard, Mylar and Lazy Librarian (and others)
* Either proxy the NZBs from the indexers (keeping all X-NZB headers), redirect or use direct links in search results
* Included function to add results (single or a bunch) to multiple instances of SABnzbd or NZBGet(v13+) and show NFOs where available. Option to decide if links are added as links or the NZBs are uploaded. Select category in GUI or define a default.
* Statistics on indexers (average response time, share of results, access errors), searches and downloads per time of day and day of week, NZB download history and search history (both via internal GUI and API): [Screenshot](http://i.imgur.com/Xc6URSc.png) 
* Indexers with problems are paused for an increasing time span (like in sonarr)
* Multi user capabilities so that you can share with your friends but keep the config safe
* Login by HTTP basic auth or form
* Define required and forbidden words and regexes
* Fine tune categories with separate required and forbidden words. Completely ignore categories in search results. Map newznab categories to internal categories. Use indexers only for certain categories.
* Reverse proxy compatible. See https://github.com/theotherp/nzbhydra/wiki/Reverse-proxies-and-URLs
* Basic torrent support via [Jackett](https://github.com/Jackett/Jackett) / [Cardigann](https://github.com/cardigann/cardigann/). Only for internal searches.
* [Dark theme](http://imgur.com/a/iCzL0), grey theme and [Bright theme](https://imgur.com/a/lBq9n) (slightly out of date)

##  How to run
If you downloaded the source run with Python 2.7.9+. Runs on http://0.0.0.0:5075 by default. See the console output on how to choose the port and host using command line parameters.

If you downloaded the [windows release](https://github.com/theotherp/nzbhydra-windows-releases) just start with NzbHydraTray.exe. Your default browser should open to the NZBHydra web interface.

You're also free to use the [docker container by linuxserver.io](https://hub.docker.com/r/linuxserver/hydra/). 
Although I do my best to keep that container nice and working please [use their forum](https://forum.linuxserver.io/index.php?threads/support-linuxserver-io-hydra.499/) for support regarding that container.

## Install as service
### Linux
Install scripts are provided for Ubuntu upstart based systems in the `contrib` directory. To install:

```sh
sudo cp contrib/defaults /etc/default/nzbhydra
sudo cp contrib/init.ubuntu /etc/init.d/nzbhydra
sudo chmod +x /etc/init.d/nzbhydra
sudo update-rc.d nzbhydra defaults
```

Edit the default configuration options:

```sh
sudo nano /etc/default/nzbhydra
```

Start the service:

```sh
sudo service nzbhydra start
```

### Windows
See the WindowsService folder in your NZB Hydra directory. It contains batch scripts to install and uninstall Hydra as a service. Run `installService.cmd` with administrator rights.
 
### Mac
You might need to install homebrew python. See [this excellent guide](https://www.mattgibson.ca/getting-nzbhydra-working-macos-sierra/).


## Development and how you can help
Generally testing and any bug reports are very welcome.

Any pull requests are also welcome, but I feel I and the program would mostly profit from:
* Unicode handling. I have no idea what I'm doing. 
* Advice regarding stability, error handling, net code (I program Java by day and it shows) and performance

Please send merge requests to the develop branch!

### Contact ###
Send me an email at TheOtherP@gmx.de or a PM at https://www.reddit.com/user/TheOtherP

### Donate ###
If you like to help me with any running or upcoming costs you're welcome to send money to my bitcoin: 1PnnwWfdyniojCL2kD5ZDBWBuKcFJvrq4t

### License ###
   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0
