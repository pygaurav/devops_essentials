# Dev Ops Essential Thing


## Jfrog Essentails:

### Login via docker to Jfrog:

`echo $PASSWORD | sudo docker login -u=$USERNAME--password-stdin <jfrog_server_url>`

### Upload File to Jfrog:

`curl -X PUT -u $USERNAME:$PASSWORD -T <file_on_local> <full_url_path_on_Jfrog>`

### Download File to Jfrog:

`wget <full_url_path_on_Jfrog>  --user=$USERNAME --password=$PASSWORD`


## CIRCLE CI Essentails

    version: 2.1
    jobs:
      build:
        machine:      # This is needed for executing the machine 
          enabled: true
        steps:
           - checkout           #This line is needed for getting the latest code in github 
           - add_ssh_keys       #This is needed for adding the ssh keys configured on CircleCI
           - run:
               name: Deploy Over SSH
               command: |
                 ssh om@52.172.2.142 "bash -s" -- < demo.sh    #This is for executing shell script on the server
