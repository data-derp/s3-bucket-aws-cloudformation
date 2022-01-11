# S3 Bucket - AWS Cloudformation
This repository creates an S3 bucket via a Cloudformation template

**Warning:** this template creates AWS resources which incur costs.

This Cloudformation template sets up the following:
* A S3 bucket

## Setup
1. Add this to your Github repository as a submodule: `git submodule add git@github.com:data-derp/s3-bucket-aws-cloudformation.git`
    * This module creates AWS Resources which could incur costs
2. Set up your AWS CLI and authenticate to your AWS account. Run `export AWS_PROFILE=<the-profile-with-your-credentials>`
3. **OPTIONAL:** Switch your role.  For those expected to assume a role (within the same account) to perform AWS operations, there is a helper function:
```bash
./github-runner-aws-cloudformation/switch-role -b <starting-profile> -t <target-role>
```
This uses credentials in your `-b <starting-profile>` to switch into the `-t <target-role>`. You can now use the target role's credentials by using the AWS_PROFILE `data-derp`
```bash
export AWS_PROFILE=data-derp
```
4. Create the Stack.
```bash
./s3-bucket-aws-cloudformation/create-stack -p <your-project-name> -m <your-team-name> -r <aws-region>
```
:bulb: the `your-project-name` and `your-team-name` must be globally unique as an AWS S3 bucket is created (this resource is globally unique)

5. View your [Cloudformation Stacks in the AWS Console](https://eu-central-1.console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks)

6. When you're done, destroy your stack:
```bash
./s3-bucket-aws-cloudformation/delete-stack -p <your-project-name> -m <your-team-name> -r <aws-region>
```