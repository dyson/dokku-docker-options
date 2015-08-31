DEPRECIATED
===========

Dokku docker options was merged into dokku at https://github.com/progrium/dokku/commit/df8f4fb8824550518b07c87ac56aba568bd81295

There is no need to use this plugin if you're running a dokku version after this. This plugin will no longer be maintained.

dokku-docker-options
==================================

Basic docker options for dokku (https://github.com/progrium/dokku).

Requirements
------------

Development version of dokku at or after https://github.com/progrium/dokku/commit/c77cbf1d3ae07f0eafb85082ed7edcae9e836147.

Installation
------------

```bash
$ cd /var/lib/dokku/plugins
$ sudo git clone https://github.com/dyson/dokku-docker-options.git docker-options
````

Usage
-----

```bash
$ dokku help
...
    docker-options <app>                            display docker options for an app
    docker-options:add <app> OPTIONS_STRING         add an option string to an app
    docker-options:remove <app> OPTIONS_STRING      remove an option string from an app
...
````

Add some options

```bash
$ dokku docker-options:add myapp "-v /host/path:/container/path"
$ dokku docker-options:add myapp "-v /another/container/path"
$ dokku docker-options:add myapp "-link container_name:alias"
```

Check what we added

```bash
$ dokku docker-options myapp
-link container_name:alias
-v /host/path:/container/path
-v /another/container/path
```

Remove an option
```bash
$ dokku docker-options:remove myapp "-link container_name:alias"
```

Manual Usage
------------

In your applications folder (/home/dokku/app_name) create a file called DOCKER_OPTIONS.

Inside this file list one docker option per line. For example:

```bash
-link container_name:alias
-v /host/path:/container/path
-v /another/container/path
```

The above example will result in the following options being passed to docker during deploy and docker run:

```bash
-link container_name:alias -v /host/path:/container/path -v /another/container/path
```

You may also include comments (lines beginning with a #) and blank lines in the DOCKER_OPTIONS file.

Move information on docker options can be found here: http://docs.docker.io/en/latest/reference/run/ .


License
-------

MIT.
