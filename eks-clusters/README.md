#### Create EKS Cluster using eksctl
```
# Create cluster without nodegroup
eksctl create cluster --name=eks-demo --region=us-east-1  --zones=us-east-1a,us-east-1b  --without-nodegroup

# List clusters
eksctl get cluster
```

#### Create & Associate IAM OIDC Provider for the EKS Cluster (optional)
```
eksctl utils associate-iam-oidc-provider \
    --region us-east-1 \
    --cluster eks-demo \
    --approve
```
