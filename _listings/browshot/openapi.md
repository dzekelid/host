---
swagger: "2.0"
x-collection-name: Browshot
x-complete: 1
info:
  title: Browshot
  description: take-screenshots-of-any-website-in-real-time
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
---