openID connect create

eksctl utils associate-iam-oidc-provider --cluster <name> --approve

eksctl create iamserviceaccount --cluster=<clusterName> --name=<serviceAccountName> --namespace=<namespace> --attach-policy-arn=<policyArn>

aws command to access secret:

aws secretsmanager get-secret-value --secret-id roboshop/dev/mysql/password --query SecretString --output text


