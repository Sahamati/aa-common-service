# Overview

This document provides an overview of a common AA ecosystem service that provides two features:

1. Central Registry of all participants&#x20;
2. an Access Token issued to each participant (a dynamic, short-lived Json Web Token) for it to access APIs provided by other API providers in the ecosystem

Specifically, this document describes what AA ecosystem members have to do, from an IT perspective, for integration with this common service.

It also provides a set of FAQs that describe the two features in greater detail.

The common service is currently hosted by Sahamati, the non-profit industry alliance of all AA ecosystem members, chartered by its members to define procedures and standards that help interoperability and scalability of the ecosystem.

## Context

The AA ecosystem depends on FIPs and FIUs being able to seamlessly connect to AAs and likewise, on AAs being able to seamlessly connect to either FIPs or FIUs.

Seamless connection is enabled through a set of standards and protocols that guarantee interoperability amongst connecting participants.

Each participant plays the role of being both an API provider and an API client, for the purpose of communicating with other participants.

In these roles, a prerequisite for participation is a certified implementation of the NBFC-AA API specifications published by ReBIT.

### API Clients

In addition, every API client needs the following information to be available in an automated, easy manner:

1. API endpoints of the API providers, to make API calls to&#x20;
2. An access token that it can present to the API providers, for them to authorize the calls&#x20;
3. Public Keys of the API providers, to verify the digitally signed responses from the providers

### API Providers

Every API provider needs the following information, to be available in an automated, easy manner:

1. API endpoints of the API clients, to send responses to&#x20;
2. Public Key of a common Token Issuance service, to validate the access token presented by an API client&#x20;
3. Public Keys of the API clients, to verify the digitally signed requests from the API clients

## Common Services for both

To facilitate easy, secure availability of the above information, the ecosystem uses a common “Central Registry and Token Issuance Server”.

The above needs of API providers and clients are mapped to the features of this common service as follows:

| Feature                                           |                      |
| ------------------------------------------------- | -------------------- |
| API endpoints of clients and providers            | Central Registry API |
| Public keys of clients and providers              | Central Registry API |
| Short-lived, dynamic access Token for each client | Token Service API    |



### Central Registry

The Central Registry feature provides information, through a secure API, about:&#x20;

1. API endpoints of every participant&#x20;
2. Public keys of every participant

The Central Registry Service API, similar to other APIs provided by participants, expects callers to present an access token. This token is validated by the Central Registry Service to authorize the call.

### Token Issuance

The Token Issuance feature provides a short-lived JSON Web Token (JWT) to each API client.

This JWT is digitally signed by Sahamati, as the issuer of the token. The digitally-signed token is inserted into API authorization headers by the API client, as its identity token, for every call made to any API provider in the ecosystem.

So, e.g. an FIU would use its digitally-signed JWT to connect to every AA resource server. The same JWT can also be used to connect to the Central Registry resource server.

Likewise, an AA would use its digitally-signed JWT to connect to every FIU resource server or every FIP resource server. The same JWT can also be used to connect to the Central Registry resource server.

JWTs are issued with a lifespan of 24 hours. Therefore, all API clients (FIPs, FIUs, AAs) are expected to refresh their tokens every 24 hours.
