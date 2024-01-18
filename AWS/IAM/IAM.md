* IAM Stands for Identity and Access Management.
* We use IAM to control who is authenticated (signed in) and authorized
(has permissions) to use resources.
Features of IAM:
----------------
## Shared access to your AWS account
  * You can grant permission to other people and use resources without sharing your password or access key  
##  Granular permissions
  * You can grant different permissions to different people like for some people you can grant full permissions on EC2 instances and for some people you can allow read-only access.
## Secure access to AWS resources for applications that run on Amazon EC2
  * You can use IAM features to securely provide credentials for applications that run on EC2 instances.
  * For example you are hosting a static website and the code of that application resides in S3 bucket. You need to have permissions for EC2 instance to access S3 bucket. You can control that using IAM.
## Multi-factor authentication (MFA)
  * For extra security you can add two factor authentication to your account using IAM. With MFA users should provide not only a password or access key to work with your
  account, but also a code from a specially configured device.
## Identity federation
  * You can allow users who already have passwords elsewhere—for example, in your corporate
network or with an internet identity provider—to get temporary access to your AWS account.
  * As an example we can say suppose a user in on-premise who does not have AWS credentials but has an identity in on-premise directory store and want to access the S3 bucket we use Identity federation to provide temporary access to the user. Providing access involves following steps
    1. Client application attempts to authenticate using IdP(Identity provider like Active directory)
    2. IdP authenticates the user.
    3. IdP sends SAML assertion
    4. App calls sts:AssumeRoleWithSAML(STS - Security Token Service)
    5. AWS return temporary security credentials
## Identity information for assurance
  * If you use AWS CloudTrail, you receive log records that include information about those who made requests for resources in your account. That information is based on IAM identities.
## PCI DSS Compliance
  * IAM supports the processing, storage, and transmission of credit card data by a merchant or service provider, and has been validated as being compliant with Payment Card Industry (PCI) Data Security Standard (DSS).
## Integrated with many AWS services
  * IAM can be integrated with almost all the AWS services.
##  Eventually Consistent
  * Like many other services in AWS IAM is eventually consistent.
## Free to use
  * AWS IAM and AWS Security Token Service (AWS STS) are free to use. You will be charged only when you access other AWS services using your IAM users or AWS STS temporary security credentials.