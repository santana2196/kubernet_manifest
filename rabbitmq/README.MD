# Rabbitmq

###### root@master:~# kubectl get pods -A
###### NAMESPACE        NAME                                       READY   STATUS    RESTARTS        AGE
###### kube-system      calico-kube-controllers-74d5f9d7bb-fhcsx   1/1     Running   0               112s
###### kube-system      calico-node-8bvbj                          1/1     Running   0               112s
###### kube-system      coredns-76f75df574-bvlgm                   1/1     Running   0               112s
###### kube-system      coredns-76f75df574-pcxwf                   1/1     Running   0               112s
###### kube-system      etcd-master                                1/1     Running   1 (3m33s ago)   47s
###### kube-system      kube-apiserver-master                      1/1     Running   1 (3m33s ago)   41s
###### kube-system      kube-controller-manager-master             1/1     Running   1 (3m33s ago)   32s
###### kube-system      kube-proxy-rj8gm                           1/1     Running   0               112s
###### kube-system      kube-scheduler-master                      1/1     Running   1 (3m33s ago)   29s
###### metallb-system   controller-67d9f4b5bc-x2qdg                1/1     Running   0               112s
###### metallb-system   speaker-c7zrz                              1/1     Running   0               112s

###### root@master:~# kubectl apply -f  pv.yaml
###### persistentvolume/pv-volume-rabbitmq01 created
###### persistentvolume/pv-volume-rabbitmq02 created
###### persistentvolume/pv-volume-rabbitmq03 created

###### root@master:~# kubectl apply -f cluster-operator.yaml
###### namespace/rabbitmq-system created
###### customresourcedefinition.apiextensions.k8s.io/rabbitmqclusters.rabbitmq.com created
###### serviceaccount/rabbitmq-cluster-operator created
###### role.rbac.authorization.k8s.io/rabbitmq-cluster-leader-election-role created
###### clusterrole.rbac.authorization.k8s.io/rabbitmq-cluster-operator-role created
###### clusterrole.rbac.authorization.k8s.io/rabbitmq-cluster-service-binding-role created
###### rolebinding.rbac.authorization.k8s.io/rabbitmq-cluster-leader-election-rolebinding created
###### clusterrolebinding.rbac.authorization.k8s.io/rabbitmq-cluster-operator-rolebinding created
###### deployment.apps/rabbitmq-cluster-operator created

###### root@master:~# kubectl create ns rabbitmq
###### namespace/rabbitmq created

###### root@master:~# kubectl apply -f rabbitmqcluster.yaml -n rabbitmq
###### rabbitmqcluster.rabbitmq.com/production-rabbitmqcluster created

###### root@master:~# kubectl get pods -A
###### NAMESPACE         NAME                                        READY   STATUS     RESTARTS        AGE
###### kube-system       calico-kube-controllers-74d5f9d7bb-5vv8r    1/1     Running    0               4m21s
###### kube-system       calico-node-lz8fm                           1/1     Running    0               4m21s
###### kube-system       coredns-76f75df574-2k2f5                    1/1     Running    0               4m21s
###### kube-system       coredns-76f75df574-6m75b                    1/1     Running    0               4m21s
###### kube-system       etcd-master                                 1/1     Running    2 (6m20s ago)   3m13s
###### kube-system       kube-apiserver-master                       1/1     Running    2 (6m20s ago)   3m5s
###### kube-system       kube-controller-manager-master              1/1     Running    2 (6m20s ago)   3m13s
###### kube-system       kube-proxy-65dwx                            1/1     Running    0               4m21s
###### kube-system       kube-scheduler-master                       1/1     Running    2 (6m20s ago)   3m14s
###### metallb-system    controller-67d9f4b5bc-qgnc2                 1/1     Running    0               4m21s
###### metallb-system    speaker-l2df4                               1/1     Running    0               4m21s
###### rabbitmq-system   rabbitmq-cluster-operator-9ff66fdbd-k8q95   1/1     Running    0               4m21s
###### rabbitmq          production-rabbitmqcluster-server-0         0/1     Init:0/1   0               2s
###### rabbitmq          production-rabbitmqcluster-server-1         0/1     Init:0/1   0               2s
###### rabbitmq          production-rabbitmqcluster-server-2         0/1     Init:0/1   0               2s

###### root@master:~# kubectl get pvc -A
###### NAMESPACE   NAME                                              STATUS   VOLUME                 CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
###### rabbitmq    persistence-production-rabbitmqcluster-server-0   Bound    pv-volume-rabbitmq01   30G        RWO                           <unset>                 103s
###### rabbitmq    persistence-production-rabbitmqcluster-server-1   Bound    pv-volume-rabbitmq03   30G        RWO                           <unset>                 103s
###### rabbitmq    persistence-production-rabbitmqcluster-server-2   Bound    pv-volume-rabbitmq02   30G        RWO                           <unset>                 103s

###### root@master:~# kubectl get pods -A
###### NAMESPACE         NAME                                        READY   STATUS    RESTARTS       AGE
###### kube-system       calico-kube-controllers-74d5f9d7bb-5vv8r    1/1     Running   0              6m9s
###### kube-system       calico-node-lz8fm                           1/1     Running   0              6m9s
###### kube-system       coredns-76f75df574-2k2f5                    1/1     Running   0              6m9s
###### kube-system       coredns-76f75df574-6m75b                    1/1     Running   0              6m9s
###### kube-system       etcd-master                                 1/1     Running   2 (8m8s ago)   5m1s
###### kube-system       kube-apiserver-master                       1/1     Running   2 (8m8s ago)   4m53s
###### kube-system       kube-controller-manager-master              1/1     Running   2 (8m8s ago)   5m1s
###### kube-system       kube-proxy-65dwx                            1/1     Running   0              6m9s
###### kube-system       kube-scheduler-master                       1/1     Running   2 (8m8s ago)   5m2s
###### metallb-system    controller-67d9f4b5bc-qgnc2                 1/1     Running   0              6m9s
###### metallb-system    speaker-l2df4                               1/1     Running   0              6m9s
###### rabbitmq-system   rabbitmq-cluster-operator-9ff66fdbd-k8q95   1/1     Running   0              6m9s
###### rabbitmq          production-rabbitmqcluster-server-0         1/1     Running   0              110s
###### rabbitmq          production-rabbitmqcluster-server-1         1/1     Running   0              110s
###### rabbitmq          production-rabbitmqcluster-server-2         1/1     Running   0              110s

###### root@master:~# kubectl get service -n rabbitmq
###### NAME                               TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)                                          AGE
###### production-rabbitmqcluster         LoadBalancer   10.105.201.40   192.168.0.100   5672:30255/TCP,15672:32232/TCP,15692:32502/TCP   11m
###### production-rabbitmqcluster-nodes   ClusterIP      None            <none>          4369/TCP,25672/TCP                               11m

###### root@master:~# telnet  192.168.0.100 15672
###### Trying 192.168.0.100...
###### Connected to 192.168.0.100.
###### Escape character is '^]'.

