Install OIDC provider

eksctl utils associate-iam-oidc-provider --cluster <name> --approve

2. Download IAM policy


curl -o iam-policy.json https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v3.1.0/docs/install/iam_policy.json

3. Create IAM Policy

aws iam create-policy \
    --policy-name AWSLoadBalancerControllerIAMPolicy \
    --policy-document file://iam-policy.json


4. Create service account and IAM role , map above policy

eksctl create iamserviceaccount \
--cluster=volumes-k8-dev \
--namespace=kube-system \
--name=aws-load-balancer-controller \
--attach-policy-arn=arn:aws:iam::444353257404:policy/AWSLoadBalancerControllerIAMPolicy \
--override-existing-serviceaccounts \
--region us-east-1 \
--approve

5. helm installation

6.Add eks chart repo 
helm repo add eks https://aws.github.io/eks-charts


7. Install load balancer controller

helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=volumes-k8-dev --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller

8.Check drivers are running