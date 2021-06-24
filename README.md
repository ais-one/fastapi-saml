## Description

Implementing SAML on FastAPI using Keycloak & python3-saml...

with less than 100 lines-of-code

## References

- https://medium.com/@gohberg/okta-authentication-using-saml-simplified-python-version-74ea9d5b4be7
- https://fastapi.tiangolo.com/
- https://github.com/onelogin/python3-saml

## Requirements
- Windows 10 (with bash commands), if Linux or MacOS, just need to run the commands in Linux way, e.g. / instead of \\
- Docker
- Python 3.8+

## Setup Keycloak

Refer to the following repository README.md for running Keycloak using docker-compose and setting up a SAML2 client on Keycloak

https://github.com/ais-one/vue-crud-x/tree/master/docker-devenv/keycloak

**Note:**
- please follow the names used, e.g. realm is test (appears as Test on Keycloak UI) if not there could be configuration problems
- Ignore the section on SAML Step 7 as it is already setup, except replace the cert ("x509cert" in main.py) with the cert generated in the Keycloak Realm that you created (see **Realm Settings -> Keys** on Keycloak admin UI)
- Ignore the section on OIDC setup

## SAML Sample Application Installation
```cmd
python -m venv dev
dev\Scripts\activate

pip install fastapi uvicorn[standard] python3-saml python-multipart

uvicorn main:app --reload --port 3000
```

## Testing

With application running, navigate to http://127.0.0.1:3000/api/saml/login on the browser to initiate redirect to IDP

SAML Response is sent to http://127.0.0.1:3000/api/saml/login/callback

## API Documentation

With application running, navigate to [http://127.0.0.1:3000/docs](http://127.0.0.1:3000/docs) on the browser for API documentation
