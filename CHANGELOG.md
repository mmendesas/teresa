# Change Log
All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/).

## [0.30.0] - 2019-06-04
### Added
- Support for GCE static IP

## [0.29.0] - 2019-04-29
### Added
- One click way to delete app silently with --no-input flag

## [0.28.0] - 2018-10-29
#### Fixed
- [server] Teresa was not sending env vars to the cloudsql-proxy sidecar

#### Changed
- [server] Bump the slugbuilder version to v3.6.0

## [0.27.1] - 2018-10-15
#### Fixed
- [server] Hanging release phase process with cloudsql-proxy sidecar

## [0.27.0] - 2018-09-05
### Added
- Validation for env var and secret names
- Support to create more than one web app per code base

### Fixed
- [server] Missing clousql-proxy sidecar in the release pod

## [0.26.0] - 2018-08-27
### Added
- Support for creating apps with multiple virtual hosts
- `app set-vhosts` command

### Changed
- [client] Improve app delete message
- [server] Command `app stop` and `app start` now stop/start cronjobs
- [server] Refactor the tests of the app package
- [server] Add first test using the fake client-go
- [server] Better logs on build errors
- [server] Bump the slugbuilder version to v3.5.0

### Fixed
- [server] Error message when enabling ssl with ingress
- [server] App ingress detection
- [server] Don't return internal server error for invalid app names

## [0.25.2] - 2018-08-06
### Fixed
- [server] Only use the nginx sidecar for services

## [0.25.1] - 2018-08-02
### Fixed
- [server] Ingress setting for out of cluster configs
- [server] `enable-ssl` command resetting the protocol to tcp

## [0.25.0] - 2018-08-01
### Added
- [server] Cluster autocaler support
- Support for secrets as files
- [server] Support for .yml extension
- Support for cloudsql-proxy sidecar
- FAQ entry about the cloudsql-proxy
- FAQ entry about the unix socket between nginx and app

### Changed
- [server] Remove external uuid package dependency to generate deploy uid's
- [server] Big refactor on spec pkg
- [server] Change healthcheck port back to the nginx one
- [server] Remove the function test.DeepEqual
- [server] Remove secrets from k8s after remove from deploy
- [server] Bump slugrunner version to v3.4.0

### Fixed
- [server] Database initial migration on mysql 5.7
- [server] Doesn't log request content on error middleware if the route is `User/Create`

## [0.24.1] - 2018-07-11
### Fixed
- [server] Channel leak on watch deploy rolling update and service creation

## [0.24.0] - 2018-07-06
### Added
- Limits to the nginx container
- Experimental Commands `build list`, `build delete` and `build run`
- [server] Support for teresa.yaml v2 format
- Command `service whitelist-source-ranges`
- Firewall whitelist to the `service info` command

### Fixed
- [server] Fix panic when monitoring the rolling update
- [server] `app info` command output

### Changed
- [client] Print more friendly error message when connection fails
- Bump the default slugrunner version to v3.3.0

## [0.23.0] - 2018-06-21
### Added
- [client] Support to remove remote cluster from configuration file

### Changed
- [client] Print app name and current cluster on command `app delete`
- [server] Set default backoff limit to 3 on cronjobs
- [server] Always use service type LoadBalancer on builds
- [server] Use app.tgz as source code tarball name
- Switch from godep to govendor

### Fixed
- [server] Fix cloud provider detection on gce
- [server] Save last user of deploy
- [server] Fix long running exec commands
- [server] Fix lack of error handling when streaming messages from readers
- [client] Add limits validation on app creation

## [0.22.0] - 2018-06-07
### Changed
- [server] Update client-go to v6.0.0 and bump minimum k8s version to 1.9
- [server] Use an explicit selector for the deploy spec
- [server] `app create` requires vhost when ingress is enabled
- Bump the default slugrunner version to v3.2.0
- Bump the default slugbuilder version to v3.4.0

### Fixed
- [server] Return not implemented error when enabling ssl with ingress on aws

## [0.21.0] - 2018-05-02
### Changed
- [server] Always return `fallback` cloudprovider operations for unknown cloud providers

### Fixed
- [server] Do not monitor rolling update of cronjob apps

## [0.20.0] - 2018-04-19
### Fixed
- Make deploy rollback update the app env vars

