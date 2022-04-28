###################################Assigment 1 ##################################################
DaemonSet is going to deploy Nginx only on nodes labeled as ssd=true

apiVersion: apps/v1 
kind: "DaemonSet" 
metadata: 
labels: 
app: nginx 
ssd: "true" 
name: nginx-ssd-storage 
spec: 
template: 
metadata: 
labels: 
app: nginx ssd: "true" 
spec: 
nodeSelector: 
ssd: "true" 
containers: - 
name: nginx 
image: nginx:1.10.0
#######################################################################################



################################Assignment 2##########################################
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 1
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
     
     
     Create the Deployment by running the following command: 
     kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml
     
     
    Run "kubectl get deployments" to check if the Deployment was created.
    NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment        0/1     0            0           1s
 ##################################################################################################
 
 
 #####################################Assignment 3#################################################
 
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-world
spec:
  selector:
    matchLabels:
      run: load-balancer-example
  replicas: 2
  template:
    metadata:
      labels:
        run: load-balancer-example
    spec:
      containers:
        - name: hello-world
          image: gcr.io/google-samples/node-hello:1.0
          ports:
            - containerPort: 8000
              protocol: TCP
 
 Run a Hello World application in your cluster: Create the application Deployment using the file above:  
 
  kubectl apply -f https://k8s.io/examples/service/access/hello-application.yaml
  kubectl get deployments hello-world
  kubectl get rc
  
  #####Create a Service object that exposes the deployment################
  kubectl expose deployment hello-world --type=NodePort --name=example-service
  
 kubectl describe svc example-service
 
kubectl get pods --selector="run=load-balancer-example" --output=wide
NAME                           READY   STATUS    ...  IP           NODE
hello-world-2895499144-bsbk5   1/1     Running   ...  10.200.1.4   worker1
hello-world-2895499144-m1pwt   1/1     Running   ...  10.200.2.5   worker2

curl 10.32.0.16:8000

################################################################################################################################



#################################### Assignment 4 ##############################################################################

