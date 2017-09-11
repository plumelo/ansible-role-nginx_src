nginx_src
=====

This role installs the nginx web server from sources from nginx mainline repository. The user can specify
the nginx version and the nginx modules to fetch and compile.

[![Build Status](https://travis-ci.org/plumelo/ansible-role-nginx_src.svg?branch=master)](https://travis-ci.org/plumelo/ansible-role-nginx_src)

Install
-------

```sh
ansible-galaxy install plumelo.nginx_src
```

Role Variables
--------------

The variables that can be passed to this role and a brief description about
them are as follows. (For all variables, take a look at [defaults/main.yml](defaults/main.yml))

```yaml
# The nginx version to install
nginx_src_version: 1.13.3

# The path used to download and compile/build nginx 
nginx_src_build_path: '/root/nginx-src'

# A list of modules to compile with nginx
nginx_src_modules:
  - name: ngx_cache_purge
    url: https://github.com/FRiCKLE/ngx_cache_purge/archive/2.3.tar.gz
  - name: ngx_pagespeed
    url: https://github.com/pagespeed/ngx_pagespeed/archive/v1.12.34.2-stable.tar.gz
    dynamic: true # will use --add-dynamic-module and copy the compiled module to nginx installation folder
     # module dependencies to download and add to build path
    deps:
      - name: psol
        url: https://dl.google.com/dl/page-speed/psol/1.12.34.2-x64.tar.gz

# Additional nginx compile arguments
nginx_src_args: []

# Cleanup/delete the build directory after installation
nginx_src_cleanup: true
```
