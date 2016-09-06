RHTE Keycloak Demo (SECTION6)
====================

To start the keycloak service using docker-compose 

    docker-compose up -f docker/docker-compose.yml

There is no admin user by default, you need to add one to use the console

    docker exec <CONTAINER_ID> keycloak/bin/add-user-keycloak.sh -u <USER> -p <PASSWORD>
    docker exec <CONTAINER_ID> keycloak/bin/jboss-cli.sh -c ":reload"

To run the ansible playbook:

    ansible-playbook  -i "localhost," -c local rhte-keycloak-demo.yml -v \
      -e aws_access_key="xyz" -e aws_secret_key="abc"

You may need to:

     sudo setenforce 0
     source ~/git/ansible/hacking/env-setup
