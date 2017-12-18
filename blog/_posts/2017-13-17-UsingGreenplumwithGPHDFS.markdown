---
layout: post
title:  "Using Greenplum OSS with GPHDFS"
date:   2017-12-17 12:44:29 -0800
categories: greenplum ubuntu docker
---
Now, you can start using Greenplum OSS that is built for Ubuntu OS. Greenplum is a highly scalable massively parallel processing(MPP) database.  Most companies use this database solution to load large scale data beyond petabytes while using SQL interface to query the data.

Since Greenplum.org published blog on how to install OSS on Ubuntu, i want to start using the solution, instead of spending time to install and configure the solution.
I wrote [scripts](https://github.com/kongyew/greenplum-dockers) to build Greenplum docker file, so you can save time.

To start using the GPDB open source docker, you can follow these commands.
"Docker pull" downloads the image from Docker [registry]() and stores image locally.

{% highlight bash %}
$ docker pull kochanpivotal/gpdb5oss

$ export DOCKER_TAG="kochanpivotal/gpdb5oss"
$ docker run  -it --hostname=gpdb5oss \
    --name gpdb5oss \
    --publish 5432:5432 \
    --publish 88:22 \
    ${DOCKER_TAG} bin/bash
Running /docker-entrypoint.d
Running bin/bash
root@gpdb5oss:/#
{% endhighlight %}

You can start GPDB service by using the pre-built script "startGPDB.sh".
{% highlight bash %}
$ root@gpdb5oss:/# startGPDB.sh
SSHD is running
20171217:21:29:11:000248 gpstart:gpdb5oss:gpadmin-[INFO]:-Starting gpstart with args: -a
20171217:21:29:11:000248 gpstart:gpdb5oss:gpadmin-[INFO]:-Gathering information and validating the environment...
20171217:21:29:11:000248 gpstart:gpdb5oss:gpadmin-[INFO]:-Greenplum Binary Version: 'postgres (Greenplum Database) 5.3.0 build 2155c5a-oss'
20171217:21:29:11:000248 gpstart:gpdb5oss:gpadmin-[INFO]:-Greenplum Catalog Version: '301705051'
20171217:21:29:11:000248 gpstart:gpdb5oss:gpadmin-[INFO]:-Starting Master instance in admin mode
...su g
{% endhighlight %}

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
