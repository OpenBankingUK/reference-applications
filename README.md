# Reference Applications

Suite of reference applications to facilitate development and testing relating to Open Banking APIs.

## Summary

The Open Banking Implementation Entity (OBIE) is building a suite of reference applications for the Open Banking ecosystem. 

Whilst there is no specified requirement for OBIE to actively test or validate the implementations of ASPSPs or TPPs, OBIE is taking steps to help users do their own testing.

There are 3 high level user needs:

* As OBIE I want to ensure that the overall OB ecosystem works technically so that I can identify and fix issues early and proactively (without being totally dependent on others finding them for me).
* As a participant (ASPSP or TPP) I want tools and examples to help me build and test so that I can save time and deliver quality products.
* As OBIE I want to provide these tools for participants (ASPSPs and TPPs) so that I can accelerate adoption and to meet the objectives of the CMA remedies.

## Caveats

The API specifications and the test instance of the OB directory are critical path dependencies for ASPSPs and TPPs to enable development and testing prior to go live.

However, these Reference Applications should not be considered as a critical path dependency for either ASPSPs nor TPPs, but rather they are provided to help facilitate testing and speed up adoption.

Because the standards will evolve over time and because participant adoption is expected to grow over time, all of these are ongoing requirements - i.e. these needs will not go away after Jan 2018. 

## List of applications

| Application | Key Features | Availability |
| --- | --- | --- | 
| FAPI Conformance Suite | Online tool which allows an ASPSP to test their implementation against the OB security profile. Produces a conformance report which can be shared/posted to a central space to share proof of conformance. | Due early Dec |
| JSON Data Validation Tool | Online tool which allows an ASPSP to test the response/output of any API endpoint to validate that the JSON and data formats meet the schema. | Due early Nov |
| Reference ASPSP Implementations | Hosted 'model banks' for real (or ficitious) ASPSPs with stubbed/dynamic data behind each of the functional API endpoints. | Available to enrolled participants via the OB Directory |
| TPP Onboarding Application | Downloadable tool which a TPP can install (on their infra) and which allows creation of an SSA and (via a number of steps) get client credentials for s/w statement for one or more ASPSPs (as long as they support auto registration). Allows TPP to confirm that credentials work via a test page which allows a PSU to connect to ASPSP end point(s) to authenticate and get an access token for a specific user to get list of accounts. | Due early Nov |
| TPP Reference Applications | Downloadable web applications which simulate TPP applications for each of the AISP and PISP use cases. | See https://github.com/OpenBankingUK/reference-applications/blob/master/tpp-reference-applications.md |
