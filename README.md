# k8s-installer
- CentOS 7.4 >
- Kubernetes v1.18
- Docker-ce

# configuration
group_vars/all.yml 을 수정한다.
```yaml
# 마스터 노드 isolation
master_isolation: "yes"
master_host_name: "bskim-master"
master_ip: 10.20.200.125

# Container type : docker or containerd
container_type: "docker"
docker_default_path: "/var/lib/docker"
docker_version: "docker-ce-18.06.3.ce-3.el7"
containerd_release_version: 1.1.0-rc.0
# kubernetes version 명시
kubernetes_version: "1.18.0"
timezone: Asia/Seoul
# ingress controller 설치가 필요한 경우, yes
ingress_controller: "nginx"
# helm chart 설치가 필요한 경우, yes
helm_enabled: "yes"

# network cni 
network_cni: "calico"

# pod ip
pod_network_cidr: "192.168.0.0/16"
docker_cidr: "172.17.0.1/16"
service_cidr: "10.96.0.0/12"
kubelet_clusterdns: "10.96.0.10"
kubernetes_clusterip: "10.96.0.1"

```

# install 
```bash
ansible-playbook -i hosts all.yml
```

# Uninstall
```bash
ansible-playbook -i hosts kube-teardown.yml
```