# Linked and Networked DRoneS - Schema

This repository contains the configuration required to create a hosted version of Zazuko's [ontology manager](https://github.com/zazuko/ontology-manager) for the LANDRS project. It sets up a Traefik container as a reverse proxy for the ontology manager as well as a PostgreSQL database.

## Installation

### Configuration

To setup this stack, first it needs to be configured by crating a secrets.env file based off of the secrets.env.example file. Zazuko's provideds documentation on how to setup the [OAuth configuration](https://zazuko.github.io/ontology-manager/local-development-setup.html). Along with the environment variables setup in the secrets file, a number of variables are available in the docker-compose.yaml file which point the editor at a specific GitHub repository that stores the ontology information.

Once the environment is setup, the docker-compose.yaml file must be modified to replace the email address associated with the let's encrypt account (used for HTTPS certificates) on [line #12](https://github.com/landrs-toolkit/landrs-stack-schema/blob/master/docker-compose.yaml#L11).

Finally the docker-compose.yaml file needs to be modified to point to the correct domain for the project. This must be changed on [line #54](ttps://github.com/landrs-toolkit/landrs-stack-schema/blob/master/docker-compose.yaml#L54) and [line #64](ttps://github.com/landrs-toolkit/landrs-stack-schema/blob/master/docker-compose.yaml#L11).

### Building

Once the stack has been configured, the docker containers need to be built. To do this, the LANDRS' version of the ontology manager must be cloned to a subdirectory below the current directory.

```bash
git clone https://github.com/landrs-toolkit/schema.landrs.org.git ../zazuko
```

Once cloned, it's docker container can be built by running the following.

```bash
docker-compose build
```

Finally, the stack can be started with docker-compose by running the up command:

```bash
docker-compose up
```
