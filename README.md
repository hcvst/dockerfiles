Dockerfiles
===========

* Erlang - Erlang R14B04 based on `stackbrew/ubuntu` 
* Zotonic - Erlang Web Framework (http://zotonic.com) based on `hcvst/erlang`

Notes
=====

Zotonic
-------
To run Zotonic in debug mode use the following command:
```bash
docker run -t -i           \
  -e HOME=/var/lib/zotonic \
  -u zotonic -p 8000:8000  \
  hcvst/zotonic            \
  /var/lib/zotonic/bin/zotonic debug
```

To start Zotonic in detached mode run instead:
`docker run -d -e HOME=/var/lib/zotonic -u zotonic -p 8000:8000 hcvst/zotonic /var/lib/zotonic/bin/zotonic start`

We have to use the -e command option to set the `$HOME` enviromental variable (https://github.com/dotcloud/docker/issues/2968)
as otherwise Zotonic will fail to start with the error message "Failed to create cookie file".

Use `docker ps` to lookup your container's ID and `docker inspect <ID>` to see which local port maps to Zotonic's 8000/tcp. **Note**: This didn't work for me which is why I now removed the `EXPOSE` command from the Dockerfile and use the `-p` option instead.




