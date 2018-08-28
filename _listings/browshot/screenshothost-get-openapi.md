---
swagger: "2.0"
x-collection-name: Browshot
x-complete: 0
info:
  title: Browshot Host thumbnails on your own S3 account or on Browshot.
  description: You can host screenshots and thumbnails on your own S3 account or on
    Browshot.
  termsOfService: https://browshot.com/terms
  contact:
    name: API Support
    url: https://browshot.com/contact
    email: support@browshot.com
  version: 1.17.0
host: api.browshot.com
basePath: /api/v1
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /screenshot/host:
    get:
      summary: Host thumbnails on your own S3 account or on Browshot.
      description: You can host screenshots and thumbnails on your own S3 account
        or on Browshot.
      operationId: HostScreenshot
      x-api-path-slug: screenshothost-get
      parameters:
      - in: query
        name: bucket
        description: S3 bucket to upload the screenshot or thumbnail - required with
          hosting=s3
      - in: query
        name: file
        description: file name to use - optional, used with hosting=s3
      - in: query
        name: headers
        description: HTTP headers to add to your S3 object - optional, used with hosting=s3
      - in: query
        name: height
        description: height of the thumbnail
      - in: query
        name: hosting
        description: 'hosting option: s3 or browshot'
      - in: query
        name: id
        description: screenshot ID
      - in: query
        name: scale
        description: scale of the thumbnail
      - in: query
        name: width
        description: width of the thumbnail
      responses:
        200:
          description: OK
      tags:
      - Screenshot
      - Host
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