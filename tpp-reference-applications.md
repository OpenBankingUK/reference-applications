# TPP Reference Applications

## Summary

There are 2 core user needs:

* As an ASPSP I want to test my endpoints (without exposing them to live applications) so that I can ensure that they work.
* As a TPP (AISP or PISP) I want example code so that I can build my application(s) more quickly.

Initially this application is limited to the use case for an Account Information Service Provider (AISP).

## Health warning relating to support

This release is an early preview of the TPP Reference Application so that developers can download and try out the code. Eventually the intention is to publish this application together with detailed documentation in public GitHub repositories, and to provide support for enrolled developers. In this version documentation is limited and OBIE cannot provide any support for this version of the application, however we will do our best to respond to any comments raised below.

## AISP application

This application uses the architecture below to simulate an AISP - a third party (TPP) application that can aggregate account balances for their customer.

Our AISP creates a unified viewed of the account balances on the frontend while using Open Banking APIs to query for the data.

This is based on a classic architecture of Frontend, Backend, and (Mock) Server:

```
------------       -----------        -------------
- Frontend - <---> - Backend -  <---> - Mock APIs -
------------       -----------        -------------
                    |      |
                    /      \
            ===========  ===========
            = Session =  =  Data   =
            =  Store  =  =  Cache  =
            ===========  ===========
```

### Frontend

This is a Single Page Application written in [Vue.js](http://vuejs.org/).

It showcases workflows visible to an end user. Typically, the end user gives access to a third party (TPP) application to aggregate data on their behalf.

Setup and detailed info here, https://github.com/OpenBankingUK/tpp-reference-client

### Backend

This is a [Node.js](http://nodejs.org/) server that manages and brokers interactions with the Open Banking APIs (Read/Write ASPSP & OB Directory).

Typically, these include the necessary consent and security flows.

__Note__: This component can be used directly without the frontend to trial the Open Banking APIs. (WIN)

Setup and detailed info here: https://github.com/OpenBankingUK/tpp-reference-server

### Mock APIs

This is a [Node.js](http://nodejs.org/) server that simulates Open Banking APIs.

We simulate the Read ASPSP APIs using [a published Swagger spec](https://www.openbanking.org.uk/read-write-apis/account-transaction-api/v1-1-0/#swagger). And, we also simulate Open Banking Directory APIs for third parties who are __NOT__ yet provisioned.

Setup and detailed info here: https://github.com/OpenBankingUK/reference-mock-server

## Release plan (for AISP application)

| Release | Sprint | Date   | Functionality |
| ------- | ------ | ------ | --- |
| 0.1.0   | 17     | 10 Oct | Login to TPP app and select ASPSP from list, request accounts & balance data, view account balances |
| 0.2.0   | 18     | 24 Oct | Gets ASPSP list from test OB Directory, setup account request |
| 0.3.0   | 19     | 07 Nov | Authorise consent |
| 0.4.0   | 20     | 21 Nov | List ASPSPs TPP has registered with, call ref ASPSP authorisation server, data from Reference ASPSP |
