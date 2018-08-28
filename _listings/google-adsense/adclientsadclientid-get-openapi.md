---
swagger: "2.0"
x-collection-name: Google Adsense
x-complete: 0
info:
  title: Google Adsense API Get Ad Client
  version: 1.0.0
  description: Get information about one of the ad clients in the Host AdSense account.
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
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---