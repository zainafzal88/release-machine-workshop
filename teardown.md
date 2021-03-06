# Teardown

Most of the infrastructure can be destroyed via the tools we have used to create it - CDK and CloudFormation.

While CDK offers an explicit `destroy` option, SAM does not.

## Before you start

Empty your S3 buckets. S3 buckets that are not empty will make CloudFormation stack deletions fail. You will need to [go to the S3 console](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-2) and empty the buckets that we created - they should start with `release-machine-` so hopefully are easy to find.

> Make sure you **show all versions** in the release bucket, as you will need to also remove any old versions of files that were copied up more than once.

## Let the destruction begin!

Once you have manually emptied the S3 buckets, head to the CloudFormation console to delete the `release-machine` stack (noting that you may have called it something different, in which case, it's whatever you called it).

Then go into the `cdk-serverless-stack` directory on your machine and issue the following commands:

```
cdk destroy CdkServerlessStack
cdk destroy RepoStack
```

That should tear down all the resources created in Part One.
