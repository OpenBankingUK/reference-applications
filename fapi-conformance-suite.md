# FAPI Conformance Suite

Tools which allow an ASPSP to run tests to check conformance to the OIDC FAPI security profile.

## Background

The Open ID Foundation (OIDF) profiles are a robust set of security standards for the safe provision of Financial APIs (FAPIs) that offer the highest level of protection for all participants; in particular end users. One of the main benefits of using the OIDF security standards is that the OIDF facilitates individual organisations to attest to OpenID standards through a self-certification process using an OIDF supplied and maintained suite of tests. The log files generated during self-certification are made available for peer review using an open and transparent approach.

The OBIE will leverage, with the consent of the OIDF and under the existing licensing arrangements, the existing code and attestation approach adopted by the OIDF by enhancing the existing code to meet the needs of the OB programme. The enhanced code will then be released unencumbered by any intellectual property claims to the OIDF thus creating a common global standard for use by PSPs. In terms of the OB, this enhanced code and test approach is called the 'Conformance Harness'.

## User needs

As an ASPSP I want to test my implementation of the OIDC FAPI security profile so I can assure it meets the required standard.

## Key features

* To allow an ASPSP to self certify their implementation is compatible with the security profile. 
* 60+ tests (standard FAPI plus OB specific), see below.
* Gives a pass fail flag on each test.
* Hosted web service, initially by OBIE and will migrate to OIDF.
* Hosting and maintenance of the live service will then be managed by OIDF.
* The service will be branded OpenID Foundation.
* Will store logs and allow users to publish logs so others can see their results (as a proof point).
* OIDF may charge for this publishing and peer review service.
* May be an option for ASPSPs to download themselves and use internally TBC.
* This is not a mandatory service for ASPSPs at this stage.
* There will not be a formal SLA for the running of the conformance suite of tests and no liability for use of the certification test harness will be carried by OBIE.

## Benefits

The key benefits of developing this suite in a timescale that matches the aggressive timelines are: 

* ASPSPs will be able to demonstrate conformance with the OB security profile ahead of the planned compliance date in January 2018.
* The availability of a common global conformance capability will drive standardisation across the OB community.
* TPPs will be able to demonstrate conformance to the security profiles without significant additional investment and the consequent delay.

Detailed list of tests (draft)

[AS] Support the code/idtoken flow
[AS] Support the code/idtoken/token flow
[AS] Request object sent with parameters inside
[AS] Request object signed with client secret/key
[AS] Enforce Client authenticates with mTLS
[AS] Enforce Client authenticates with symmetric key JWT
[AS] Enforce Client authenticates with asymmetric key JWT
[AS] Enforce Client key is appropriate size for RSA
[AS] Enforce Client key is appropriate size for EC
[AS] Enforce Client secrets meet minimum entropy
[AS] Enforce Client can only use pre-registered redirect URI
[AS] Enforce Client can use PKCE/S256
[AS] Enforce Client can’t use PKCE/none
[AS] Enforce Client sends redirect_uri parameter
[AS] Enforce Client can’t re-use authorization code
[AS] Token responses conform to OAuth
[AS] Token responses contain scope list
[AS] Tokens are of sufficient length and entropy
[AS] ID token is well-formatted and includes subject when openid scope is sent
[AS] ID token always sent with appropriate requests
[AS] ID token contains s_hash
[AS] issues MTLS access tokens
[AS] Can issue encrypted ID tokens
[C] AS allows authentication with MTLS
[C] AS allows authentication with symmetric key JWT
[C] AS allows authentication with asymmetric key JWT
[C] Ensure key and secret sizes
[C] Uses TLS 1.2
[C] Sends the token in Authorization: Bearer header
[C] Sends the FAPI financial id header
[C] Sends the FAPI auth date header
[C] Sends the FAPI IP address header
[C] Sends the FAPI interaction ID header
[C] Accepts and sends MTLS access tokens
[C] Sends the request object
[C] Signs the request object
[C] Verifies the ID token signature and content
[C] Can accept encrypted ID tokens
[C] Have client talk to two AS test instances and make sure client uses different redirect URI with each
[RS] Uses TLS 1.2 (this might be a separate socket-only test?)
[RS] Supports HTTP GET (This requirement doesn’t make sense, what about POST-only API calls or other verbs?)
[RS] Supports Authorization: Bearer header
[RS] Rejects access_token= query parameter
[RS]* Verify the access token is not expired or revoked
[RS]*+ Verify the scope matches
[RS]* Identify the entity represented by the token
[RS]*+ Response is tied to entity and scope
[RS]+ Encode response in UTF8
[RS]+ Sends the Content-type header as JSON
[RS] Sends the Date header
[RS] Accepts the FAPI interaction ID header in request
[RS] Sends the FAPI interaction id header in response
[RS] accepts MTLS access tokens

The RS tests marked with * would require a connection to the test AS, or some other way to make that work. Since FAPI doesn’t mandate any particular connection to the AS/RS, we might not be able to pull these off into separate systems. FAPI does allow introspection, but its support isn’t mandated or profiled, and therefore many providers might just do their own thing at their RS. RS tests marked with + would need to have a specific test API defined that could be called by our client. There are a few additional tests that would need screenshot submission (making sure you do LOA2 auth, allowing revocation in the UI, you log the FAPI ID header, etc) and I’ve left those off here.
