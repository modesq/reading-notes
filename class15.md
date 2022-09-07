# CLASS 15

## part 1

1. What is OAuth?

    OAuth, or open authorization, is a widely adopted authorization framework that allows you to consent to an application interacting with another on your behalf without having to reveal your password.
2. Give an example of what using OAuth would look like.

    it is used as a way for internet users to grant websites or applications access to their information on other websites but without giving them the passwords.
3. How does OAuth work? What are the steps that it takes to authenticate the user?

    by providing access tokens to third-party services without exposing user credentials.

    1. The first website connects to the second website on behalf of the user, using OAuth, providing the user’s verified identity.
    2. The second site generates a one-time token and a one-time secret unique to the transaction and parties involved.
    3. The first site gives this token and secret to the initiating user’s client software.
    4. The client’s software presents the request token and secret to their authorization provider (which may or may not be the second site).
    5. If not already authenticated to the authorization provider, the client may be asked to authenticate. After authentication, the client is asked to approve the authorization transaction to the second website.
    6. The user approves (or their software silently approves) a particular transaction type at the first website.
    7. The user is given an approved access token (notice it’s no longer a request token).
    8. The user gives the approved access token to the first website.
    9. The first website gives the access token to the second website as proof of authentication on behalf of the user.
    10. The second website lets the first website access their site on behalf of the user.
    11. The user sees a successfully completed transaction occurring.
4. What is OpenID?

    OpenID is for humans logging into machines, OAuth is for machines logging into machines on behalf of humans

## part 2

1. What is the difference between authorization and authentication?

     Authentication verifies the identity of a user or service, and authorization determines their access rights.
2. What is Authorization Code Flow?

    Authorization code flow is used to obtain an access token to authorize API requests.
3. What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?

    its an OpenId Connect flow specifically designed to authenticate native or mobile application users.
4. What is Implicit Flow with Form Post?

    web sign-in using OIDC in a way that is very similar to the way SAML and WS-Federation operates.
5. What is Client Credentials Flow?

    permissions are granted directly to the application itself by an administrator. When the app presents a token to a resource, the resource enforces that the app itself has authorization to perform an action since there is no user involved in the authentication
6. What is Device Authorization Flow?

    With input-constrained devices that connect to the internet, rather than authenticate the user directly, the device asks the user to go to a link on their computer or smartphone and authorize the device. This avoids a poor user experience for devices that do not have an easy way to enter text.
7. What is Resource Owner Password Flow?

    allows exchanging the username and password of a user for an access token and, optionally, a refresh token
