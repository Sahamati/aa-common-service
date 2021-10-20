# CR API Details

The Central Registry API can be accessed using the following URL format:

> #### https://\<path-to-cr>.sahamati.org.in/entityInfo/**{Entity\_Type}**

The _`<path-to-cr>`_ varies for UAT/PROD environments and can be requested from Sahamati services.&#x20;

The Central Registry API can be used by the caller to fetch the details of all entities, subject to restrictions based on the role of the API caller (as per the role in the identity token).

API callers that present an identity `token.roles = AA` will be able to fetch details of all FIPs and FIUs (but not that of other AAs). If the request is for `Entity_type = AA`, they will get their own details only in the response.

API callers that present an identity `token.roles = FIU` will be able to fetch details of all AAs and all FIPs (but not that of other FIUs). If the request is for `Entity_type = FIU`, they will get their own details only in the response.

API callers that present an identity `token.roles = FIP` will be able to fetch details of all AAs (but not that of other FIPs or FIUs). If the request is for `Entity_type = FIP`, they will get their own details only in the response.

### Authentication Header

Every request to Central Registry API requires an authentication header present in the request.

| Header Name   | Description                                   |
| ------------- | --------------------------------------------- |
| Authorization | Access token with prefix `Bearer` is required |

### Request Type

`HTTP GET` method is expected for the Central Registry API.

#### Sample response:

```
{
    "ver": "1.0",
    "timestamp": "2020-06-01 09:09:32.0",
    "txnid": "29ae-11e8-a8d7-0210",
    "requester": {
        "name": "Bank Ltd.",
        "id": "fiu@bank"
    },
    "entityinfo": {
        "name": "Bank Ltd.",
        "id": "fiu@bank",
        "code": "BANKFIU",
        "entityhandle": "",
        "Identifiers": [
            {
                "category": "STRONG",
                "type": "MOBILE"
            }
        ],
        "baseurl": "https://fiu.bank.com/v1",
        "webviewurl": null,
        "fitypes": [
            ""
        ],
        "certificate": {
            "kty": "RSA",
            "e": "AQAB",
            "use": "sig",
            "kid": "sig-1634660208",
            "alg": "RS256",
            "n": "gn4pXGuRcuAzmqecSGEzThUXhIdy7ud2c4Pmdcl7YwhBrRfKSVPJ3sswX7pyRR_G5f_KkVILDGc8n1Fk6tmfguCC9NqdXR8js_83KOOakQgdar21pcJrpsko8nWe1PDSpihhKC6KbT1ihialRWwBkNPLtec3HDf5_pqbkqWnMwHpM19lFgavgmxCpVS2OmAx2f6Mcvz512AefgkxKKN5y6eaJc34bxZiacXrKjKnZGYMv0rl1JWkL9kajBr6ilUCsW8o1TBN3SimEawzvh1C4jApBCU94yqj8obM5-d3mwijJDUiHyDsutQBUXkM1f87fs6P5eBpvRAEZ7tw6qLzIQ"
        },
        "tokeninfo": {
            "desc": ""
        },
        "gsp": null,
        "signature": {
            "signValue": "pqYW98PLbK_PdiVGKPsqzmaIsLa7sa2aEanHa1uaLNafauUiC891"
        },
        "inboundports": null,
        "outboundports": null,
        "ips": null,
        "credentialsPk": null
    }
}
```

### Error Codes

| Code    | Description                          |
| ------- | ------------------------------------ |
| **200** | OK                                   |
| **400** | Bad Request                          |
| **401** | Unauthorized or Invalid Access Token |
| **403** | Forbidden                            |
| **404** | Not Found                            |
| **500** | Internal Server Error                |
