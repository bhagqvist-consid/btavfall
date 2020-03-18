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

## Data exchange format
JSON

## Transport security
mTLS is used, you will need to have a client certificate from an approved authority.

## Autentication
OAuth2 Bearer is used, you will be provided with an access token with one year limitation.

## URL
* Production `https://api.naturvardsverket.se/btavfall/[api name]/v1/[resource name]...`
* Test `https://api-test.naturvardsverket.se/btavfall/[api name]/v1/[resource name]...`
* Sandbox not implemented

## Language
Most data fields have Swedish naming.

## Request headers
`NV-Client-System-ID` (mandatory) should contain the name and version of the connecting system.

`NV-Client-Tracking-ID` (optional) is always returned in the response and can be used for tracking the request with an id of your choosing. If it is left unset a random UUID is provided in the response.

## API's
### Submission of waste notes
This is the api for waste operators, handlers, carriers, brokers and dealers
for submission of regulatory waste notes. 

* Api name: anteckning
* Description [swagger-file](anteckning-v1-swagger.json).
* Status: In development

Example GET
```
GET https://api-test.naturvardsverket.se/btavfall/anteckning/v1/avfallstyper
Authorization : Bearer xxXx0x0x0x0xxXXX000xx . . .
NV-Client-System-ID : My-system-version-1.1
NV-Client-Tracking-ID: 3.1415297
```

Example POST
```
POST https://api-test.naturvardsverket.se/btavfall/anteckning/v1/behandlingsmottaganden
Content-Length: 342
Content-Type: application/json; charset=UTF-8
Authorization: Bearer xxXx0x0x0x0xxXXX000xx . . .
NV-Client-System-ID: My-system-version-1.1
NV-Client-Tracking-ID: 3.1415927 

{
  "tidpunktForAnteckningen": "2019-11-25T10:07:19",
  "datumForAvfalletsMottagande": "2019-11-25",
  "ombud": "1212121212",
  "verksamhetsutovare": "2021001975",
  "referens": "876182763",
  "avfall": {
    "kod": "010305",
    "mangd": 1000.00,
    "foreganendeavfallid": "0d2e3ec4-c84a-40fc-8711-a00b5cd4c6cd"
  },
  "tidigareInnehavare": "2021001975"
}
```

#### Response
For all the POST's and PUT's the response body contains the field `AvfallsID` which is the _waste record id_ of the created or updated record. This value should be used when register succeeding events if possible, thereby chaining together events to enable better tracking of the handling of each waste 'thing'.

Example
```
HTTP/1.1 201 Created
Date: 2020-09-04 18:34:04
Connection: Keep-Alive
Content-Type: application/json; charset=UTF-8
Content-Length: 63
NV-Client-Tracking-ID: 3.1415927 

{
    "AvfallsId": "072f294c-9e70-4cf6-b6a3-139922067ddc"
}
```

### Review of waste notes
This is the api for Supervisory authorities to query registred waste notes. 

* Api name: tillsyn
* Description [swagger-file](tillsyn-v1-swagger.json).
* Status: In development