### Changed
- Improve `deploy rollback` usability
- [server] Monitor the rolling update after the deploy, returning an error if
  the former is stalled
- [server] Name service ports with the protocol

### Added
- `app change-team` command
- App protocol field
- Experimental `build` feature

## [0.19.0] - 2018-04-05
### Fixed
- Return error with timeout message when there's no resources for build, release phase and command exec
- Health Checks ports on deploys with nginx sidecar

### Changed
- Show CREATED AT instead of AGE in deploy list
- Delete configmap if a deploy remove the nginx
- Default nginx image to nginx:1.13-alpine-perl
- Bump the default slugrunner version to v3.1.0
- Update environment vars (`env-set` and `env-unset`) on each pod container

### Added
- Share application directory with nginx sidecar
- Share application environment vars nginx sidecar
- FAQ entry with an example dynamic nginx configuration

## [0.18.0] - 2018-03-27
### Added
- `service` command, for now only used to enable ssl support
- `service info` command

### Changed
- Update `gorm` version to v1.9.1
- Update `go-sql-driver/mysql`

### Fixed
- `.teresaignore` behavior (to work like `.gitignore`)
- Protect nginx vars from being interpreted as env vars

## [0.17.0] - 2018-03-20
### Changed
- Change Method `CreateSecret` to `CreateOrUpdateSecret` on k8s interfaces
- Default max-cpu app limit to 400m
- [HELM] Bump minio version to v0.5.5
- [server] Change the pull policy to always pull
- Infer if an app is a cronjob by `cron` prefix on process type
- Bump the default slugbuilder version to v3.3.0

### Added
- Support Nginx as sidecar
- Support for internal apps
- Support to filter app logs by container name
- Support to set secrets as env var

### Fixed
- Storage env vars on spec of Init Container

## [0.16.0] - 2018-03-07
### Added
- `app logs` support to filter by pod name
- `app logs` support to print the logs of the previous pod instance
- [server] `replace-storage-secret` admin command
- CronJob experimental support
- CONTRIBUTING.md and related FAQ entry

### Changed
- Better error message for invalid app name error
- Better error message for invalid env var name error
- Refactor specs to be more in line with k8s concepts
- The slugrunner doesn't mount the storage keys anymore. An init container is responsible for downloading the slug
- Bump the default slugrunner version to v3.0.1

## [0.15.0] - 2018-02-14
### Changed
- [server] using multistage build on teresa dockerfile
- [server] update default slugbuilder version to v3.2.0
- Upgrade golang version to 1.9

### Added
- `exec` command
- [helm] Add HealthChecks
- [server] graceful shutdown
- [client] support to deploy remote (http and https) and local files

## [0.14.0] - 2018-02-06
### Changed
- [server] decouple k8s client interface from the domain ones
- [client] rewrite client tar pkg and change the deploy cmd accordingly

### Fixed
- Pod list on `app info` command for apps without HPA
- [server] make the build process stop on client cancellation

### Added
- [server] default deploy lifecycle with 10s drain timeout
- [server] configurable env (`TERESA_DB_SHOW_LOGS`) to show (or not) database logs (default `false`)

## [0.13.0] - 2018-01-22
### Fixed
- [client] On deploys create the tar file before connecting to the server and
  remove it before exiting
- [server] null pointer exception on deploy

### Added
- app Start/Stop commands
- `app delete-pods` command
- set-password now support the --user flag to set password of another user(needs admin)

## [0.12.0] - 2018-01-12
### Changed
- Back to Godep for dependencies management
- Update `client-go` lib to version 4.0
- [server] Don't use the default service account on builds and deploys

### Added
- alias `app log` to `app logs`
- `app logs` now  support shorthand `-f` to `--follow` and `-n` to `--lines`

### Fixed
- Env vars being set or unset for the app on deploy update errors
- Typo on server pkg
- [server] Return all deploy errors to the client
- [client] teresaignore on Windows

## [0.11.0] - 2017-12-11
### Added
- [helm] support rbac
- Support ingress on app expose
- app create now support --vhost to define a virtual host to app
- Helm support ingress and service type config

### Fixed
- Don't return error on `app info` command if the app doesn't have HPA

