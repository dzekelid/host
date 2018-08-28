swagger: "2.0"
x-collection-name: New Relic
x-complete: 1
info:
  title: New Relic
  version: 1.0.0
basePath: v2/
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /applications/{application_id}/hosts/{host_id}/metrics.{format}:
    get:
      summary: Get Applications Application  Hosts Host  Metrics. Format
      description: |-
        Return a list of known metrics and their value names for the given resource.

        See our documentation for a discussion
        on  output pagination
        and for examples of requesting and using metric values.
      operationId: getApplicationsApplicationHostsHostMetrics.Format
      x-api-path-slug: applicationsapplication-idhostshost-idmetrics-format-get
      parameters:
      - in: path
        name: application_id
        description: Application ID
        type: integer
      - in: query
        name: cursor
        description: Cursor for next page (replacing page param)
        type: string
      - in: path
        name: host_id
        description: Application Host ID
        type: integer
      - in: query
        name: name
        description: Filter metrics by name
        type: string
      - in: query
        name: page
        description: Pagination index (will be deprecated)
        type: integer
      responses:
        200:
          description: OK
      tags:
      - Applications
      - Application
      - ""
      - Hosts
      - Host
      - ""
      - Metrics.
      - Format
  /applications/{application_id}/hosts/{host_id}/metrics/data.{format}:
    get:
      summary: Get Applications Application  Hosts Host  Metrics Data. Format
      description: "This API endpoint returns a list of values for each of the requested
        metrics. The list of available metrics\ncan be returned using the Metric Name
        API endpoint.\n\nMetric data can be filtered by a number of parameters, including
        multiple names and values, and by time range.\nMetric names and values will
        be matched intelligently in the background.\n\nYou can also retrieve a summarized
        data point across the entire time range selected by using the summarize\nparameter.\n\nSee
        our documentation for a discussion on \noutput pagination,  time range \nrelated
        considerations, and for examples of requesting and using metric values."
      operationId: getApplicationsApplicationHostsHostMetricsData.Format
      x-api-path-slug: applicationsapplication-idhostshost-idmetricsdata-format-get
      parameters:
      - in: path
        name: application_id
        description: Application ID
        type: integer
      - in: query
        name: from
        description: Retrieve metrics after this time
        type: time
      - in: path
        name: host_id
        description: Application Host ID
        type: integer
      - in: query
        name: names
        description: Retrieve specific metrics by name
        type: array
      - in: query
        name: period
        description: Period of timeslices in seconds
        type: integer
      - in: query
        name: raw
        description: Return unformatted raw values
        type: boolean
      - in: query
        name: summarize
        description: Summarize the data
        type: boolean
      - in: query
        name: to
        description: Retrieve metrics before this time
        type: time
      - in: query
        name: values
        description: Retrieve specific metric values
        type: array
      responses:
        200:
          description: OK
      tags:
      - Applications
      - Application
      - ""
      - Hosts
      - Host
      - ""
      - Metrics
      - Data.
      - Format
  /applications/{application_id}/hosts.{format}:
    get:
      summary: Get Applications Application  Hosts. Format
      description: "This API endpoint returns a \npaginated list of hosts associated
        with the given application. The time range for summary data is the last 10
        minutes.\n\nApplication hosts can be filtered by hostname, or the list of
        application host IDs.\n\nSee our documentation for a discussion and examples
        of\nusing  filters \nand summary data output."
      operationId: getApplicationsApplicationHosts.Format
      x-api-path-slug: applicationsapplication-idhosts-format-get
      parameters:
      - in: path
        name: application_id
        description: Application ID
        type: integer
      - in: query
        name: filter[hostname]
        description: Filter by server hostname
        type: string
      - in: query
        name: filter[ids]
        description: Filter by application host ids
        type: list
      - in: query
        name: page
        description: Pagination index
        type: integer
      responses:
        200:
          description: OK
      tags:
      - Applications
      - Application
      - ""
      - Hosts.
      - Format
  /applications/{application_id}/hosts/{id}.{format}:
    get:
      summary: Get Applications Application  Hosts  . Format
      description: |-
        This API endpoint returns a single application host, identified by ID. The time range for summary data is the last 10 minutes.

        See our documentation for a discussion of
        summary data output.
      operationId: getApplicationsApplicationHosts.Format
      x-api-path-slug: applicationsapplication-idhostsid-format-get
      parameters:
      - in: path
        name: application_id
        description: Application ID
        type: integer
      - in: path
        name: id
        description: Application host ID
        type: integer
      responses:
        200:
          description: OK
      tags:
      - Applications
      - Application
      - ""
      - Hosts
      - ""
      - .
      - Format