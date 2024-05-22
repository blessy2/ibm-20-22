new creds to connect to cluster :

```

-- linux-interface to connect tocluster :

ssh -i "raman.pem" ubuntu@ec2-3-208-12-167.compute-1.amazonaws.com



---command to connect to cluster :

oc login --token=sha256~z8h-i0lxjqa_A_ERDv6Y1jL8xjc4K_QWg80VTWc1ljs --server=https://c116-e.us-south.containers.cloud.ibm.com:32256

```

Last day feedback :

https://forms.office.com/r/yX1hQ2G4qz



```

20th :
    
    ssh -i "raman.pem" ubuntu@ec2-52-201-152-100.compute-1.amazonaws.com
    
    'for mac :
        chmod 400
        
    docker host : 
        
        docker installation :
            
            https://docs.docker.com/engine/install/ubuntu/
            
            docker operations :
                
            
            -it :
                
                 docker -h
                 
    9  clear
   10  docker ps
   11  docker run -it --name ramanc1 centos:7
   12  docker ps
   
   -dit :
       
       docker run -dit --name ramanc1 centos:7
       
       
       
       
       
       
       
       
       history :
           
           
            docker ps
    2  docker images
    3  clear
    4  docker -h
    5  clear
    6  docker run -it --name ramanc1 httpd
    7  docker ps
    8  docker rm -f ramanc1
    9  clear
   10  docker ps
   11  docker run -it --name ramanc1 centos:7
   12  docker ps
   13  history
   14  docker run -dit --name ramanc2 centos:7
   15  docker ps -a
   16  docker ps
   17  docker attach ramanc1
   18  docker ps
   19  history
   20  docker run -dt --name ramanc3 centos:7
   21  docker ps
   22  docker attach ramanc3
   23  docker run -d --name ramanc4 centos:7
   24  docker ps
   25  docker ps -a
   26  docker attach ramanc4
   27  docker start ramanc4
   28  docker ps
   29  docker ps -a
   30  clear
   31  docker ps
   32  docker exec -it ramanc1 ls
   33  docker exec -it ramanc1 pwd
   34  docker exec -it ramanc1 mkdir raman
   35  docker exec -it ramanc1 ls
   36  docker exec -it ramanc1 /bin/bash
   37  docker exec -it ramanc4 ls
   38  docker exec -it ramanc3 ls
   39  docker exec -it ramanc3 /bin/bash
   40  clear
   41  docker ps
   42  docker exec -it bharat1 ls
   43  docker exec -it bharat1 /bin/bash




port mapping :
    
    
    
    ip addr
   61  clear
   62  docker ps
   63  netstat -tulnp
   64  apt install net-tools
   65  clear
   66  netstat -tulnp
   67  clear
   68  docker ps
   69  docker run -d --name ramanhttpd2 -p 80:81 httpd
   70  docker ps
   71  netstat -tulnp
   72  curl 172.31.49.229:80
   73  curl 172.31.49.229:81
   74  docker rm -f ramanhttpd2
   75  clear
   76  docker run -d --name ramanhttpd2 -p 81:80 httpd
   77  docker ps
   78  netstat -tulnp
   79  curl 172.31.49.229:81


8  netstat -tulnp
   79  curl 172.31.49.229:81
   80  history
   81  clear
   82  docker run -d --name ramanshop -P bkimminich/juice-shop
   83  docker ps


=================================================================


        
        volume mapping :
            
            
             docker ps
   14  docker run -it --name ramanc1 -v /app
   15  ls
   16  mkdir ramanconvolume
   17  ls
   18  docker run -dit --name ramanc1 -v /app:/data ubuntu
   19  dockerps
   20  docker ps
   21  docker inspect ramanc1
   22  ls
   23  cd ramanconvolume/
   24  ls
   25  cd ..
   26  ls
   27  pwd
   28  docker ps
   29  docker rm -f ramanc1
   30  docker run -dit --name ramanc1 -v /root/ramanconvolume:/data ubuntu
   31  docker inspect ramanc1
   32  clear
   33  docker ps
   34  ls
   35  docker ps
   36  docker ps -a
   37  docker exec -it ramanc1 /bin/bash
   38  ls
   39  cd ramanconvolume/
   40  ls
   41  docker run -dit --name ramanc2 -v /root/ramanconvolume:/data ubuntu
   42  docker ps
   43  docker exec -it ramanc2 /bin/bash

=======================================================

network :
    
    
    
     docker inspect ramanc1
   51  clear
   52  ip addr
   53  clear
   54  docker ntwork ls
   55  docker network ls
   56  docker ps
   57  docker network create --subnet 10.0.0.0/16 -h
   58  docker network create --subnet 10.0.0.0/16 -d bridge  raman-net
   59  docker network ls
   60  docker run -dit --name ramannetcon --network raman-net centos:7
   61  docker ps
   62  docker inspect ramannetcon
   63  docker inspect ramannetcon| grep -i raman
   64  docker ps
   65  docker rm -f `docker ps -aq`
   66  docker run -dit --name ramanhostconhttpd --network host httpd
   67  docker ps
   68  netstat -tulnp
   69  apt install net-tools
   70  netstat -tulnp
   71  docker run -dit --name ramanhostconnginx --network host nginx
   72  docker ps
   73  docker ps -a
   74* docker l
   75  docker run -dit --name ramanhostjuiceshop --network host bkimminich/juice-shop
   76  docker ps
   77  netstat -tulnp


==============================================


 vi ramandockerfile
   81  clear
   82  ls
   83  cat raman
   84  cat ramandockerfile
   85  docker images
   86  docker ps
   87  clear
   88  cat raman
   89  cat ramandockerfile
   90  ls
   91  vi index.html
   92  ls
   93  cat ramandockerfile
   94  docker build -t ramancustomimage:v1 -f ramandockerfile .
   95  docker images
   96  docker history ramancustomimage:v1
   97  clear
   98  docker images
   99  docker ps
  100  cat ramandockerfile
  101  docker run -d --name customcon -P ramancustomimage:v1
  102  docker ps
  103  vi index.html
  104  ls
  105  docker build -t ramancustomimage:v2 -f ramandockerfile .
  106  docker images
  107  docker run -d --name customcon2 -P ramancustomimage:v2
  108  docker ps
  109  historycat ramandockerfile
  110  cat ramandockerfile
  111  history
  
  
  
  
root@ip-172-31-58-244:~# cat ramandockerfile
FROM centos:7
RUN yum update -y
RUN yum install -y httpd
COPY ./index.html /var/www/html/index.html
EXPOSE 80
WORKDIR /var/www/html
CMD ["httpd","-D","FOREGROUND"]

        
        ==============================================================================
        
        
        
        OPENSHIFT :


oc instlattion windows : https://access.redhat.com/downloads/content/290/ver=4.15/rhel---9/4.15.13/x86_64/product-software



oc installation Linux : https://gist.github.com/mehdihasan/3399998cba54bdec78deb9be4a002acb





oc login --token=sha256~OGI1tijp0oFir5bG8ZzZcLwpILO1CH1zYMotrdFzy6w --server=https://c116-e.us-south.containers.cloud.ibm.com:31879



pod creation :
    
    
    oc api-resources
    4  ls
    5  mkdir ramanyml
    6  cd ramanyml/
    7  ls
    8  vi pod.yaml
    9  oc create -f pod.yaml 
   10  cat pod.yaml 
   11  oc get pods 
   12  oc get pods -o wide
   13  oc get svc
   
   
   
   root@ip-172-31-21-147:~/ramanyml# cat pod.yaml 
apiVersion: v1
kind: Pod
metadata:
  name: ramannginxpod
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80    
    
    
    =================================================
    
    
exec process for a pod/container :
    
    oc get pods -o wide
   24  oc exec -it ramanpod1 -- /bin/bash
   25  oc rsh ramanpod1
   26  ls
   27  pwd
   
   
   
   
   ========================
   
   multicon :
       
       
       vi multiconpod.yaml 
   34  oc status
   35  oc delete all --all
   36  vi multiconpod.yaml 
   37  k create -f multiconpod.yaml 
   38  oc create -f multiconpod.yaml 
   39  oc get [pods
   40  oc get pods
   41  oc get pods -o wide
   42  oc describe pod ramanmulticonpod
   43  oc describe pod ramanmulticon
   44  oc describe pod ramanmuticon
   45  oc exec -it ramanmuticon -c ramancon1 -- /bin/bash 
   46  oc exec -it ramanmuticon -c ramancon2 -- /bin/bash
   
   ====================================================
        
        
        oc run ramanpod --image nginx 
   56  oc get pods
   57  oc expose pod --name extsvc --type LoadBalancer --target-port 80 --port 80
   58  oc expose pod ramanpod --name extsvc --type LoadBalancer --target-port 80 --port 80
   59  oc get pods -o wide
   60  oc get svc
   61  oc describe svc extsvc
   62  oc get routes
   63  oc expose svc extsvc
   64  oc get routes
   
   =================================================
   deploymnts using cmdline :
   
   
   oc get pods
   73  oc project
   74  clear
   75  oc get all
   76  oc create deployment ramandep --image nginx --replicas 5
   77  oc create deployment ramandep --image nginx --replica 5
   78  oc create deploy ramandep --image nginx --replica=5
   79  oc create deploy -h
   80  clear
   81  oc create deploy ramandep --image nginx
   82  oc get pods
   83  clear
   84  oc get all
   85  oc scale deploy ramandep --replicas 5
   86  oc get pods
   87  oc scale deploy ramandep --replicas 10
   88  oc get pods
   89  oc scale deploy ramandep --replicas 1
   90  oc get pods
   91  oc scale deploy ramandep --replicas 5
   92  oc get pods -o wide
   93  clear
   94  oc get deploy
   95  oc get rs
   96  oc get pods
   97  oc delete pod ramandep-798ddd4b79-x9pjk
   98  oc get pods
   99  oc expose deploy ramandep --name ramandepsvc --type NodePort --taget-port 80 --port 80
  100  oc expose deploy ramandep --name ramandepsvc --type NodePort --target-port 80 --port 80
  101  oc get svc
  102  oc get route
  103  oc expose svc ramandepsvc
  104  oc get routes
  
  
  ========================
  deploymnt using yamml :
      
       vi deploysvc.yaml
  265  cat deploysvc.yaml
  266  clear
  267  oc delete all --alla
  268  oc delete all --all
  269  oc create -f deploysvc.yaml
  270  oc get pods
  271  oc get svc
  272  vi deploysvc.yaml
  273  oc apply -f deploysvc.yaml
  274  oc get svc
  275  ls
  276  cat deploysvc.yaml
  277  oc edit svc my-nginx




root@ip-172-31-21-147:~/ramanyml# cat deploysvc.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: my-nginx
  labels:
    run: my-nginx
spec:
  ports:
  - port: 80
    protocol: TCP
  selector:
    app: nginx
  type: LoadBalancer


=======================================================================


s2i :

First lab :
-- https://docs.openshift.com/container-platform/3.11/dev_guide/application_lifecycle/new_app.html

S2i : auto detect feature of openshuft

-- auto detecting from the source code :

oc new-app https://github.com/ramannkhanna2/ruby-ex.git
  141  oc get pods
  142  oc status
  143  oc expose svc/ruby-ex

#oc new-app openshift/ruby:2.5-ubi8~https://github.com/ramannkhanna2/ruby-ex.git  (specifically mentioning the builder image of ruby )
oc logs -f buildconfig/ruby-ex

oc start-build ruby-ex
oc get pods

oc logs -f bc/ruby-ex
-------------------------------

detectin a  image :
oc new-app bkimminich/juice-shop

oc new-app docker.io/nginx
  515  oc status
oc delete all --all
$ oc get is



=======================================================

Second lab :
    
Create our own repository on Github :
    
Add index.html file on same
now build the image with base builder image httpd:2.4
oc new-app httpd:2.4~https://github.com/ramannkhanna2/openshiftS2i.git   
oc status
oc logs -f bc/openshiftS2i
oc exec test-1-2klhv -- curl 127.0.0.1:8080

-- update the index.html file on github
oc start-build openshifts2i
oc expose dc/openshiftS2i --type=NodePort --port=8080
curl 192.168.42.163:32275

oc get all

======================================================================





oc new-build https://github.com/ramannkhanna2/DevOps-Jenkinsfile-Docker-Git.git --strategy=docker --name=myappp
  205  oc get all
  206  oc new-app myappp

  209  oc get all

  213  oc logs -f build/myappp-1
  214  oc get all
  215  clear
  216  oc get pods
oc new-app myappp

-- try making chnges on GitHub repo index file ,

 than :

 oc start-build myappp
  241  oc get builds
  242  oc logs -f build/myappp-2
  243  oc get pods


================================================









Build using templates to implement DEVOPS in openshift by both methods source as well as dockerfile :


--Below code is for source strategy :


apiVersion: v1
kind: Template
metadata:
  name: hello2-template
objects:
- kind: ImageStream
  apiVersion: v1
  metadata:
    annotations:
    labels:
      app: hello2
    name: hello2
  spec:
    lookupPolicy:
      local: false
- kind: "BuildConfig"
  apiVersion: "v1"
  metadata:
    name: "hello2" 
    labels:
      app: hello2
  spec:
    runPolicy: "Serial" 
    triggers: 
      -
        type: "GitHub"
        github:
          secret: "secret101"
      - type: "Generic"
        generic:
          secret: "secret101"
      -
        type: "ImageChange"
    source: 
      git:
        uri: "https://github.com/ramannkhanna2/spring-boot-hello-world.git"
    strategy: 
      sourceStrategy:
        from:
          kind: "ImageStreamTag"
          name: "ubi8-openjdk-8:1.3"
          namespace: openshift    
    output: 
      to:
        kind: "ImageStreamTag"
        name: "hello2:latest"
- kind: "DeploymentConfig"
  apiVersion: "v1"
  metadata:
    name: "hello2"
    labels:
      app: hello2
  spec:
    template: 
      metadata:
        labels:
          name: "hello2"
          app: hello2
      spec:
        containers:
          - name: "hello2"
            imagePullPolicy: Always
            ports:
              - containerPort: 8080
                protocol: "TCP"
            env:
              - name: RUN_ENV
                value: OpenShift-With-SourceStrategy 
        restartPolicy: Always
    replicas: 1 
    triggers:
      - type: "ConfigChange" 
      - type: "ImageChange" 
        imageChangeParams:
          automatic: true
          containerNames:
            - "hello2"
          from:
            kind: "ImageStreamTag"
            name: "hello2:latest"
    strategy: 
      type: "Rolling"
    paused: false 
    revisionHistoryLimit: 2 
    minReadySeconds: 0 
- kind: Service
  apiVersion: v1
  metadata:
    annotations:
    name: hello2
    labels:
      app: hello2
  spec:
    ports:
    - name: 8080-tcp
      protocol: TCP
      port: 8080
      targetPort: 8080
    selector:
      app: hello2
    type: ClusterIP
    sessionAffinity: None
- kind: Route
  apiVersion: route.openshift.io/v1
  metadata:
    name: hello2
    labels:
      app: hello2
    annotations:
  spec:
    to:
      kind: Service
      name: hello2
      weight: 100
    port:
      targetPort: 8080-tcp
  wildcardPolicy: None  





-- Build the above template first :


  325  oc create -f source.yml 
  326  oc get template
  327  oc describe template
oc new-app --template hello2-template
oc get bc
  377  ocget builds
  378  oc get builds

  381  oc logs -f build/hello2-1


-- check if appis deployed by browing he route ,,

-- ,now we have to create a webhook , sothat this template will build if anychanges happens on GitHub ...


oc describe bc hello2

-- get the webhook url for the build from above command..

-- on the guthub epo >> settings >> webhook >> 

-- paste the url in payload url section like below : (make sure update secret value)

https://c116-e.us-south.containers.cloud.ibm.com:31879/apis/build.openshift.io/v1/namespaces/projecttest/buildconfigs/hello2/webhooks/secret101/generic

--change content type to application/json


==========================================================

oc rollback hello2 --to-version 2
 1162  clear
 1163  oc get all
 1164  oc get pods
 
 ==============================
 
 
 
 
 HELM CHARTS:

Installation :

https://helm.sh/docs/intro/install/


-- To download helm

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/hel...
chmod 700 get_helm.sh
./get_helm.sh



--- Let’s create Our First Helm Chart


two famous public repos :

bitnami repo :
https://charts.bitnami.com/bitnami

helm repo add stable https://charts.helm.sh/stable


helm repo remove stable
helm repo add stable https://charts.helm.sh/stable
helm search repo jenkins

 helm search repo tomcat
NAME            CHART VERSION   APP VERSION     DESCRIPTION
stable/tomcat   0.4.3           7.0             DEPRECATED - Deploy a basic tomcat application ...

helm show values stable/tomcat

helm show chart stable/tomcat

helm show all stable/tomcat

apt-get install tree

mkdir helm
   61  cd helm/
   62  helm create hello-world
   63  ls
   64  cd hello-world/
   65  ls
   66  tree
   67  cd ..
   68  ls
   69  helm create my-app
   70  ls
   71  cd my-app/
   72  ls
   73  tree
   74  cat templates/deployment.yaml 
   75  ls
   76  cd ..
   77  ls
   78  cd ..
   79  ls
   80  cd helm/

root@master:~# helm install test-tomcat stable/tomcat


 kubectl  get all


helm install test-jenkins stable/jenkins

kubectl get all

 helm delete testjenkins

k get all

root@master:~# helm install --dry-run test-jenkins stable/jenkins

k get all

helm list

helm install test-tomcatv2 --version 0.4.0 stable/tomcat

k get all
helm list


helm list
   66  helm delete all
   67  helm delete test-tomcat
   68  helm delete test-tomcatv2
   69  helm install test-tomcat stable/tomcat
   70  helm list
   71  helm show values stable/tomcat
   72  helm install test-tomcat2 --set service.type=NodePort stable/tomcat
   73  helm list
   74  helm get values test-tomcat2
   77  helm get values test-tomcat2
   78  helm status
   79  helm status test-tomcat
   80  helm status test-tomcat2
   81  kubectl get all
   83  helm get manifest test-tomcat
   84  helm get manifest test-tomcat2



helm delete test-tomcat test-tomcat2

   96  helm list
   97  helm install test-tomcat stable/tomcat --version 0.4.0
   99  helm history test-tomcat
  100  helm upgrade test-tomcat stable/tomcat
  101  helm status test-tomcat
  103  helm history test-tomcat
  105  kubectl get all
  107  helm rollback test-tomcat
  108  helm history
  109  helm history test-tomcat
  
  
  =====================================================
 
 
 


HELMHUB :

https://artifacthub.io/


helm delete test-tomcat
  116  helm repolist
  117  helm repo list
  118  helm repo add bitnami https://charts.bitnami.com/bitnami
  119  helm show chart bitnami/tomcat
  120  clear
  121  helm pull --help
  122  clear
  123  helm pull bitmani/tomcat
  124  helm pull bitnami/tomcat
  125  helm list
  126  helm search repo bitnami
  127  clear
  128  helm install test-tomcatbit bitnami/tomcat
  129  clear
  130  kubectl get all
  131  helm ls
  132  ls
  133  helm pull bitnami/tomcat --untar
  134  ls
  135  cd tomcat
  136  ls
  137  tree
  
  
  ----------------------------------------------------------------------------------

      git clone https://github.com/ramannkhanna2/nodejsapp_jenkins-docker-kubernetes.git
 1319  ls
 1320  cd nodejsapp_jenkins-docker-kubernetes/
 1321  ls
 1322  rm -rf Jenkinsfile 
 1323  rm -rf Readme.md 
 1324  rm -rf deploy.tf 
 1325  cd test/
 1326  ls
 1327  cd ..
 1328  ls
 1329  clear
 1330  ls
 1331  docker ps
 1332  apt  install docker.io
 1333  docker ps
 1334  ls
 1335  docker images
 1336  docker build -t ramancusimage .
 1337  docker image
 1338  docker images
 1339  clear
 1340  docker login
 1341  docker images
 1342  docker push ramancusimage
 1343  docker tag ramancusimage ramann123/myimage:ibmappv1
 1344  docker images
 1345  docker push ramann123/myimage:ibmappv1
 1346  ls
 1347  clear
 1348  ls
 1349  vi deploymentservice.yml 
 1350  oc delete all --all
 1351  oc create -f deploymentservice.yml 
 1352  oc get all
 1353  ocget nodes -o wide
 1354  oc get nodes -o wide
 1355  ls
 1356  history
 ==========================

```
