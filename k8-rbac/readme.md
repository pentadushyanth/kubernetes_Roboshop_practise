openID connect create

eksctl utils associate-iam-oidc-provider --cluster <name> --approve

eksctl create iamserviceaccount --cluster=<clusterName> --name=<serviceAccountName> --namespace=<namespace> --attach-policy-arn=<policyArn>