=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2022.04.28 16:48:01 =~=~=~=~=~=~=~=~=~=~=~=
login as: ec2-user
Authenticating with public key "imported-openssh-key"
Last login: Thu Apr 28 03:56:12 2022 from 106.202.141.115


       __|  __|_  )
       _|  (     /   Amazon Linux 2 AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-2/
]0;ec2-user@ip-172-31-24-58:~[?1034h[ec2-user@ip-172-31-24-58 ~]$ 
]0;ec2-user@ip-172-31-24-58:~[ec2-user@ip-172-31-24-58 ~]$ 
]0;ec2-user@ip-172-31-24-58:~[ec2-user@ip-172-31-24-58 ~]$ cd [K[K[Ksudo -[Ksu -
Last login: Thu Apr 28 05:52:23 UTC 2022 on pts/0
]0;root@ip-172-31-24-58:~[?1034h[root@ip-172-31-24-58 ~]# cd /root/
]0;root@ip-172-31-24-58:~[root@ip-172-31-24-58 ~]# cd [K[K[Kpwd 
/root
]0;root@ip-172-31-24-58:~[root@ip-172-31-24-58 ~]# git clone https://github.com/omrKalyan/example-voting- 
app
fatal: destination path 'example-voting-app' already exists and is not an empty directory.
]0;root@ip-172-31-24-58:~[root@ip-172-31-24-58 ~]# cd /root/
.cache/              example-voting-app/  kubernetes-training/
.config/             .kube/               .ssh/
[root@ip-172-31-24-58 ~]# cd /root/
.cache/              example-voting-app/  kubernetes-training/
.config/             .kube/               .ssh/
[root@ip-172-31-24-58 ~]# cd /root/example-voting-app/
]0;root@ip-172-31-24-58:~/example-voting-app[root@ip-172-31-24-58 example-voting-app]# git clone https://github.com/omrKalya 
n/example-voting-app
Cloning into 'example-voting-app'...
remote: Enumerating objects: 494, done.[K
Receiving objects:   0% (1/494)
Receiving objects:   1% (5/494)
Receiving objects:   2% (10/494)
Receiving objects:   3% (15/494)
Receiving objects:   4% (20/494)
Receiving objects:   5% (25/494)
Receiving objects:   6% (30/494)
Receiving objects:   7% (35/494)
Receiving objects:   8% (40/494)
Receiving objects:   9% (45/494)
Receiving objects:  10% (50/494)
Receiving objects:  11% (55/494)
Receiving objects:  12% (60/494)
Receiving objects:  13% (65/494)
Receiving objects:  14% (70/494)
Receiving objects:  15% (75/494)
Receiving objects:  16% (80/494)
Receiving objects:  17% (84/494)
Receiving objects:  18% (89/494)
Receiving objects:  19% (94/494)
Receiving objects:  20% (99/494)
Receiving objects:  21% (104/494)
Receiving objects:  22% (109/494)
Receiving objects:  23% (114/494)
Receiving objects:  24% (119/494)
Receiving objects:  25% (124/494)
Receiving objects:  26% (129/494)
Receiving objects:  27% (134/494)
Receiving objects:  28% (139/494)
Receiving objects:  29% (144/494)
Receiving objects:  30% (149/494)
Receiving objects:  31% (154/494)
Receiving objects:  32% (159/494)
Receiving objects:  33% (164/494)
Receiving objects:  34% (168/494)
Receiving objects:  35% (173/494)
Receiving objects:  36% (178/494)
Receiving objects:  37% (183/494)
Receiving objects:  38% (188/494)
Receiving objects:  39% (193/494)
Receiving objects:  40% (198/494)
Receiving objects:  41% (203/494)
Receiving objects:  42% (208/494)
Receiving objects:  43% (213/494)
Receiving objects:  44% (218/494)
Receiving objects:  45% (223/494)
Receiving objects:  46% (228/494)
Receiving objects:  47% (233/494)
Receiving objects:  48% (238/494)
Receiving objects:  49% (243/494)
Receiving objects:  50% (247/494)
Receiving objects:  51% (252/494)
Receiving objects:  52% (257/494)
Receiving objects:  53% (262/494)
Receiving objects:  54% (267/494)
Receiving objects:  55% (272/494)
Receiving objects:  56% (277/494)
Receiving objects:  57% (282/494)
Receiving objects:  58% (287/494)
Receiving objects:  59% (292/494)
Receiving objects:  60% (297/494)
Receiving objects:  61% (302/494)
Receiving objects:  62% (307/494)
Receiving objects:  63% (312/494)
Receiving objects:  64% (317/494)
Receiving objects:  65% (322/494)
remote: Total 494 (delta 0), reused 0 (delta 0), pack-reused 494[K
Receiving objects:  66% (327/494)
Receiving objects:  67% (331/494)
Receiving objects:  68% (336/494)
Receiving objects:  69% (341/494)
Receiving objects:  70% (346/494)
Receiving objects:  71% (351/494)
Receiving objects:  72% (356/494)
Receiving objects:  73% (361/494)
Receiving objects:  74% (366/494)
Receiving objects:  75% (371/494)
Receiving objects:  76% (376/494)
Receiving objects:  77% (381/494)
Receiving objects:  78% (386/494)
Receiving objects:  79% (391/494)
Receiving objects:  80% (396/494)
Receiving objects:  81% (401/494)
Receiving objects:  82% (406/494)
Receiving objects:  83% (411/494)
Receiving objects:  84% (415/494)
Receiving objects:  85% (420/494)
Receiving objects:  86% (425/494)
Receiving objects:  87% (430/494)
Receiving objects:  88% (435/494)
Receiving objects:  89% (440/494)
Receiving objects:  90% (445/494)
Receiving objects:  91% (450/494)
Receiving objects:  92% (455/494)
Receiving objects:  93% (460/494)
Receiving objects:  94% (465/494)
Receiving objects:  95% (470/494)
Receiving objects:  96% (475/494)
Receiving objects:  97% (480/494)
Receiving objects:  98% (485/494)
Receiving objects:  99% (490/494)
Receiving objects: 100% (494/494)
Receiving objects: 100% (494/494), 236.47 KiB | 5.03 MiB/s, done.
Resolving deltas:   0% (0/178)
Resolving deltas:   1% (2/178)
Resolving deltas:   2% (4/178)
Resolving deltas:   3% (6/178)
Resolving deltas:   4% (8/178)
Resolving deltas:   5% (9/178)
Resolving deltas:   6% (11/178)
Resolving deltas:   7% (13/178)
Resolving deltas:   8% (15/178)
Resolving deltas:   9% (17/178)
Resolving deltas:  10% (18/178)
Resolving deltas:  11% (20/178)
Resolving deltas:  12% (22/178)
Resolving deltas:  13% (24/178)
Resolving deltas:  14% (25/178)
Resolving deltas:  15% (27/178)
Resolving deltas:  16% (29/178)
Resolving deltas:  17% (31/178)
Resolving deltas:  18% (33/178)
Resolving deltas:  19% (34/178)
Resolving deltas:  20% (36/178)
Resolving deltas:  21% (38/178)
Resolving deltas:  22% (40/178)
Resolving deltas:  23% (41/178)
Resolving deltas:  24% (43/178)
Resolving deltas:  25% (45/178)
Resolving deltas:  26% (47/178)
Resolving deltas:  27% (49/178)
Resolving deltas:  28% (50/178)
Resolving deltas:  29% (52/178)
Resolving deltas:  30% (54/178)
Resolving deltas:  31% (56/178)
Resolving deltas:  32% (57/178)
Resolving deltas:  33% (59/178)
Resolving deltas:  34% (61/178)
Resolving deltas:  35% (63/178)
Resolving deltas:  36% (65/178)
Resolving deltas:  37% (66/178)
Resolving deltas:  38% (68/178)
Resolving deltas:  39% (70/178)
Resolving deltas:  40% (72/178)
Resolving deltas:  41% (73/178)
Resolving deltas:  42% (75/178)
Resolving deltas:  43% (77/178)
Resolving deltas:  44% (79/178)
Resolving deltas:  45% (81/178)
Resolving deltas:  46% (82/178)
Resolving deltas:  47% (84/178)
Resolving deltas:  48% (86/178)
Resolving deltas:  49% (88/178)
Resolving deltas:  50% (89/178)
Resolving deltas:  51% (91/178)
Resolving deltas:  52% (93/178)
Resolving deltas:  53% (95/178)
Resolving deltas:  54% (97/178)
Resolving deltas:  55% (98/178)
Resolving deltas:  56% (100/178)
Resolving deltas:  57% (102/178)
Resolving deltas:  58% (104/178)
Resolving deltas:  59% (106/178)
Resolving deltas:  60% (107/178)
Resolving deltas:  61% (109/178)
Resolving deltas:  62% (111/178)
Resolving deltas:  63% (113/178)
Resolving deltas:  64% (114/178)
Resolving deltas:  65% (116/178)
Resolving deltas:  66% (118/178)
Resolving deltas:  67% (120/178)
Resolving deltas:  68% (122/178)
Resolving deltas:  69% (123/178)
Resolving deltas:  70% (125/178)
Resolving deltas:  71% (127/178)
Resolving deltas:  72% (129/178)
Resolving deltas:  73% (130/178)
Resolving deltas:  74% (132/178)
Resolving deltas:  75% (134/178)
Resolving deltas:  76% (136/178)
Resolving deltas:  77% (138/178)
Resolving deltas:  78% (139/178)
Resolving deltas:  79% (141/178)
Resolving deltas:  80% (143/178)
Resolving deltas:  81% (145/178)
Resolving deltas:  82% (146/178)
Resolving deltas:  83% (148/178)
Resolving deltas:  84% (150/178)
Resolving deltas:  85% (152/178)
Resolving deltas:  86% (154/178)
Resolving deltas:  87% (155/178)
Resolving deltas:  88% (157/178)
Resolving deltas:  89% (159/178)
Resolving deltas:  90% (161/178)
Resolving deltas:  91% (162/178)
Resolving deltas:  92% (164/178)
Resolving deltas:  93% (166/178)
Resolving deltas:  94% (168/178)
Resolving deltas:  95% (170/178)
Resolving deltas:  96% (171/178)
Resolving deltas:  97% (173/178)
Resolving deltas:  98% (175/178)
Resolving deltas:  99% (177/178)
Resolving deltas: 100% (178/178)
Resolving deltas: 100% (178/178), done.
]0;root@ip-172-31-24-58:~/example-voting-app[root@ip-172-31-24-58 example-voting-app]# 
[K[root@ip-172-31-24-58 example-voting-app]# cd /[K[K[K[Kls
[0m[01;35marchitecture.png[0m  docker-compose-javaworker.yml  docker-compose.yml  [01;34mexample-voting-app[0m  LICENSE      README.md  [01;34mvote[0m
dockercloud.yml   docker-compose-simple.yml      docker-stack.yml    [01;34mk8s-specifications[0m  MAINTAINERS  [01;34mresult[0m     [01;34mworker[0m
]0;root@ip-172-31-24-58:~/example-voting-app[root@ip-172-31-24-58 example-voting-app]# cd k8s-specifications/
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl apply -f .
deployment.apps/db created
service/db created
deployment.apps/redis created
service/redis created
deployment.apps/result created
service/result created
deployment.apps/vote created
service/vote created
deployment.apps/worker created
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get po -o wide
NAME                             READY   STATUS    RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-x7wwl               1/1     Running   0          6m20s   192.168.199.38   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running   0          6h20m   192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending   0          4h30m   <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running   0          6m20s   192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running   0          6m20s   192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-6fcvh             1/1     Running   0          6m20s   192.168.199.43   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-r6hzl           1/1     Running   0          6m20s   192.168.199.42   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get all
NAME                                 READY   STATUS    RESTARTS   AGE
pod/db-b54cd94f4-x7wwl               1/1     Running   0          8m43s
pod/fortune-configmap-volume         2/2     Running   0          6h23m
pod/mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending   0          4h32m
pod/redis-868d64d78-fsstx            1/1     Running   0          8m43s
pod/result-5d57b59f4b-wtcpj          1/1     Running   0          8m43s
pod/vote-94849dc97-6fcvh             1/1     Running   0          8m43s
pod/worker-dd46d7584-r6hzl           1/1     Running   0          8m43s

NAME                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
service/db              ClusterIP   10.97.101.64    <none>        5432/TCP         8m43s
service/mavenir-mysql   ClusterIP   10.96.59.151    <none>        3306/TCP         4h32m
service/redis           ClusterIP   10.97.175.28    <none>        6379/TCP         8m43s
service/result          NodePort    10.98.74.170    <none>        5001:31001/TCP   8m43s
service/vote            NodePort    10.104.40.203   <none>        5000:31000/TCP   8m43s

NAME                            READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/db              1/1     1            1           8m43s
deployment.apps/mavenir-mysql   0/1     1            0           4h32m
deployment.apps/redis           1/1     1            1           8m43s
deployment.apps/result          1/1     1            1           8m43s
deployment.apps/vote            1/1     1            1           8m43s
deployment.apps/worker          1/1     1            1           8m43s

NAME                                       DESIRED   CURRENT   READY   AGE
replicaset.apps/db-b54cd94f4               1         1         1       8m43s
replicaset.apps/mavenir-mysql-54f7ddc699   1         1         0       4h32m
replicaset.apps/redis-868d64d78            1         1         1       8m43s
replicaset.apps/result-5d57b59f4b          1         1         1       8m43s
replicaset.apps/vote-94849dc97             1         1         1       8m43s
replicaset.apps/worker-dd46d7584           1         1         1       8m43s
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# ^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# ^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# ^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# 192.168.199.43[K[K[K[K[K[K[K[K[K[K[K[K[K[K^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# ^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# 192.168.199.3131001[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[Kls
db-deployment.yaml  redis-deployment.yaml  result-deployment.yaml  vote-deployment.yaml  worker-deployment.yaml
db-service.yaml     redis-service.yaml     result-service.yaml     vote-service.yaml
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# v[Kvay[K[Ki result-service.yaml
[?1049h[>4;2m[?1h=[?2004h[?1004h[1;44r[?12h[?12l[22;2t[22;1t[27m[23m[29m[m[H[2J[?25l[44;1H"result-service.yaml" 13L, 195B[2;1H▽[6n[2;1H  [3;1HPzz\[0%m[6n[3;1H           [1;1H[>c]10;?]11;?[1;1H[36mapiVersion[m[35m:[m v1
[36mkind[m[35m:[m Service[2;14H[K[3;1H[36mmetadata[m[35m:[m[3;10H[K[4;3H[36mname[m[35m:[m result
[36mspec[m[35m:[m
  [36mtype[m[35m:[m NodePort
  [36mports[m[35m:[m
  [33m- [m[36mname[m[35m:[m [31m"result-service"[m
    [36mport[m[35m:[m [31m5001[m
    [36mtargetPort[m[35m:[m [31m80[m
    [36mnodePort[m[35m:[m [31m31001[m
  [36mselector[m[35m:[m
    [36mapp[m[35m:[m result
[1m[34m~                                                                                                                                                            [15;1H~                                                                                                                                                            [16;1H~                                                                                                                                                            [17;1H~                                                                                                                                                            [18;1H~                                                                                                                                                            [19;1H~                                                                                                                                                            [20;1H~                                                                                                                                                            [21;1H~                                                                                                                                                            [22;1H~                                                                                                                                                            [23;1H~                                                                                                                                                            [24;1H~                                                                                                                                                            [25;1H~                                                                                                                                                            [26;1H~                                                                                                                                                            [27;1H~                                                                                                                                                            [28;1H~                                                                                                                                                            [29;1H~                                                                                                                                                            [30;1H~                                                                                                                                                            [31;1H~                                                                                                                                                            [32;1H~                                                                                                                                                            [33;1H~                                                                                                                                                            [34;1H~                                                                                                                                                            [35;1H~                                                                                                                                                            [36;1H~                                                                                                                                                            [37;1H~                                                                                                                                                            [38;1H~                                                                                                                                                            [39;1H~                                                                                                                                                            [40;1H~                                                                                                                                                            [41;1H~                                                                                                                                                            [42;1H~                                                                                                                                                            [43;1H~                                                                                                                                                            [m[44;140H1,1[11CAll[1;1H[?25h[?25l[44;130Hi[1;1H[44;130H [1;1H[44;1H[1m-- INSERT --[m[44;13H[K[44;140H1,1[11CAll[1;1H[?25h[44;1H[K[1;1H[?25l[44;130H^[[1;1H[44;130H  [1;1H[44;140H1,1[11CAll[1;1H[?25h[?25l[44;130H:[1;1H[44;130H[K[44;1H:[?25hq!
[?25l[?2004l[>4;m[23;2t[23;1t[44;1H[K[44;1H[?1004l[?2004l[?1l>[?25h[>4;m[?1049l]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# cat result-service.yaml
apiVersion: v1
kind: Service
metadata:
  name: result
spec:
  type: NodePort
  ports:
  - name: "result-service"
    port: 5001
    targetPort: 80
    nodePort: 31001
  selector:
    app: result
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# cat vote-service.yaml
apiVersion: v1
kind: Service
metadata:
  name: vote
spec:
  type: NodePort
  ports:
  - name: "vote-service"
    port: 5000
    targetPort: 80
    nodePort: 31000
  selector:
    app: vote
  
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# 
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# v[Kkubectl get po -o wide
NAME                             READY   STATUS    RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-x7wwl               1/1     Running   0          45m     192.168.199.38   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running   0          6h59m   192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending   0          5h9m    <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running   0          45m     192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running   0          45m     192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-6fcvh             1/1     Running   0          45m     192.168.199.43   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-r6hzl           1/1     Running   0          45m     192.168.199.42   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl delete po vote-94849dc97-6fcvh
pod "vote-94849dc97-6fcvh" deleted
^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl delete po vote-94849dc97-6fcvh[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K
error: resource(s) were provided, but no name was specified
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl delete po [K[K[K[K[K[K[K[K[K[Kget po
NAME                             READY   STATUS    RESTARTS   AGE
db-b54cd94f4-x7wwl               1/1     Running   0          46m
fortune-configmap-volume         2/2     Running   0          7h
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending   0          5h10m
redis-868d64d78-fsstx            1/1     Running   0          46m
result-5d57b59f4b-wtcpj          1/1     Running   0          46m
vote-94849dc97-kfmkq             1/1     Running   0          23s
worker-dd46d7584-r6hzl           1/1     Running   0          46m
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get po -o wide
NAME                             READY   STATUS    RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-x7wwl               1/1     Running   0          47m     192.168.199.38   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running   0          7h1m    192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending   0          5h11m   <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running   0          47m     192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running   0          47m     192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-kfmkq             1/1     Running   0          74s     192.168.199.48   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-r6hzl           1/1     Running   0          47m     192.168.199.42   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get po -o wide[Kdelete po worker-dd46d7584-r6hzl
pod "worker-dd46d7584-r6hzl" deleted
^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl delete po worker-dd46d7584-r6hzl[18Pget po -o wide
NAME                             READY   STATUS        RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-x7wwl               1/1     Running       0          47m     192.168.199.38   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running       0          7h2m    192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending       0          5h11m   <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running       0          47m     192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running       0          47m     192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-kfmkq             1/1     Running       0          107s    192.168.199.48   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-h67zd           1/1     Running       0          13s     192.168.199.41   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-r6hzl           1/1     Terminating   0          47m     192.168.199.42   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get po -o wide
NAME                             READY   STATUS        RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-x7wwl               1/1     Running       0          48m     192.168.199.38   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running       0          7h2m    192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending       0          5h12m   <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running       0          48m     192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running       0          48m     192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-kfmkq             1/1     Running       0          2m6s    192.168.199.48   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-h67zd           1/1     Running       0          32s     192.168.199.41   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-r6hzl           0/1     Terminating   0          48m     192.168.199.42   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get po -o widedelete po worker-dd46d7584-r6hzl[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[K[Kdb-b54cd94f4-x7wwl
pod "db-b54cd94f4-x7wwl" deleted
^C
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl delete po db-b54cd94f4-x7wwl[14Pget po -o wide
NAME                             READY   STATUS        RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-x7wwl               1/1     Terminating   0          48m     192.168.199.38   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
db-b54cd94f4-z24ph               1/1     Running       0          12s     192.168.199.51   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running       0          7h3m    192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending       0          5h12m   <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running       0          48m     192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running       0          48m     192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-kfmkq             1/1     Running       0          2m38s   192.168.199.48   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-h67zd           1/1     Running       0          64s     192.168.199.41   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get po -o wide
NAME                             READY   STATUS    RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-z24ph               1/1     Running   0          76s     192.168.199.51   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running   0          7h4m    192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending   0          5h13m   <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running   0          49m     192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running   0          49m     192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-kfmkq             1/1     Running   0          3m42s   192.168.199.48   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-h67zd           1/1     Running   1          2m8s    192.168.199.41   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# 
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# 
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# 
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# kubectl get po -o wide
NAME                             READY   STATUS    RESTARTS   AGE     IP               NODE                                               NOMINATED NODE   READINESS GATES
db-b54cd94f4-z24ph               1/1     Running   0          2m4s    192.168.199.51   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
fortune-configmap-volume         2/2     Running   0          7h5m    192.168.199.24   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
mavenir-mysql-54f7ddc699-4f8mq   0/1     Pending   0          5h14m   <none>           <none>                                             <none>           <none>
redis-868d64d78-fsstx            1/1     Running   0          50m     192.168.199.45   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-wtcpj          1/1     Running   0          50m     192.168.199.31   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-kfmkq             1/1     Running   0          4m30s   192.168.199.48   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-h67zd           1/1     Running   1          2m56s   192.168.199.41   ip-172-31-31-186.ap-southeast-1.compute.internal   <none>           <none>
]0;root@ip-172-31-24-58:~/example-voting-app/k8s-specifications[root@ip-172-31-24-58 k8s-specifications]# exit
logout
]0;ec2-user@ip-172-31-24-58:~[ec2-user@ip-172-31-24-58 ~]$ exit
logout


Observations:
1.voting result are not update becuase DB pod is deleted.
2. we required to deleted the result pod to update the results.
######################################################################################################################################################

