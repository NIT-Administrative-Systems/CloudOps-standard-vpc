# Northwestern Standard Peered VPC Template

This repository contains an AWS Cloudformation template for a VPC that can peer
with the AWS shared services VPC.

Note that because the shared services VPC is in the us-east-2 (Ohio) region,
then if you intend to actually peer your VPC with the shared services VPC, you
must also launch into us-east-2. If you don't intend to peer and are just using
this template as an easy way to create a standard VPC, then you can launch in
any region.

Also note that if you intend to peer this VPC, then the CIDR range you specify
when creating the stack must be one assigned by TNS. If you do not intend to
peer then you can use any private subnet range.

The `CIDRRange` parameter should look like e.g. `10.28.100.0/24`.

To launch this stack you can use the following command:

    aws cloudformation create-stack --stack-name <STACKNAME> --template-body file://vpc.yaml --parameters ParameterKey=CIDRRange,ParameterValue=<CIDRRANGE> --tags Key=Environment,Value=<ENVIRONMENT> Key=Application,Value=PeeredVPC Key=Owner,Value=<OWNER>

Replacing the `STACKNAME`, `CIDRRANGE`, `ENVIRONMENT`, and `OWNER` place holders with appropriate values.