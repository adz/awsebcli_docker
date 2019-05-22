# awsebcli_docker
AWS Elastic Beanstalk in a small alpine image


# How?

The Dockerfile is used to build an image with the Elastic Beanstalk (eb)
command line tool.

The `eb` script will mount your `~/.ssh`, `~/.aws`, and `~/.elasticbeanstalk`
directories as well as the current directory into the docker container so that
the tool can access your ssh keys, your configuration and the project in the
current directory.

Any arguments will be passed along to be run inside the container.

Make a small wrapper and put it in your path:

`~/eb`
```
#!/bin/bash
~/path/to/awsebcli_docker/eb $@
```

...then you can use `eb` as if you had installed the cli tool directly.

DockerHub is setup to build this automatically, but you can build it
locally with `./build` tagging with `adzdavies/awsebcli_docker`

# Why?

These tools broke a few times for me, with various incompatibilities.
The last straw was incompatibility between aws cli and eb cli!

I wanted to have a known good version and isolate it to avoid future issues.

