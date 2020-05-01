RPA Dashboard
===

## What is it?

RPA Dashboard is a dashboard to launch RPA jobs made with Robot Framework.

It uses open source software and integrates everything smootly into one customizable dashboard.

## Installation
Currently this repository is only good for localhost setup. There is no documentation for how to set up Certificate Authority for an internet domain.

For a RPA Dashboard repository with instructions how to setup a CA, go to [rpa_dashboard](https://github.com/Robo-Project/rpa_dashboard).

[Installation manual](documentation/installation.md)

## Create your first job and run it

[Setting up jobs and launching them](documentation/manual.md)

## How it all works?
[Architecture](documentation/architecture.md)

## Processes and where you can find them
Addresses to use with a browser:
- https://localhost/
- https://jenkins.localhost/

Nginx redirects the url to correct local address.

| Process          | Url               | local port | open port |
| ---------------- | ----------------- | ---------- | --------- |
| Grafana          | domain/           | 3000       |           |
| Jenkins          | jenkins.domain/   | 8080       |           |
| Backend          | backend.domain/   | 4000       |           |
| Postgres         |                   | 5432       |           |
| Docker in Docker |                   | 2376       |           |
| Watchtower       |                   |            |           |
| Nginx            |                   | 80, 443    | 80, 443   |

### Problems related with DbBot-SQLalchemy

DbBot proved not to be suitable for saving task related data. This is why we had to create our own dbsaver, that saves required data from the task. More about that [here](documentation/dbbotreport.md)
