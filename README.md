# BTAvfall
<i>BTAvfall</i> är en så kallad <i>bastjänst</i>, en tjänst med api:er, för NV:s avfallsregister.
Informationen om anslutningen och beskrivningen av api:er lämnas här på engelska.

## Introduction
<i>BTAvfall</i> is a public service hosted by The Swedish Environmental Protection Agency targeting two audiences:
<ul><li>Waste operators, handlers, carriers, brokers and dealers</li>
<li>Supervisory authorities</li></ul>

## On-boarding
<ol>
  <li>Application on-line at The Swedish Environmental Protection Agency</li>
  <li>Granted access to test nvironment</li>
  <li>Review, test and approvement</li>
  <li>Granted access to production environment</li>
</ol>
                                           
## Service style
REST

## Transport security
mTLS is used, you will need to have a client certificate from an approved authority.

## Autentication
OAuth2 Bearer is used, you will be provided with an access token with one year limitation.

## URL
<p>Production https://api.naturvardsverket.se/btavfall/<api>/v1/<resource>...
<p>Test https://api-test.naturvardsverket.se/btavfall/<api>/v1/<resource>...
<p>Sandbox not implemented

## Data exchange format
REST/JSON


