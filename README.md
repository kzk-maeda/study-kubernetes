# Hello World

```
// kubectl run <POD NAME> --image <IMAGE NAME> --restart=Never
$ kubectl run hello-world --image hello-world --restart=Never
pod/hello-world created

// Confirm created Pod
$ kubectl get pod
NAME          READY   STATUS      RESTARTS   AGE
hello-world   0/1     Completed   0          39s

// Confirm Pod logs
$ kubectl logs pod/hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

// Delete created Pod
$ kubectl delete pod/hello-world
pod "hello-world" deleted

$ kubectl get pod
No resources found in default namespace.
```

# Resourses

* Create manufest file

```pod.yml
apiVersion: v1
kind: Pod
metadata:
  name: test
  namespace: default
  labels:
    env: study
spec:
  containers:
  - name: hello-world
    image: hello-world

```

* control

```
$ kubectl apply -f pod.yml
pod/test created

$ kubectl get all
NAME       READY   STATUS             RESTARTS   AGE
pod/test   0/1     CrashLoopBackOff   1          27s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   3h13m

$ kubectl get -f pod.yml
NAME   READY   STATUS             RESTARTS   AGE
test   0/1     CrashLoopBackOff   2          34s

$ kubectl delete -f pod.yml
pod "test" deleted 
```

