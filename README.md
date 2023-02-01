# springboot-crud-k8s
Run &amp; Deploy Spring Boot CRUD Application With MySQL on K8S


<h2>Kubernetes Status</h2>
<pre>
[ec2-user@ip-172-31-85-97 ~]$ k get all
NAME                                              READY   STATUS    RESTARTS      AGE
pod/angular-app                                   1/1     Running   4 (11h ago)   42h
pod/mysql-fb4dd8d-k9sp6                           1/1     Running   1 (11h ago)   14h
pod/springboot-crud-deployment-7f9bb7cfdb-8946p   1/1     Running   0             92m
pod/springboot-crud-deployment-7f9bb7cfdb-mnnrd   1/1     Running   0             92m
pod/springboot-crud-deployment-7f9bb7cfdb-xsmjz   1/1     Running   0             12h

NAME                          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
service/kubernetes            ClusterIP   10.96.0.1       <none>        443/TCP          20d
service/mysql                 NodePort    10.97.199.243   <none>        3306:31819/TCP   12h
service/springboot-crud-svc   NodePort    10.110.62.170   <none>        8080:30463/TCP   12h

NAME                                         READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/mysql                        1/1     1            1           14h
deployment.apps/springboot-crud-deployment   3/3     3            3           12h

NAME                                                    DESIRED   CURRENT   READY   AGE
replicaset.apps/mysql-fb4dd8d                           1         1         1       14h
replicaset.apps/springboot-crud-deployment-7f9bb7cfdb   3         3         3       12h
replicaset.apps/springboot-crud-deployment-7fb5f8fc9c   0         0         0       12h

[ec2-user@ip-172-31-85-97 ~]$ k port-forward service/springboot-crud-svc --address=0.0.0.0 8080:8080
Forwarding from 0.0.0.0:8080 -> 8989
Handling connection for 8080

^C[ec2-user@ip-172-31-85-97 ~]$ k get po
NAME                                          READY   STATUS    RESTARTS      AGE
angular-app                                   1/1     Running   4 (11h ago)   42h
mysql-fb4dd8d-k9sp6                           1/1     Running   1 (11h ago)   14h
springboot-crud-deployment-7f9bb7cfdb-8946p   1/1     Running   0             70m
springboot-crud-deployment-7f9bb7cfdb-mnnrd   1/1     Running   0             70m
springboot-crud-deployment-7f9bb7cfdb-xsmjz   1/1     Running   0             11h
[ec2-user@ip-172-31-85-97 ~]$ k port-forward service/springboot-crud-svc --address=0.0.0.0 8080:8080
Forwarding from 0.0.0.0:8080 -> 8989
Handling connection for 8080
</pre>
<img src="https://github.com/Krreesh/springboot-crud-k8s/blob/main/spring_application.JPG">
<h2>Minikube Dashboard</h2>
<pre>
[ec2-user@ip-172-31-85-97 ~]$ minikube dashboard
* Verifying dashboard health ...
* Launching proxy ...
* Verifying proxy health ...
* Opening http://127.0.0.1:37925/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ in your default browser...
  http://127.0.0.1:37925/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
</pre>
<h2>Started kube proxy to view dashboard in browser</h2>
<img src="https://github.com/Krreesh/springboot-crud-k8s/blob/main/k8s-dashboard.JPG">
<pre>
[ec2-user@ip-172-31-85-97 ~]$ k proxy --address=0.0.0.0 --accept-hosts '.*'
Starting to serve on [::]:8001
</pre>
