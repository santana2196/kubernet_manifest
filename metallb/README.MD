# Metallb - para caso precise de expor aplicação via loadbalancer local

###### kubectl apply -f metallb-native.yaml
###### kubectl get service
###### kubectl get pods -A
###### kubectl apply -f ipaddresspool.yaml
###### kubectl apply -f l2advertisement.yaml
###### kubectl get service
###### kubectl get pods -A
###### kubectl expose pod mysql-openshift --type LoadBalancer --port 3306 --target-port 3306
###### telnet 192.168.0.101 3306
