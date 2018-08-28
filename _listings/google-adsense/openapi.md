swagger: "2.0"
x-collection-name: Google Adsense
x-complete: 1
info:
  title: Google Adsense Merged API
  version: 1.0.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /adclients/{adClientId}:
    get:
      summary: Get Ad Client
      description: Get information about one of the ad clients in the Host AdSense
        account.
      operationId: adsensehost.adclients.get
      x-api-path-slug: adclientsadclientid-get
      parameters:
      - in: path
        name: adClientId
        description: Ad client to get
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Clients