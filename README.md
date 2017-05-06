# jwtAuthorizer - Custom JWT AWS Lambda Authorizer for Amazon API Gateway

A _Custom Authorizer_ [AWS Lambda](https://aws.amazon.com/lambda) function for [Amazon API Gateway](https://aws.amazon.com/api-gateway) which takes a [JSON Web Token (JWT)](https://jwt.io) in `Bearer` format from `Authorization` HTTP header.

[Read more about Custom Authorizers at AWS Docs.](http://docs.aws.amazon.com/de_de/apigateway/latest/developerguide/use-custom-authorizer.html)

The JWT is verified against a secret (in case of HSA encryption) and some other claims (should be at least `audience` and `issuer`).

The **jwtAuthorizr** lambda function makes use of the aweseome [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) package at NPM.

Secret and claims can be different for every used stage environment.
In this example, **jwtAuthorizr** lambda function reads them from environment variables which should be baked into the function deployment for each stage.
But Lambda could also load them from e.g. S3 or DynamoDB or something completely different.
