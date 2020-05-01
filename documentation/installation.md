# Installation

## Requirements

* Ansible installation
* docker-py installation on host machine
  * run `pip install docker-py`

## Deployment

If you have previously used rpa_dashboard, it's best to clear all volumes and images related to it to avoid conflicts.

### Localhost setup
Jenkins address `jenkins.localhost`and backend address 'backend.localhost' does not work unless you edit your '/etc/hosts' file.
Inside `/etc/hosts` add new line `127.0.0.1 *.localhost`, if it doesn't exist yet.

If you're using localhost, the site will warn about connection not being private. This happens because we are using encrypted connection, but we do not have a certificate authority. It doesn't matter as we are using localhost connection. In most browsers, select `advanced` and proceed to the site.

### Setup with ansible
0. Edit `vars.yml` and change `pg_db`, `pg_user`, `pg_pswd` and `backend_token` to something else, do not use defaults.
1. Run `ansible-playbook site.yml -i hosts.yml -c local -l localhost`
2. If reading initial admin password fails run playbook again.
  - It might fail because it takes some time for jenkins to start up.
3. With browser, open jenkins.localhost and insert the initial admin password.
4. Login to jenkins. Skip the automated setup.
5. Go to your profile and configuration. Change your password and create an api token.
6. Open `jenkins-api-token` -file and type `[YOUR_USERNAME]:[YOUR_API_TOKEN]` without brackets. Leave End-Of-Line (EOL) character to the end of the line, this happens automatically with most editors. Ex. `admin:132123eab7892734987`
7. Restart backend with `docker restart backend`
8. With browser, open address `localhost` and login with username `admin` and password `admin`. Change the default password when prompted.
9. Navigate to Configuration -> Data Sources -> PostgreSQL. Add database credentials, the ones which you changed in section 0.

#### Define Jenkins security:

1. Login to Jenkins.
2. Navigate to `Manage Jenkins` -> `Configure Global Security`
3. Under Strategy, Authorization, select `Logged-in users can do anything`
4. Uncheck `Allow anonymous read access`
5. Save

### Setting up your first job
[Setting up jobs and launching them](manual.md)
