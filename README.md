# isvcs-zookeeper
asdf
asdf
asdf
isvcs-zookeeper is the docker image containing the [Zookeeper](https://zookeeper.apache.org/)
installation as used by [Control Center](https://github.com/control-center/serviced).

*NOTE:* Prior to July 2016, image versions v4 and earlier were defined in the
[serviced-isvcs](http://github.com/control-center/serviced-isvcs) repository.
Versions v5 and later of the isvcs-zookeeper the were defined and built from
this repo so that the isvcs-zookeeper and serviced-isvcs images could be
tagged and released independently of each other using standard git-flow procedures.


# Building
To buid a dev image for testing locally, use
  * `git checkout develop`
  * `git pull origin devlop`
  * `make clean build`

The result should be a `vN-dev` image in your local docker repo (e.g. `v5-dev`).   If you need to make changes, create
a feature branch like you would for any other kind of change, modify the image definition as necessary, use `make clean build` to
build an image and then test it as necessary.   Once you have finished your local testing, commit your changes, push them,
and create a pull-request as you would normally. A Jenkins PR build will be started to verify that your changes will build in
a Jenkins environment.

*NOTE:* To test changes of this image with Control Center, you will have to update a
GO language constant in the serviced source code to reference the new image tag; e.g.
[`ZK_IMAGE`](https://github.com/control-center/serviced/blob/1.1.6/isvcs/isvc.go#L29)

# Releasing

Use git flow to release a new version to the `master` branch.

The image version is defined in the [makefile](./makefile).

For Zenoss employees, the details on using git-flow to release a version is documented 
on the Zenoss Engineering 
[web site](https://sites.google.com/a/zenoss.com/engineering/home/faq/developer-patterns/using-git-flow).
After the git flow process is complete, a jenkins job can be triggered manually to build and 
publish the image to docker hub. 
