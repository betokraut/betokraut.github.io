<!-- comments -->

## Install & Configure on Ubuntu

```bash

sudo apt install gnome-terminal

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get install ./docker-desktop-4.10.0-amd64.deb

Settings > Kubernetes > enable

curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm

snap install kubectl --classic

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/cloud/deploy.yaml

kubectl get all --namespace ingress-nginx

127.0.0.1	localhost default-example-solrcloud.ing.local.domain ing.local.domain default-example-solrcloud-0.ing.local.domain default-example-solrcloud-1.ing.local.domain default-example-solrcloud-2.ing.local.domain dinghy-ping.localhost

helm repo add apache-solr https://solr.apache.org/charts
helm repo update

kubectl create -f https://solr.apache.org/operator/downloads/crds/v0.5.1/all-with-dependencies.yaml

helm install solr-operator apache-solr/solr-operator --version 0.5.1

kubectl get all

helm install example-solr apache-solr/solr --version 0.5.1 \
  --set image.tag=8.3 \
  --set solrOptions.javaMemory="-Xms300m -Xmx300m" \
  --set addressability.external.method=Ingress \
  --set addressability.external.domainName="ing.local.domain" \
  --set addressability.external.useExternalAddress="true" \
  --set ingressOptions.ingressClassName="nginx"

curl "http://default-example-solrcloud.ing.local.domain/solr/admin/collections?action=CREATE&name=mycoll&numShards=1&replicationFactor=3&maxShardsPerNode=2&collection.configName=_default"

http://default-example-solrcloud.ing.local.domain/solr/#/~cloud?view=graph

curl -XPOST -H "Content-Type: application/json" \
    -d '[{id: 1}, {id: 2}, {id: 3}, {id: 4}, {id: 5}, {id: 6}, {id: 7}, {id: 8}]' \
    "http://default-example-solrcloud.ing.local.domain/solr/mycoll/update/"

```   
