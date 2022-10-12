# nginx-bosh-release
this is a release for nginx using Bosh releasing platform, it allows you to run an nginx web server 
## prerequisites for running locally:
    - Bosh Lite
    - virtual box

## testing the release: 

- open the terminal in tmp-homework-ma/bosh directory


- upload cloud-config to the bosh director, this step is necessary for BOSH to find the network and other configuration :

    ```console
        user@TMP-HOMEWORK-MA/bosh:~$ bosh update-cloud-config cloud-config.yml
    ```

- upload the stemcell, a steam cell is a versioned OS image wrapped with IaaS specific packaging (I am using ubuntu-bionic). 

    ```console
     user@TMP-HOMEWORK-MA/bosh:~$ bosh upload-stemcell --sha1 19355b8bece54930f78077290b7c1562ef45c1ee \
  https://bosh.io/d/stemcells/bosh-warden-boshlite-ubuntu-bionic-go_agent?v=1.115
    ```
     
- upload the release to BOSH Director (bosh lite): open terminal in bosh directory and tap the following: 

    ```console
         user@TMP-HOMEWORK-MA/bosh:~$ bosh upload-release 
    ```

- check if the release is up: 

    ```console
        user@TMP-HOMEWORK-MA/bosh:~$ bosh releases
    ```

- deploy the release to the director: 

    ```console 
        user@TMP-HOMEWORK-MA/bosh:~$ bosh -d nginx-deployment deployment-manifest.yml
    ```

- to make sure the instance is up and running: 

    ``` user@TMP-HOMEWORK-MA/bosh:~$ bosh vms``` or ```bosh instances```

- (if you're using bosh lite) expose the private ip address inside bosh lite to be seen by the host machine: 

    ```console
        user@TMP-HOMEWORK-MA/bosh:~$ sudo route add -net 10.244.0.0/16     192.168.50.6
    ```


- sending a request to the deployed nginx server: 

    ```curl -i 10.244.0.2```


## things to do in the future:

add a web app to make use of the nginx and to learn and apply how to do a bosh release for multiple jobs

