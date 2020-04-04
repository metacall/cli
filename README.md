# MetaCall Command Line Interface

This repository provides a Docker fallback option for architectures and operative systems that are still not supported by [metacall/distributable](https://github.com/metacall/distributable) for installing a portable CLI by means of Docker.

## Build Commands

```sh
docker build -t metacall/cli .
docker run --rm -it metacall/cli
```

## Set up CLI

`.bashrc` `.zshrc`