## [0.10.0] - 2017-11-08
### Added
- Pod readiness to the `app info` output
- [helm] minio as dependency
- Team rename command

### Changed
- Using `dep` instead of `Godep` for dependencies management
- deploy list now print revision in reverse order and remove current column

### Fixed
- `app info` now counts only pods with defined state

## [0.9.0] - 2017-10-26
### Fixed
- login now use the --cluster flag to save the token to config file
- Don't return error on `app info` command if the app doesn't have HPA

### Changed
- Upgrade `slugbuilder` version to `v3.0.0`
- Timeout of `PodRun` process (deploy and release) is now configurable

### Added
- Allows developers to set the JWT auth token expiration period

## [0.8.0] - 2017-09-18
### Added
- Command 'deploy list'
- Command 'team remove-user'
- Command 'deploy rollback'
- Command 'app delete'

### Changed
- Deploys are now performed using the 'deploy create' command
- app info now print env vars sorted

### Fixed
- App info don't print pod without status

## [0.7.0] - 2017-08-29
### Added
- [server] --debug flag. For now only print the stack trace on panic/recover.
- [client] --cluster flag. To use a cluster different of current-cluster.

### Changed
- [client] Commands 'env-set' and 'env-unset' show the current cluster.

### Fixed
- [server] Restart count on 'app info' output
- [client] Validate 'deploy' command parameters
- [client] Hanging deploys when the app dir doesn't exist

## [0.6.0] - 2017-08-23
### Added
- [client] App name length validation
- autoscale command
- [server] Support for Teresa yaml per process type

### Changed
- [server] Specific CPU and Memory limits for both deploy and release pods
- [client] Change default `max-cpu` to `200m` (instead of `500m`) in command `create app`
- [server] Doesn't log request content on error middleware if the route is `Login`
- 'app info' command shows the pods age and restart count

## [0.5.0] - 2017-08-15
### Changed
- Use gRPC instead of go-swagger
- Changed project structure to be more k8s like
- Standardize error messages format and server logs
- 'app create' command doesn't create a welcome deploy anymore
- [client] Refactored config and bash completion
- [client] Flag --admin removed, admin users are only created with the
  'create-super-user' command
- [server] Delete build pod after deploy on success

### Added
- Unit tests
- Travis CI
- 'set-password' command
- Builtin TLS (thanks gRPC)
- Versioning by git tag
- [server] 'create-super-user' command
- [server] added so called 'release' command, which allows developers to run a
  command right after the build is finished
- [server] Healthcheck
- [server] Support for minio storage
- [server] Added deploy drain timeout in teresa.yaml, which makes the POD sleep
  for a configurable amount of time before receiving SIGTERM

### Fixed
- [server] Don't return stale app data to the user
- [server] Every deploy has at least one replica
- [server] 'app logs' command timeouts

## [0.3.2] - 2017-05-09
### Fixed
- Finish the merge with `teresa-cli` by removing all references to the old repo
- Multi team tokens. Before this fix a user would get access only to apps
  from one of its teams.

## [0.3.1] - 2017-04-24
### Fixed
- Fix deploy timeouts by sending a few bytes at a constant time interval to the
  network connection in use (as required by the idle timeout of the aws classic
  elb for instance)

### Changed
- Merge `teresa-cli` and `teresa-api`

## [0.3.0] - 2017-04-07
### Added
- Support for non-web process types

### Fixed
- Get current namespace name from environment variable instead of a constant

### Changed
- Location of slugbuilder and slugrunner images
- Read keys from k8s secrets
- Increase deploy timeouts and make them configurable

## [0.2.2] - 2017-03-16
### Changed
- Upgrade slugbuilder and slugrunner

## [0.2.1] - 2017-03-14
### Added
- use `TERESADB_DATABASE` variable to define location of `teresa.sqlite`

### Changed
- update README to use an api to generate password instead of a python script
- remove dead code
- remove users/me endpoint

## [0.2.0]
### Changed
- big breaking changing version

## [0.1.1] - 2016-08-12
### Added
- command `add team-user`
- vendoring dependencies

### Changed
- deployment now returning an error message on fail
- default service port changed from 5000 to 80
- deployment timeout increased
- improved deployment info printed out to user
- go-swagger updated to version 5.0.0

## [0.1.0] - 2016-08-03
