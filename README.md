# Docker compose traefik
> Docker compose and configuration to setup traefik ingress for web traffic

[![LICENSE][license-image]][license-url]

This docker-compose.yml uses [traefik](https://traefik.io/) - "The Cloud Native Edge Router".

> Traefik is a reverse proxy / load balancer that's easy, dynamic, automatic, fast, full-featured, open source, production proven, provides metrics, and integrates with every major cluster technologies... No wonder it's so popular!

The configuration bases on docs that can be found on the traefik project website - [Traefik let's Encrypt and Docker](https://docs.traefik.io/user-guide/docker-and-lets-encrypt/)

## Main functions
* Use Traefik as a layer-7 load balancer
* SSL termination for a set of micro-services and/or web apps
* Automatic discovery of any services on the Docker host
* Traefik reconfigure itself automatically when containers get created (or shut down)
* HTTP traffic can be routed accordingly based on automatic reconfiguration
* Let's Encrypt to automatically generate and renew SSL certificates per hostname

## Setup

* Server with public IP
* Install latest Docker (i.e. [Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/))
  - [Post-installation steps for Linux](https://docs.docker.com/install/linux/linux-postinstall/)
* Install latest [Docker Compose](https://docs.docker.com/compose/install/#install-compose)
* Configure your domain to point to your IP, i.e. `my-test-domain.com`
  - use also wildcard `CNAME` `*` is an alias `my-test-domain.com`

## Usage example

On the Docker host, run the following command:
```
docker network create web
```

Now create directory for traefik:
```
cd ~
mkdir sites
cd sites
git clone https://github.com/bitroniq/docker-compose-traefik.git
cd docker-compose-traefik
```

The `docker-compose.yml` provides simple way to create immutable Traefik container and configure it using locally shared config files:
* `traefik.toml`
* `acme.json`

Mounting the /var/run/docker.sock Docker socket in the container allows Traefik to listen to Docker events and reconfigure its own internal configuration when containers are created (or shut down).

To boot the container from the ~/sites/docker-compose-traefik directory, run:
```
docker-compose up -d
```

Now you can open your browser and go to `http://localhost:8888` to see the Traefik Dashboard.

## Release History

> All notable changes to this project will be documented in this section.

> The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
> and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

> ### How do I make a good changelog?
> #### Guiding Principles

> * Changelogs are for humans, not machines.
> * There should be an entry for every single version.
> * The same types of changes should be grouped.
> * Versions and sections should be linkable.
> * The latest version comes first.
> * The release date of each version is displayed.
> * Mention whether you follow Semantic Versioning.

> #### Types of changes
> * `Added` for new features.
> * `Changed` for changes in existing functionality.
> * `Deprecated` for soon-to-be removed features.
> * `Removed` for now removed features.
> * `Fixed` for any bug fixes.
> * `Security` in case of vulnerabilities.

### [Unreleased]

### [v1.1] - 2018-07-17
#### Fixed
- Fixed some typos

#### Added
- This CHANGELOG file to hopefully serve as an evolving example of a
  standardized open source project CHANGELOG.

### [v1.0] - 2018-07-17
#### Fixed
- Some typos

[Unreleased]: https://github.com/bitroniq/readme-template/compare/v1.1...HEAD
[v1.1]: https://github.com/bitroniq/readme-template/compare/v1.0...v1.1
[v1.0]: https://github.com/bitroniq/readme-template/compare/ff494e6...v1.0

---

## Meta

Piotr Kowalski – [@YourTwitter](https://twitter.com/YourLoign) – YourEmail@example.com

Distributed under the GNU GPL license. See ``LICENSE`` for more information.

[https://github.com/bitroniq/docker-compose-traefik](https://github.com/bitroniq/docker-compose-traefik)

## Contributing

1. Fork it (<https://github.com/bitroniq/docker-compose-traefik/fork>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request

<!-- Markdown link & img dfn's -->
[license-image]: https://img.shields.io/badge/license-GPL-brightgreen.svg
[license-url]: https://raw.githubusercontent.com/bitroniq/docker-compose-traefik/master/LICENSE
[wiki]: https://github.com/bitroniq/docker-compose-traefik/wiki

