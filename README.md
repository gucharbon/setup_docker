# Setup Docker

Quicly install and configure docker on a linux host:

- Install containerd
- Install Docker Engine (CE)
- Install Docker Client
- Configure docker daemon through `daemon.json` file

## Requirements

You only need to have an SSH access to the remote host in order to play this role.

## Role Variables

You can configure docker with the following variables:

| Variable                       | Default                                                                                               | Description                                                                                                                                                                                           |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `docker_repo`                  | `"deb [arch=amd64] https://download.docker.com/linux/ubuntu {{ansible_distribution_release}} stable"` | The apt repository where to install docker packages from. Note that `{{ ansible_distribution_release}}` will be substituted with the ubuntu release or remote host (e.g, trusty, xenial, bionic, ...) |
| `docker_packages`              | `["docker-ce", "docker-ce-cli", "containerd.io"]`                                                     | Packages to install. You can choose to install only docker engine (e.g, docker-ce) or install only the docker client (docker-ce-cli)                                                                  |
| `docker_service_state`         | `"started"`                                                                                           | Desired state for docker service                                                                                                                                                                      |
| `docker_service_enabled`       | `true`                                                                                                | Register docker service to start at boot.                                                                                                                                                             |
| `docker_restart_handler_state` | `"restarted"`                                                                                         | Desired state of docker service after performing modification of docker service configuration.                                                                                                        |

## Example Playbook

Most of the time, you only need to configure users:

```yaml
- hosts: localhost
  roles:
    - setup_docker
```

## License

MIT
