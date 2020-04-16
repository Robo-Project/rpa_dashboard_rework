RPA dashboard rework
===

## Requirements

* Ansible installation
* Docker installation on host machine
  
## Local deployment

1. Run `ansible-playbook site.yml -i hosts.yml -c local -l localhost`
2. If reading initial admin password fails run playbook again
3. Navigate to localhost:8080 and follow instructions
4. Login to jenkins and create an api token
5. Open `jenkins-api-token` -file and type `[YOUR_USERNAME]:[YOUR_API_TOKEN]` without brackets
6. Add an empty line at the end of the file
7. Run `docker restart backend` on host machine
8. Navigate to localhost and login with `admin` and `admin`
9. Add database credentials to postgres datasource.
10. By default: `database: postgres` `username: postgres` `password: password123`
11. Save and enjoy

### Notes

* Doesn't seem to work locally on firefox. Use chrome-based browser instead
* Project seems to have a mind of its own and may or may not work depending upon the will of the cosmos

## Playbooks

#### shutdown.yml

Kills and removes all containers. Run site.yml to restart app.

#### nuke.yml (WIP)

Kill and removes all containers and volumes. Deletes all files used by the application. Run only if you want to reset.
