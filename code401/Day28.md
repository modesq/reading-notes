# class 28

## Authentication & Production Server

### What is JSON Web Token?

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

Although JWTs can be encrypted to also provide secrecy between parties, we will focus on signed tokens. Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

### When should you use JSON Web Tokens?

Here are some scenarios where JSON Web Tokens are useful:

- Authorization: This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.

- Information Exchange: JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

### Django Runserver Is Not Your Production Server

You’ve built your Django web app and are working on deploying it.

You’ve been running your app locally with python manage.py runserver. That’s a fine command, built for development convenience, but it’s not meant to be used as part of a production setup.

The docs are very adamant about this:

DO NOT USE THIS SERVER IN A PRODUCTION SETTING. It has not gone through security audits or performance tests.

So the server started with runserver is not guaranteed to be performant (it’s very slow), and it hasn’t been built with security concerns in mind. Not a good fit for production use.

So, what’s the right way to approach this?

#### A Production Stack

You want to only use tech in production, which is reliable, well tested and has been around for a while.

A production setup usually consists of multiple components, each designed and built to be really good at one specific thing. They are fast, reliable and very focused.

When a request arrives at your server, it should be passed to a dedicated web server. Nginx is an example for a good web server.

This is an application, which is great at serving static files from disk (your css and js files for example) and handling multiple requests at once. If the request is not for a static file, but should be processed by your application, the webserver is configured to pass this request to the next component.

The next component is an application server. It gets those fancy requests and uses them to construct Python objects which are usable by Django. WSGI is a specification which people agreed on, which describe how that happens. Gunicorn is an example for a WSGI server.
