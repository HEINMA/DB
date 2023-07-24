
# Maria DB

https://mariadb.org/start-mariadb-in-k8s/

Create the container

```console
$ kubectl apply -f mariadb-deployment.yaml 
deployment.apps/mariadb-deployment created
```




```console

kubectl exec -it mariadb-deployment-76f576bb87-b862p -- mariadb -uroot -psecret -e "select current_user()"
```
Check the container
```console
kubectl get service mariadb-deployment
```


Expose the port by a load balancer
```console
kubectl expose service mariadb-deployment --port=3306 --target-port=30748 --name=mariadb-https
```


# REFFERENCES

Maria DB Run from docker.
https://mariadb.com/kb/en/installing-and-using-mariadb-via-docker/



## How to use customized docker versions.
https://mariadb.com/kb/en/creating-a-custom-container-image/


Hackernoon options
https://hackernoon.com/customizing-mariadb-docker-images

need to follow abve link to create this image.

## Refferences

https://linuxhint.com/lamp_server_docker/

https://dzone.com/articles/install-docker-kubernetes-and-minikube-on-linux-mi

## Start setting upa LAMP on linum mint.
This is how we can do it manually.
https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04

But we are expecting to do it with kubernetes.

https://dzone.com/articles/install-docker-kubernetes-and-minikube-on-linux-mi

If you want to execute the docker commands with the non-root user, you must add the user to the docker group by issuing the below-mentioned command:

sudo usermod -aG docker $USER


## Install kubernetes. 

https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-using-native-package-management


Above way follow to install kubernetes.

Then install the minikube.

sudo curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube


### port issue connecting to mariadb from localhost.
https://stackoverflow.com/questions/45637587/connection-between-docker-containers-via-unix-sockets

Install the mysql client on your host,

apt-get install mysql-client

then use the following command to access your database container.

mysql -u<user> -p<pass> -h $(docker inspect --format '{{ .NetworkSettings.IPAddress }}' <db-container>)

The command will automatically get the IP of your docker container.

Make sure to replace <user>, <pass> and <db-container> with your respective values. In your case:

mysql -uroot -ptest -h $(docker inspect --format '{{ .NetworkSettings.IPAddress }}' db)

Your command lets mariadb run at the standard port 3306. If not, you have to tell the mysql command the new port.

mysql -uroot -psecret -h $(docker inspect --format '{{ .NetworkSettings.IPAddress }}' mariadb-deployment-76f576bb87-b862p)



