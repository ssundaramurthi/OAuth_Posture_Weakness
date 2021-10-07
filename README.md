# OAuth_Posture_Weakness
## **What is OAuth?**

→ Authorization framework 

→ An open standard for access delegation

→ Enables websites and web applications to request limited access to a user's account on another application. Crucially, OAuth allows the user to grant this access without exposing their login credentials to the requesting application. 

→ Example, an application might use OAuth to request access to your email contacts list so that it can suggest people to connect with. 

### **OAuth authentication Flow**

For OAuth authentication mechanisms, the basic OAuth flows remain largely the same; the main difference is how the client application uses the data that it receives. From an end-user perspective, the result of OAuth authentication is something that broadly resembles SAML-based single sign-on (SSO). In these materials, we'll focus exclusively on vulnerabilities in this SSO-like use case.

OAuth authentication is generally implemented as follows:

1. The user chooses the option to log in with their social media account. The client application then uses the social media site's OAuth service to request access to some data that it can use to identify the user. This could be the email address that is registered with their account, for example.
2. After receiving an access token, the client application requests this data from the resource server, typically from a dedicated `/userinfo` endpoint.
3. Once it has received the data, the client application uses it in place of a username to log the user in. The access token that it received from the authorization server is often used instead of a traditional password.

## **How does OAuth 2.0 work?**

→ OAuth 2.0 developed to share access to specific data between applications. -> Defined by a series of interactions between three distinct parties, 

- **Client application** - The website or web application that wants to access the user's data.
- **Resource owner** - The user whose data the client application wants to access.
- **OAuth service provider** - The website or application that controls the user's data and access to it. They support OAuth by providing an API for interacting with both an authorization server and a resource serve

### OAuth Configuration

Once you know the hostname of the authorization server, you should always try sending a `GET` request to the following standard endpoints:

- `/.well-known/oauth-authorization-server`
- `/.well-known/openid-configuration`

### Why?

OAuth was not initially designed with authentication in mind; it was intended to be a means of delegating authorizations for specific resources between applications. However, many websites began customizing OAuth for use as an authentication mechanism. To achieve this, they typically requested read access to some basic user data and, if they were granted this access, assumed that the user authenticated themselves on the side of the OAuth provider.

### What's OpenID Connect?

OpenID Connect extends the OAuth protocol to provide a dedicated identity and authentication layer that sits on top of the basic OAuth implementation. It adds some simple functionality that enables better support for the authentication use case of OAuth.
