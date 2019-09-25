# DIPY Dockerfile for Brainlife

This dockerfile allows you to build/use a container containing DIPY command lines.

## Instructions

The [dipy-brainlife](https://hub.docker.com/r/skab12/dipy-brainlife/) Docker
container enables users to generate structural connectomes from diffusion MRI data using
a bunch of state-of-the-art techniques.

In your terminal, type:
```{bash}
$ docker pull skab12/dipy-brainlife:0.16.0
```

To run a specific command line of the tool:

```{bash}
$ docker run -i --rm skab12/dipy-brainlife:0.16.0 dipy_info -h
```

or  with Singularity:

```{bash}
$ SINGULARITYENV_PYTHONNOUSERSITE=true singularity exec -e docker://skab12/dipy:0.16.0 dipy_info -h
```

To get access to the list of available DIPY command line. you can get more information
on [DIPY website](https://dipy.org/documentation/1.0.0./reference_cmd/)
