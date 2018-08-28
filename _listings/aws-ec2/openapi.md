swagger: "2.0"
x-collection-name: AWS EC2
x-complete: 1
info:
  title: AWS EC2 API
  version: 1.0.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /?Action=AllocateHosts:
    get:
      summary: Allocate Hosts
      description: Allocates a Dedicated Host to your account.
      operationId: allocatehosts
      x-api-path-slug: actionallocatehosts-get
      parameters:
      - in: query
        name: Filter.N
        description: One or more filters
        type: string
      - in: query
        name: HostId.N
        description: The IDs of the Dedicated Hosts
        type: string
      - in: query
        name: MaxResults
        description: The maximum number of results to return for the request in a
          single page
        type: string
      - in: query
        name: NextToken
        description: The token to retrieve the next page of results
        type: string
      responses:
        200:
          description: OK
      tags:
      - Host
  /?Action=DescribeHostReservationOfferings:
    get:
      summary: Describe Host Reservation Offerings
      description: Describes the Dedicated Host Reservations that are available to
        purchase.
      operationId: describehostreservationofferings
      x-api-path-slug: actiondescribehostreservationofferings-get
      parameters:
      - in: query
        name: Filter.N
        description: One or more filters
        type: string
      - in: query
        name: HostReservationIdSet.N
        description: One or more host reservation IDs
        type: string
      - in: query
        name: MaxResults
        description: The maximum number of results to return for the request in a
          single page
        type: string
      - in: query
        name: NextToken
        description: The token to use to retrieve the next page of results
        type: string
      responses:
        200:
          description: OK
      tags:
      - Host Reservation
  /?Action=DescribeHostReservations:
    get:
      summary: Describe Host Reservations
      description: |-
        Describes Dedicated Host Reservations which are associated with Dedicated Hosts in
                    your account.
      operationId: describehostreservations
      x-api-path-slug: actiondescribehostreservations-get
      parameters:
      - in: query
        name: HostIdSet.N
        description: The ID/s of the Dedicated Host/s that the reservation will be
          associated            with
        type: string
      - in: query
        name: OfferingId
        description: The offering ID of the reservation
        type: string
      responses:
        200:
          description: OK
      tags:
      - Host Reservation
  /?Action=DescribeHosts:
    get:
      summary: Describe Hosts
      description: Describes one or more of your Dedicated Hosts.
      operationId: describehosts
      x-api-path-slug: actiondescribehosts-get
      parameters:
      - in: query
        name: Filter.N
        description: One or more filters
        type: string
      - in: query
        name: MaxDuration
        description: This is the maximum duration of the reservation youd like to
          purchase, specified            in seconds
        type: string
      - in: query
        name: MaxResults
        description: The maximum number of results to return for the request in a
          single page
        type: string
      - in: query
        name: MinDuration
        description: This is the minimum duration of the reservation youd like to
          purchase, specified            in seconds
        type: string
      - in: query
        name: NextToken
        description: The token to use to retrieve the next page of results
        type: string
      - in: query
        name: OfferingId
        description: The ID of the reservation offering
        type: string
      responses:
        200:
          description: OK
      tags:
      - Hosts
  /?Action=GetHostReservationPurchasePreview:
    get:
      summary: Get Host Reservation Purchase Preview
      description: |-
        Preview a reservation purchase with configurations that match those of your
                    Dedicated Host.
      operationId: gethostreservationpurchasepreview
      x-api-path-slug: actiongethostreservationpurchasepreview-get
      parameters:
      - in: query
        name: AutoPlacement
        description: Specify whether to enable or disable auto-placement
        type: string
      - in: query
        name: HostId.N
        description: The host IDs of the Dedicated Hosts you want to modify
        type: string
      responses:
        200:
          description: OK
      tags:
      - Host Reservation
  /?Action=ModifyHosts:
    get:
      summary: Modify Hosts
      description: Modify the auto-placement setting of a Dedicated Host.
      operationId: modifyhosts
      x-api-path-slug: actionmodifyhosts-get
      parameters:
      - in: query
        name: Affinity
        description: The new affinity setting for the instance
        type: string
      - in: query
        name: HostId
        description: The ID of the Dedicated Host that the instance will have affinity
          with
        type: string
      - in: query
        name: InstanceId
        description: The ID of the instance that you are modifying
        type: string
      - in: query
        name: Tenancy
        description: The tenancy of the instance that you are modifying
        type: string
      responses:
        200:
          description: OK
      tags:
      - Hosts
  /?Action=PurchaseHostReservation:
    get:
      summary: Purchase Host Reservation
      description: Purchase a reservation with configurations that match those of
        your Dedicated Host.
      operationId: purchasehostreservation
      x-api-path-slug: actionpurchasehostreservation-get
      parameters:
      - in: query
        name: HostId.N
        description: The IDs of the Dedicated Hosts you want to release
        type: string
      responses:
        200:
          description: OK
      tags:
      - Host Reservation
  /?Action=ReleaseHosts:
    get:
      summary: Release Hosts
      description: When you no longer want to use an On-Demand Dedicated Host it can
        be released.
      operationId: releasehosts
      x-api-path-slug: actionreleasehosts-get
      parameters:
      - in: query
        name: DhcpOptionsId
        description: The ID of the DHCP options set, or default to associate         no
          DHCP options with the VPC
        type: string
      - in: query
        name: DryRun
        description: Checks whether you have the required permissions for the action,
          without actually making the request,        and provides an error response
        type: string
      - in: query
        name: VpcId
        description: The ID of the VPC
        type: string
      responses:
        200:
          description: OK
      tags:
      - Hosts