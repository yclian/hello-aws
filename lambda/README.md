# README

Lambda function(s) to help migrating from Bitbucket to Github. Took the boilerplate out of [irvinlim/es2017-lambda-boilerplate](https://github.com/irvinlim/es2017-lambda-boilerplate).

Bootstrap the stack with CloudFormation, as followed. Take note that node CodeBuild/CodePipeline is configured.

```bash
$ aws cloudformation update-stack --stack-name bitbucket-to-github --template-body file://support/stack.yml --capabilities CAPABILITY_NAMED_IAM
$ npm run deploy
```

To run locally, use [lambci/docker-lambda](https://github.com/lambci/docker-lambda):

```bash
$ https://github.com/lambci/docker-lambda
```

Or in Lambda:

```bash
$ aws lambda invoke --function-name bitbucket-to-github-utils invoke.out && cat invoke.out
```