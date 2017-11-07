# gcr.io


docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/tiller:v2.3.0

docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/pause-amd64:3.0

docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/k8s-dns-kube-dns-amd64:1.14.2
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/k8s-dns-kube-dns-amd64:1.14.5
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/k8s-dns-dnsmasq-nanny-amd64:1.14.2
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/k8s-dns-dnsmasq-nanny-amd64:1.14.5
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/k8s-dns-sidecar-amd64:1.14.2
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/k8s-dns-sidecar-amd64:1.14.5

docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/kubernetes-dashboard-amd64:v1.6.1

docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/heapster-grafana-amd64:v4.0.2
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/heapster-amd64:v1.3.0-beta.1
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/heapster-influxdb-amd64:v1.1.1
docker pull registry.cn-hangzhou.aliyuncs.com/zhugaoxiao/heapster-influxdb-amd64:v1.3.3

docker images |grep egistry.cn-hangzhou.aliyuncs.com | sed 's/registry.cn-hangzhou.aliyuncs.com\/zhugaoxiao\//gcr.io\/google_containers\//' | awk '{print "docker tag "$3" "$1":"$2""}' | tail -6 | sh

docker images |grep egistry.cn-hangzhou.aliyuncs.com | awk '{print $1":"$2}' | xargs -t -i docker rmi {}

mkdir -p gcr.io/google_containers

docker images |grep gcr | awk  '{print $1":"$2 }' | xargs -t -i docker save {} -o {}.tar
