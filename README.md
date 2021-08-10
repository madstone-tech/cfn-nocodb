# Deploy NocodB on AWS via Cloudformation

## Steps

### Install AWS CLI

Install [AWS CLI][awsclilink]

### Create an S3 bucket to upload the template artifacts

```bash
aws s3 mb s3://[bucketname]
```

### Package the Cloudformation Package

```bash
aws cloudformation package --template-file cfn-templates/cfn-main.yaml --s3-bucket [bucketname] --output-template-file cfn-deploy.yaml
```

### Update your paramaters

replace `parameters/cfn-parameters.json` with the parameters from your account.

### Deploy Stack

#### Deploy via cli

```bash
aws cloudformation deploy --template-file cfn-deploy.yaml --stack-name <YOUR STACK NAME> --parameter-overrides file://parameters/cfn-parameters.json --capabilities CAPABILITY_IAM
```

[awsclilink]: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html
