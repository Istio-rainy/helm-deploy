# helm-deploy 
> 此项目进行管理所有需要部署到k8s的编排。


# 项目charts介绍

```
.
└── casdoor                 # 用户服务
```
- 子Chart 介绍

chart名|介绍
---|---
casdoor|开源的用户中心 [casdoor Home](https://casdoor.org/docs/deploy/k8s)
|
|
|
|
|
|
|

# helm私仓库

> 本项目采用阿里云helm私仓库 [传送地址](https://repomanage.rdc.aliyun.com/my/helm-repos/namespaces)

## 仓库使用方法
添加Helm仓库(基于安全考虑页面上不显示密码)
```
export NAMESPACE=73181-hcloud
export HELM_PASSWORD=****

helm repo add $NAMESPACE https://repomanage.rdc.aliyun.com/helm_repositories/$NAMESPACE --username=Oyl1Uo --password=$HELM_PASSWORD
```
## 发布Chart
1. 安装 Helm push 插件

```
helm plugin install https://github.com/chartmuseum/helm-p
```

2. 发布 Chart 目录
```
helm cm-push mychart/ $NAMESPACE
```

3. 发布 Chart 压缩包

```
helm package mychart
helm cm-push mychart-0.3.2.tgz $NAMESPACE
```

4. 更新本地索引

```
helm repo update
```

5. 搜索 Chart

```
helm search $NAMESPACE/mychart
```

6. 安装 Chart

```
helm install $NAMESPACE/mychart
```
   
## 测试helm是否正确
```
cd charts/
helm install casdor ./casdor --dry-run --debug --kube-apiserver https://localhost:8443/k8s/clusters/c-m-rwvh7hgs  --kube-token kubeconfig-u-**
```