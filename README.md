# BTAvfall
<i>BTAvfall</i> är en så kallad <i>bastjänst</i> (en tjänst för maskin-till-maskin-kommunikation med api:er) för NV:s avfallsregister.
Informationen om anslutningen och beskrivningen av api:er lämnas här på engelska.

## Introduction
<i>BTAvfall</i> is a public api rest-based service hosted by The Swedish Environmental Protection Agency targeting two audiences:
<ul><li>Waste operators, handlers, carriers, brokers and dealers</li>
<li>Supervisory authorities</li></ul>

## On-boarding
<ol>
  <li>Application on-line at The Swedish Environmental Protection Agency</li>
  <li>Approval of access to test environment</li>
  <li>Setting up mTLS (installing certificates)
  <li>Reviewing and testing compliance to the api.</li>
  <li>Approval of access to production environment</li>
</ol>
                                           
## Service style
REST

## Transport security
mTLS is used, you will need to have a client certificate from an approved authority.

## Autentication
OAuth2 Bearer is used, you will be provided with an access token with one year limitation.

## URL
* Production `https://api.naturvardsverket.se/btavfall/[api name]/v1/[resource name]...`
* Test `https://api-test.naturvardsverket.se/btavfall/[api name]/v1/[resource name]...`
* Sandbox not implemented

## Data exchange format
REST/JSON

## API's
### anteckning
This is the api for waste operators, handlers, carriers, brokers and dealers
to register waste notes. 

* Api name: anteckning
* Description [swagger-file](anteckning-v1-swagger.json).

### tillsyn
This is the api for Supervisory authorities to query registred waste notes. 

* Api name: tillsyn
* Description [swagger-file]().

