# Amazon Cognito

## User Pools
- A user pool is a user directory in Amazon Cognito. With a user pool, your users can sign-up and sign-in to your web or mobile app through Amazon Cognito

## Identity Pools
- Amazon Cognito identity pools enable you to create unique identities for your users and authenticate them with identity providers. With an identity, you can obtain temporary, limited-privilege AWS credentials to access other AWS services. Amazon Cognito identity pools support public identity providers—Amazon, Apple, Facebook, and Google—as well as unauthenticated identities. It also supports developer authenticated identities, which let you register and authenticate users via your own back-end authentication process. Think of User Pools as providing authentication, and Identity Pools as providing authorization.

## Web Identity Federation
- Web identity federation removes the need for creating individual IAM users. Instead, users can sign in to an identity provider and then obtain temporary security credentials from AWS Security Token Service (AWS STS).
- With web identity federation, you don't need to create custom sign-in code or manage your own user identities. Instead, users of your app can sign in using a well-known external identity provider (IdP), such as Login with Amazon, Facebook, Google, or any other OpenID Connect (OIDC)-compatible IdP.