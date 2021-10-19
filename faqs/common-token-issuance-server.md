---
description: FAQs on the Common Token Issuance Server
---

# Common Token Issuance Server

### What is a “Token”, in the context of the AA ecosystem?

As per the ReBIT NBFC-AA specification, each API provider is expected to authorize an API caller on the basis of an API token presented by the API caller. This is also referred to as the “API Key” in the specification and is expected to be passed in the API header.

### Who is supposed to issue this key to whom?

Since all communication is bilateral between AAs and FIPs or FIUs, API tokens are expected to be obtained by AAs, while calling FIP/FIU APIs. Similarly, API tokens are expected to be obtained by FIPs/FIUs while calling AA APIs.

One way for API clients to obtain these tokens is to get them directly from the API resource servers. However, for an ecosystem containing a large number of FIPs, FIUs, and AAs, this would prove to be unmanageable at scale. Each party would have to issue tokens bilaterally to each other, which would impede the principle of easy, real-time discoverability of AAs, FIPs, and FIUs of each other.

Instead, the ecosystem relies on a common Token Issuance server to issue API tokens. This common token server issues bearer tokens to API clients in the AA ecosystem.

### Why is it better to have a common token issuance server?

The benefits of having a common server are:&#x20;

1. Scale - Individual parties need not manage the bilateral issuance of tokens. That would impede the scalability of the ecosystem.&#x20;
2. Security standards - by having a common authorization server, important aspects of security such as Token Format, Token Lifespan, and other claims used for seeking authorization are standardized in the AA ecosystem. This will ensure that the same security standards, for authentication and authorization of API clients, are followed uniformly in the AA ecosystem.

### Are the Tokens Digitally Signed by the common Token Issuance Server?

Yes.

Each access token issued by the common server is digitally signed by the server, using its digital certificate.

### Is authorization also performed by the common server?

No. Authorization is supposed to be performed by each API resource server, on its own.

The role of the common server is ONLY to issue short-lived bearer tokens, to each API client.

Each API resource server validates whether the issuer of the token is the common ecosystem server (managed by Sahamati) and whether the owner of the token is indeed the API client. It further checks if the token has expired or is still active, as per its lifespan attribute.

Beyond this, API resource servers are free to add additional authorization rules, to control access to their resources.

The common token issuance server has NO role to play in the actual authorization process.

### On what basis does the common server issue a token?

Only those entities (FIPs, FIUs, and AAs) that are listed in the ecosystem’s Central Registry get an access token.

To be listed in the Central Registry, each entity must have undergone certification to prove that it has a standards-compliant implementation of the NBFC-AA APIs, whether it is an AA, a FIP, or an FIU.

Once an entity is listed in the Central Registry, it is issued a client ID and Secret as its credentials.

The actual 24-hour access token is granted when these credentials are passed through a secure HTTPS API call, by the API client to the common token issuance server.

### What is the lifespan of each token issued?

Each token issued has a lifespan of only 24 hours. Tokens have to be procured every 24 hours by each API client.

What are the other attributes of the token issued?

The token is issued in JSON Web Token format. See reference [Access Token Schema](../reference/access-token-schema.md).
