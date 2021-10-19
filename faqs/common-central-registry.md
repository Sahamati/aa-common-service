---
description: FAQs on the Common Central Registry
---

# Common Central Registry

### **What is the “Central Registry”?**

It is a directory listing of all participants in the AA ecosystem, namely AAs, FIPs**,** and FIUs.

### **What is this used for and by whom?**

For the AA ecosystem to be successful as a scalable, API-driven ecosystem, automated discovery of trusted API endpoints and additional metadata of each API provider is a must. Without this, interoperability at scale would be difficult to achieve.

The Central Registry is a common service that facilitates this automated discovery.

### What are the criteria to get listed in the Central Registry?

To be listed in the Central Registry, the entity (AA, FIP, or FIU) must be certified as having a standards-compliant API implementation in place.

The [Sahamati Certification Framework](https://app.gitbook.com/s/-MjQh9gCESKBasLLyTg3/) provides this guarantee.

On being awarded certification, the entity is listed in the Central Registry.

### What are the attributes that are made available through this registry?

The following attributes are the key public metadata attributes of each entity, listed in the central registry:

| Attribute              | Description                                                       |
| ---------------------- | ----------------------------------------------------------------- |
| Base URL               | The endpoint of the service that hosts the relevant AA APIs       |
| IP addresses and ports | The IP addresses and ports that communicate with the AA ecosystem |
| Public Key             | The public key of the entity                                      |

In addition to the above, specific metadata such as what is given below is also stored :&#x20;

1. The VUA suffix - relevant only for licensed AAs&#x20;
2. Types of identifiers used for discovery - relevant only for FIPs&#x20;
3. Type of financial information provided - relevant only for FIPs

### Who can provide information to the Central Registry and How?

In order to be listed in the Central Registry, an entity has to provide the above information to Sahamati through a secure, password-protected spreadsheet mechanism. No API access has been opened up for direct entry into the central registry, to exercise due diligence and control.

Information is put into the Central Registry for general availability only after the entity gets certified, as having a standard-compliant API implementation.

### Who can access the Central Registry and How?

AAs, FIPs, and FIUs that are listed in the Central Registry can access information about the other participants through an API provided by the Common Central Registry Service.

This means only those entities that are certified and have already provided their own information to the registry, are allowed access to other entities’ information.

### How is access controlled by the Central Registry?

The API provided by the Central Registry enforces authorization on the basis of an access token that the API client is expected to present.

Access Tokens are issued by the Common Token Issuance Server, to only certified entities.

All communication to and from this API is through HTTPS (using TLS 1.2).

### Are details of all entities available to all others?

No.

Role-based access control is implemented in the Central Registry API.

FIUs can access the registry details of AAs and FIPs, but not that of other FIUs. FIPs can access the registry details of AAs but not that of other FIPs or other FIUs. AAs can access the registry details of FIPs and FIUs but not that of other AAs.

These role-based restrictions are designed keeping in mind the design principles of the AA ecosystem.
