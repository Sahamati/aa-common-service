# Overview

Every entity interested in participating in the AA ecosystem (FIPs, FIUs, AAs) must be listed in the Central Registry, a common directory of all participants, provided as a common service by Sahamati to all ecosystem's participants.

The Central Registry contains public information provided by all participants, such as their public IP addresses and public keys, which other participants need to interact in an interoperable manner.

### Fetch of CR Information through an API

Central Registry service provides an API to all participants, to allow them to fetch the details of other AA ecosystem participants, subject to role-based access restrictions.

The role of each participant is as per the “roles” field in the identity token issued to the participant by Sahamati. A role could be one of three values - AA, FIP, FIU.

AAs are allowed to fetch details of FIPs and FIUs, but not that of other AAs. FIPs and FIUs are allowed to fetch details of all AAs, but not that of other FIPs or FIUs.

All participants are expected to use the API to retrieve information from the Central Registry. No other mechanism of getting information from the Central Registry will be allowed after v1.0 goes live.

AA ecosystem participants are expected to provide their CR information to Sahamati, through a password-protected mechanism already in place. Sahamati will review this information and make this available to other participants through the API detailed below.

Future versions of this service will allow API-driven updates to be made by participants directly.

### Security Considerations

The APIs offered by the Central Registry enforce:

1.  Source Authentication

    This is achieved through the use of short-lived identity tokens issued by Sahamati to each participant, which are then used to authorize API calls. The issuance of tokens is managed by Sahamati through the Central Token Service, details of which are found [here](broken-reference).
2. Data Encryption
   1. All data-at-rest is encrypted at the database level, using native encryption techniques offered by the database management system.
   2. Data-in-transit encryption is enforced through transmission over SSL using a strong security protocol of TLS 1.2 and above only. SSL Certificates are procured from a registered CA authority.
   3. Access controls, restricting access to the Central Registry, are also implemented.

