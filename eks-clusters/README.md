#### Create EKS Cluster using eksctl
```
# Create cluster without nodegroup
eksctl create cluster --name=eks-demo --region=us-east-1  --zones=us-east-1a,us-east-1b  --without-nodegroup

# List clusters
eksctl get cluster
```

#### Create & Associate IAM OIDC Provider for the EKS Cluster (optional)
- To enable and use AWS IAM roles with Kubernetes service accounts on EKS cluster, you need to create & associate OIDC identity provider.
```
eksctl utils associate-iam-oidc-provider \
    --region us-east-1 \
    --cluster eks-demo \
    --approve
```

#### Create a Node Group in Public Subnets
```
# Create Public Node Group   
eksctl create nodegroup --cluster=eks-demo \
                       --region=us-east-1 \
                       --name=ng-public1 \
                       --node-type=t3.small \
                       --nodes=2 \
                       --nodes-min=2 \
                       --nodes-max=4 \
                       --node-volume-size=20 \
                       --ssh-access \
                       --ssh-public-key=my-key \
                       --managed \
                       --asg-access \
                       --external-dns-access \
                       --full-ecr-access \
                       --appmesh-access \
                       --alb-ingress-access 

```
#### Commands to check delete eks Cluster
```
# List EKS clusters
eksctl get cluster

# List NodeGroups in a cluster
eksctl get nodegroup --cluster=eks-demo

# List Nodes in current kubernetes cluster
kubectl get nodes -o wide

# Our kubectl context should be automatically changed to new cluster
kubectl config view --minify

# Delete Node Group
eksctl delete nodegroup --cluster=eks-demo --name=ng-public1

# Delete Cluster
eksctl delete cluster eks-demo

```
