# Thingsboard Gateway Docker Container
A slightly modified Thingsboard Gateway configured to run on top of AgileIoT image

## Installation
The latest version of the tb-gateway available (v1.4 at the moment) will be used.
1. [Get](https://github.com/thingsboard/thingsboard-gateway/releases) (or build) the latest deb package and copy it to this project's directory
1. Run `docker build -t tb-gateway .`
1. Edit `docker-compose.yml` and set the rest of `services.tb-gateway.environment` variables according to your [setup](https://thingsboard.io/docs/iot-gateway/getting-started/#step-3-gateway-provisioning)
1. Run `docker-compose up`


## Challenges
* The `docker-compose up` command exits with no logs. That happens because the initial sleep delay, defined in the `run-application.sh` file, was too short for the log file to be created.
* Tb-gateway application/system is too slow.
* The ports set up to be exposed by Kura’s docker container (port 1883 for MQTT and 5002 for telnet) were not accessible from the host and thus Thingsboard gateway was unable to subscribe to Kura’s Artemis MQTT broker.
