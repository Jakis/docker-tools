A few tools to ease the use of docker locally.

Add {repo}/bin/ to your PATH

Setup in your local repo either a [Reactor Actions](https://github.com/srevenant/reactor) or an env file at:

	.pkg/ENV

Which has:

	export DOCKER_NAME={name of image}
	export DOCKER_IMAGE={org/$DOCKER_NAME}
	export DOCKER_TAGS="{any tags to add to the default build}"
    export DOCKER_ARGS="vars to export as build args"

Additionally you can just define DOCKER_TAGS at build time, and you can include BUILD_VERSION which will include a version as a tag.  If you specify NO_DOCKER_CACHE it will include --no-cache to the build.

Commands:

* _docker-build_ -- make a build using the current repo.  Dockerfile may be in current folder or in .pkg/Dockerfile.  Includes any variables on DOCKER_ARGS as --build-args
* _docker-clean_ -- clean ALL images -- very destructive, use with care
* _docker-images_ -- list all running containers matching the current repo, and all images
* _docker-push_ -- push to docker
* _docker-run_ -- run a docker container based on current repo.  Will terminate any currently running containers.  May override default run behavior with .pkg/docker-run file that is the alternate docker run command and args, with variables to be evaluated (i.e. $DOCKER_IMAGE)
* _docker-build-run_ -- do a docker-build, followed immediately by a docker-run
* _docker-shell_ -- pull up a shell on the current image

