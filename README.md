# open\OST infrastructure

## Services

Currently deployed are:

| container  | url                  | description                                     |
| ---------- | -------------------- | ----------------------------------------------- |
| openost    | www.open-ost.ch      | our fancy website                               |
| gamejam    | game-jam.open-ost.ch | our even fancier website for the game jam event |
| synapse    | matrix.open-ost.ch   | matrix server                                   |
| synapse-db |                      | matrix db                                       |
| traefik    |                      | reverse proxy                                   |
| watchtower |                      | container updater                               |

Additionally, ufw as well as an ftp server is running, set up by
[studentenportal](https://github.com/studentenportal/deploy).

Have a look into [./docker/](./docker/) for more info.

## Deployment

Some ansible tasks are duplicated and already set up by [studentenportal](https://github.com/studentenportal/deploy).
If you'd like to hack together a better solution, PRs are welcome :)

To log in to the server behind open-ost.ch, ssh to `open-ost@open-ost.i-ost.ch`. 

Have a look into [./ansible/](./ansible/) for more info.

## Relevant files

All relevant data is in `/home/open-ost` on the server.

- `docker/data` is the data folder for the containers and should *NOT* be
  committed
- `docker/config` is the place for configif files and *SHOULD* be
  committed to preserve ssot
- `~/open-ost.env` is the docker environment file. It's deployed via
  Ansible.
  
## Deploying

The private `pass` repository contains passwords needed to run Ansible.

To deploy the Ansible-part, do the following:

- Make sure you can access the server via SSH using 
  key-based authentication.
- Clone the "pass" repository so it's inside this repository under ./ansible/pass/
- Run `ansible-playbook site.yml`
