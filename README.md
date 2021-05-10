# MetaCall Command Line Interface

This repository provides a Docker fallback option for architectures and operative systems that are still not supported by [metacall/distributable](https://github.com/metacall/distributable) for installing a portable CLI by means of Docker.

## Install

For installing we need to pull the image.

```sh
docker pull metacall/cli
```

Then set up the `metacall` command as an alias. This snippet of code must be pasted in your `.bashrc` or `.zshrc`:

```sh
alias metacall='function mc() { docker run --rm --network host -e "LOADER_SCRIPT_PATH=/metacall/source" -w /metacall/source -v `pwd`:/metacall/source -it metacall/cli $@; }; mc'
```

## Build

In case of you want to build it yourself. The `sed` is used to remove unused layer from the Dockerfile. The build is done disabling the cache of the CLI download layer so it always will download the latest version of the CLI.

```sh
sed 's/FROM metacall/#FROM metacall/' Dockerfile > Dockerfile.build
docker build --build-arg DISABLE_CACHE=`date +%s` -t metacall/cli -f Dockerfile.build .
```
