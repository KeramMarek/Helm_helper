Chart: is collectin of yaml files. 

Release: installed chart in K8s.

Config: configurations in the values.yaml file and contains config explicit to a release of k8s app

Repository: place of published charts.

Hub: helps to find charts hosted in many distributed repositories.

#### shows repos after addding them localy:
```bash
helm repo list
```
#### remove your repo:
```bash
helm repo remove repo_name
````
#### insall your chart:
```bash
helm install name_it bitnami/nginx
```
### you can check the status of that release:
```bash
helm status nameofyouinstalledchart
```

#### pulling the repo:
```bash
helm pull bitnami/nginx --untar
```

by pulling the repo you will have zip pacage .tgz that you can tar -vdf  nameoffile.tgz it contains list yaml manifests. 

#### to check your installed charts:
```bash
helm list
```
 #### we can check manifest of the installed release:
 ```bash
helm get manifest nameofrelease
```

#### to unistall helm release:
```bash
helm unistall releasename
```
chart is zip of yaml manifests but it also contains some metadata that we can examine by: helm show all, chart, crds, readme, values

```bash
helm show chart bitnami/nginx
```
this should show info abot the chart. And values are all the things you can congigure

#### to check version of all the charts:
```bash
helm search repo bitnami/nginx --versions | grep "nginx "
```
#### to change from one version of chart to the other: after the upgrade you will see revision number increas.
```bash
helm upgrade name_of_release bintmai/nginx --version 13.1.3
```
#### we can check history of revision:
```bash
helm history name_of_the_release
```
#### we can also rollback from new version to old with:
```bash
helm rollback name_of_the_release 1
```
number 1 is number of revision.

#### we can also scale the number of replicas when the release is already running by:
```bash
helm upgrade name_of_release bitnami/nginx --set replicaCount=2
```
just a note if you don't specify the app version it's gonna automaticaly use the latest.

if we have more changes to make we can make a file values.yaml and put all the parameters there like replicaCount: 4
```bash
helm upgrade name_of_release bitnami/nginx --values values.yaml
```
#### we can help ourself by creating our file from the oreginal values file and see what is there to change:
```bash
helm show values bitnami/nginx > values.default.yaml
```
#### example of helm command:
```bash
helm install name_of_release ectobiit/adminer --values values.yaml --namespace rambo --create-namespace
```
