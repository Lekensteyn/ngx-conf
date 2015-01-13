Nginx Helper Script (ngx)
=========================

A helper script to help manage Nginx configuration files.

Synopsis
--------

ngx [-h] (-e ENABLE | -d DISABLE | -x REMOVE | -l) [-f] [-r] [-v]

Description
-----------

Ngx is a relatively simple script to help manage Nginx configuration files. It
can be used to enable, disable, remove, and list configuration files.

**-h, --help**
  show a help message and exit
**-e CONFIG, --enable CONFIG**
  enable a configuration file
**-d CONFIG, --disable CONFIG**
  disable a configuration file
**-x CONFIG, --remove CONFIG**
  remove a configuration file; will prompt without -f
**-l, --list**
  list configuration files
**-f, --force**
  force change, even if doing so will destroy data
**-r, --reload**
  reload configuration after change
**-v, --verbose**
  show verbose output; default is quite unless errors

Only one action (enable|disable|edit|remove) can be performed at one time.
However, any action can be specified multiple times.

Examples
--------

* ngx -e site1 -e site2 -v -e site3
* ngx -r -d site
* ngx -f -r -x site1 -x site2

Configuration Files
-------------------

Three configuration files, if present, will be read. They will be read in the
following order; the next read file will always override the previous.

1. /etc/nginx/ngx.cfg
#. /etc/ngx.cfg
#. ngx.cfg

A sample configuration file with all options set to default::

    [DEFAULT]
    base_dir = /etc/nginx/
    conf_dir = conf.d/
    sites_en = sites-enabled/
    sites_dis = sites-disabled/
    conf_ext = .conf
    verbose = no
    reload = no
    force = no

Any arguments given to the command will override configuration options.
