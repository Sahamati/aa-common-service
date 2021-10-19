---
description: Steps to perform for integrating with Common Service features
---

# Integrating Common Service

The following are the IT activities that have to be performed by AA ecosystem members:

1. Provide public API endpoints and public key information, for Central Registry hosted by Sahamati&#x20;
2. Configure Client ID & Secret values to get a dynamic, short-lived access token

## Provide public API endpoints and public key information

### For UAT environment

The authorized representative of the AA member organization, or a member of the Technology Service Provider that the AA member has contracted with, can send UAT API endpoints and public key information to `services (at) sahamati (dot) org (dot) in`.

### **For PRODUCTION environment**

Only authorized representatives of the AA member organization (and not the technology service providers) can send PRODUCTION API endpoints and public key information.

Such information has to be shared using a password-protected email mechanism with `services (at) sahamati (dot) org (dot) in`.

## **Configure Client ID, Client Secret values**

### **Fetch UAT Access Tokens**

For an AA member organization to connect to UAT environments of other participants, Sahamati will share the UAT Client ID and Secret with either an authorized representative of the organization or its technology service provider. This will be done through an email sent from `services (at) sahamati (dot) org (dot) in`.

### Fetch PRODUCTION Access Tokens

Once an AA member organization is certified to go live in the AA network, Sahamati will share the PRODUCTION Client ID and Secret with only the authorized representative of the member organization.

This will be done through an encrypted email, sent from `services (at) sahamati (dot) org (dot) in`.

Authorized representatives can then configure such information in their production systems, with the help of their technology service providers.



## Notes

1. Emails from Sahamati will also contain the URL for the Sahamati Public Key to be accessed. The same is to be used by AA member organizations, to fetch the Sahamati public key and configure in its systems, to validate tokens presented by API clients connecting to the member organization.
2. URL(s) to common service features will be shared along in the email if requested.
