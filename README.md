# aws-secrets-access2_16
What is needed to authorize your EC2 to retrieve secrets from the AWS Secrets Manager?
To allow an EC2 instance to retrieve secrets from AWS Secrets Manager, the EC2 instance must have an IAM role attached. This IAM role should have a policy that grants the necessary permissions to access the Secrets Manager API and the specific secrets

Derive the IAM policy (i.e., JSON):json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "secretsmanager:GetSecretValue",
        "secretsmanager:DescribeSecret"
      ],
      "Resource": "arn:aws:secretsmanager:region:account-id:secret:prod/cart-service/credentials-*"
    }
  ]
}
Action: Grants permissions for retrieving the secret value and describing the secret.
Resource: Grants access specifically to the secret prod/cart-service/credentials.
Replace region and account-id with your AWS region and account ID.

Using the secret name prod/cart-service/credentials, derive a sensible ARN as the specific resource for access:
arn:aws:secretsmanager:region:account-id:secret:prod/cart-service/credentials-*

