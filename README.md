
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





