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

## Language
Most data fields have Swedish naming.

## Request headers
`NV-Client-System-ID` (mandatory) should contain the name and version of the connecting system.

`NV-Client-Tracking-ID` (optional) is always returned in the response and can be used for tracking the request with an id of your choosing. If it is left unset a random UUID is provided in the response.

## API's
### anteckning
This is the api for waste operators, handlers, carriers, brokers and dealers
to register the regulatory waste notes. 

* Api name: anteckning
* Description [swagger-file](anteckning-v1-swagger.json).

#### Response
For all the POST's and PUT's the response body contains the field `AvfallsID` which is the _waste record id_ of the created or updated record. This value should be used when register succeeding events if possible, thereby chaining together events to enable better tracking of the handling of each waste 'thing'.

### tillsyn
This is the api for Supervisory authorities to query registred waste notes. 

* Api name: tillsyn
* Description [swagger-file]().

