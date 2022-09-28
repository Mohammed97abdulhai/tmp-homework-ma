# nginx-bosh-release

# prerequisites for running locally:
    - Bosh Lite
    - virtual box

# testing the release: 

1- upload the release to BOSH Director (bosh lite): open terminal in bosh directory and tap the following: 

``` bosh upload-release ```

2- check if the release is up: 

```bosh releases```

3- deploy the release to the director: 

```bosh -d nginx-deployment deployment-manifest.yml```

4- to make sure the instance is up and running: 

```bosh vms``` or ```bosh instances```

5- (if you're using bosh lite) expose the private ip address inside bosh lite to be seen by the host machine: 

```sudo route add -net 10.244.0.0/16     192.168.50.6```


6- sending a request to the deployed nginx server: 

```curl -i 10.244.0.2```


## whats left to do: 

add a web app that is protected by basic auth.

