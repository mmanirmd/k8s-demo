# Create EKS Cluster using eksctl

##Create Cluster 
eksctl create cluster --name=eks-demo \
                      --region=us-east-1 \
                      --zones=us-east-1a,us-east-1b \
                      --without-nodegroup 
