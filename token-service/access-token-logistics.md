# Access Token Logistics

### **Background**

All parties in the AA ecosystem are identified by a Sahamati certified access token generated by the Token Server. These tokens are valid for 24hrs and therefore, will need to be refreshed once a day.

### Generating An Access Token

The following section describes the headers and other parameters involved in the access token generation call to the Token Server.

#### Using Postman&#x20;

In the **Authorization tab** for a request or collection, set the following details:

1. Authorization **Type**: OAuth 2.0
2. **Grant Type** as Client Credentials.
3. Set Access Token URL to one of the URLs shared by Sahamati for PRODUCTION/UAT environments.
4. Set **Client ID** same as the entity ID in Central Registry (CR)
5. Set **Client Secret **shared by Sahamati
6. **Scope** as `openid`.
7. **Client Authentication** as `Send as Basic Auth Header`.

Decoding the Access Token

Using **jwt.io **

{% hint style="info" %}
Any popular JWT decoder tool available online can be used, please ensure that the tool is safe and secure. Compromised access tokens can allow unauthorized access.
{% endhint %}

Visit jwt.io and paste your access token to see the claims.

The decoded access token will have the following structure for Header and Payload:

#### Header

```
{
  "alg": "RS256",
  "typ": "JWT",
  "kid": "ZYeH2tvRkKKz6tXXEZ4GdZB8ykAW8sKZz2QyT-MoPEE"
}
```

#### Payload

```
{
 "exp": 1612886779,
 "iat": 1612850779,
 "jti": "bd9d1a78-3829-4c61-b52b-c8c925953916",
 "iss": "https://uattokens.sahamati.org.in/auth/realms/sahamati",
 "sub": "0ac207b8-676e-43ff-baa4-464d17f4608c",
 "typ": "Bearer",
 "azp": "AA00000000", // Same as ClientID
 "acr": "1",
 "scope": "openid email profile",
 "roles": "AA"
}
```

Refer [Access Token Schema](../reference/access-token-schema.md) for more details.