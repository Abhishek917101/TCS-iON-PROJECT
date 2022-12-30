Project Name:
Develop a docker image using Ethereum blockchain components and test using Truffle, Ganache, React, Metamask browser extension.
Prerequisites
use base OS as ubuntu and install docker and docker-Compose in that.

Instructions
Directory Structure :

Create directory called TCSiON.
Create another directory Project inside the TCSiON.
Inside the Project directory create another directory Called Project_todoapp.
Create Dockerfile and Docker Compose file :

Inside the Project_todoapp create Dockerfile to install necessory things.
And Inside the Project directory create Docker-Compose file named as docker-compose.yml 
Now run docker-composer command to start container :

docker-compose -f docker-compose.yml up -d
Install metamask chrome extension and check if Ethereum client (Ganache) works! :

Metamask chrome extension
Open Metamask and configure custom private network (http://dockerhost:8545)
Gets a list accounts from ganache container and run command :
docker logs -f docker_ganachecli_1 
Create a Truffle application :

run the below command :
docker exec -it project_truffleapp_1 bash
After running this command you will be redirect to container. Inside that run the following commands :
truffle init
after this do Manual correction to Update the truffle.js file as mentioned below (host and port are changed):

  module.exports = {
         networks: {
             development: {
                 host: 'ganachecli',
                 port: 8545,
                 network_id: '*' // Match any network id
             }
         }
     }
and add Tasks.sol file to contract folder

add deploy_tasks.js to migration folder

add app.js to test folder then run the commands :

truffle develop
Now you will be redirect to truffle environment. Inside that run the following commands :

    compile
    migrate
    test
To see tasks then run:
 testrpc