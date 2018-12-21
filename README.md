# Build sphinx documents

This docker image can be used to build sphinx documents with make.

## License

This Dockerfile is licensed under the creative commons license
[CC BY-SA](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

## Usage

The container lifecycle has to be done for every sphinx source directory.
Change the container name `doc_sphinx` to or these
directories.

Hint: The `sudo` command can be dismissed if the current user belongs to the
`docker` group.

### First build

Run

```
$ sudo docker run -v $(pwd):/data/ --name doc_sphinx forkedjensh/ubuntu-sphinx
```

with any make parameters as needed. Some of the possible parameters are:

- html
- slides
- rinoh
- latexpdf

These will be appended to the make command in the container. For an overview of
all possible parameters consult the [Sphinx
Documentation](http://www.sphinx-doc.org/en/master/contents.html). The `$(pwd)`
directory in the volume parameter is the directory where the sphinx source is
located.

One possible command would be

```
$ sudo docker run -v $(pwd):/data/ --name doc_sphinx forkedjensh/ubuntu-sphinx
html
```

### Following build

For future builds simply run

```
$ sudo docker start doc_sphinx
```

### Destroy the container

When things are finished and the container is no longer needed the command

```
$ sudo docker rm doc_sphinx
```

destroys the container.
