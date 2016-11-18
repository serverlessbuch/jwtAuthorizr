# jwtAuthorizer - Custom JWT Lambda Authorizer for AWS API Gateway

A _Custom Authorizer_ [AWS Lambda](https://aws.amazon.com/lambda) function for [AWS API Gateway](https://aws.amazon.com/api-gateway) which takes a [JSON Web Token (JWT)](https://jwt.io) in `Bearer` format from `Authorization` HTTP header.

[Read more about Custom Authorizers at AWS Docs.](http://docs.aws.amazon.com/de_de/apigateway/latest/developerguide/use-custom-authorizer.html)

The JWT is verified agains a public key (in case of RSA encryption) and some other claims (should be at least `audience` and `issuer`).

The **jwtAuthorizr** lambda function makes use of the aweseome [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) package at NPM.

Public key and claims can be different for every used stage environment.
In this example, **jwtAuthorizr** lambda function loads it from S3, but could also be loaded from DynamoDB.
Unfortunately, there's no way to read it from the API Gateway stage variables, yet.
Hopefully this will be possible in the future.
_(It's generally possible to read stage variables in a pure Lambda function, executed by a API Gateway event (aka request), but it's currently not possible to get it in custom authorizer functions.)_

This project comes with a Cloudformation template containing all the needed resources for a demo setup, see `resources.cfn.yml`.  
You can find some handy scripts in `package.json` for your convenience.  
So it should be easy for you to test and play around with it.

Any feedback is appreciated.  
Thanks - have fun exploring the _serverless_ cloud!
