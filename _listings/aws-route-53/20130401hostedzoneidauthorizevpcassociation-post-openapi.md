---
swagger: "2.0"
x-collection-name: AWS Route 53
x-complete: 0
info:
  title: AWS Route 53 API Create V P C Association Authorization
  version: 1.0.0
  description: Authorizes the AWS account that created a specified VPC to submit an
    AssociateVPCWithHostedZone request to associate the VPC with a specified hosted
    zone that was created by a different account. To submit a CreateVPCAssociationAuthorization
    request, you must use the account that created the hosted zone. After you authorize
    the association, use the account that created the VPC to submit an AssociateVPCWithHostedZone
    request.NoteIf you want to associate multiple VPCs that you created by using one
    account with a hosted zone that you created by using a different account, you
    must submit one authorization request for each VPC.Send a POST request to the
    /2013-04-01/hostedzone/hosted zone ID/authorizevpcassociation resource. The request
    body must include a document with a CreateVPCAssociationAuthorizationRequest element.
    The response contains information about the authorization.
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /2013-04-01/hostedzone:
    post:
      summary: Create Hosted Zone
      description: Creates a new public hosted zone, used to specify how the Domain
        Name System (DNS)routes traffic on the Internet for a domain, such as example.com,
        and its subdomains. ImportantPublic hosted zones can't be converted to a private
        hosted zone or vice versa.Instead, create a new hosted zone with the same
        name and create new resource recordsets.Send a POST request to the /2013-04-01/hostedzone
        resource. The request body must include a documentwith a CreateHostedZoneRequest
        element. The response returns theCreateHostedZoneResponse element containing
        metadata about the hostedzone.Fore more information about charges for hosted
        zones, see Amazon Route 53 Pricing.Note the following:You can't create a hosted
        zone for a top-level domain (TLD).Amazon Route 53 automatically creates a
        default SOA record and four NS records for the zone.For more information about
        SOA and NS records, see NS and SOA Records that Amazon Route 53 Creates for
        a Hosted Zone in the Amazon Route 53 Developer Guide.If your domain is registered
        with a registrar other than Amazon Route 53, you must update thename servers
        with your registrar to make Amazon Route 53 your DNS service. For more information,
        seeConfiguring Amazon Route 53 as your DNSService in the Amazon Route 53 Developer's
        Guide.After creating a zone, its initial status is PENDING. This means that
        itis not yet available on all DNS servers. The status of the zone changes
        to INSYNCwhen the NS and SOA records are available on all Amazon Route 53
        DNS servers. When trying to create a hosted zone using a reusable delegation
        set, specify anoptional DelegationSetId, and Amazon Route 53 would assign
        those 4 NS records for the zone, instead ofallotting a new one.
      operationId: createhostedzone
      x-api-path-slug: 20130401hostedzone-post
      parameters:
      - in: body
        name: CallerReference
        description: A unique string that identifies the request and that allows failedCreateHostedZone
          requests to be retried without the risk of executing theoperation twice
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: CreateHostedZoneRequest
        description: Root level tag for the CreateHostedZoneRequest parameters
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: Default
        description: None
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: DelegationSetId
        description: If you want to associate a reusable delegation set with this
          hosted zone, the ID thatAmazon Route 53 assigned to the reusable delegation
          set when you created it
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: HostedZoneConfig
        description: (Optional) A complex type that contains an optional comment about
          your hosted zone
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: Name
        description: The name of the domain
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: Parent
        description: CreatedHostedZoneRequest
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: VPC
        description: The VPC that you want your hosted zone to be associated with
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Hosted Zones
  /2013-04-01/hostedzone&amp;delegationsetid=DelegationSetId?marker=Marker&amp;maxitems=MaxItems:
    get:
      summary: List Hosted Zones
      description: 'To retrieve a list of your public and private hosted zones, send
        a GETrequest to the /2013-04-01/hostedzone resource. The response to this
        requestincludes a HostedZones child element for each hosted zone created by
        the currentAWS account.Amazon Route 53 returns a maximum of 100 items in each
        response. If you have a lot of hostedzones, you can use the maxitems parameter
        to list them in groups of up to 100.The response includes four values that
        help navigate from one group of maxitemshosted zones to the next:                  MaxItems
        is the value specified for the maxitems parameterin the request that produced
        the current response.If the value of IsTruncated in the response is true,
        there are morehosted zones associated with the current AWS account.                   NextMarker
        is the hosted zone ID of the next hosted zone that isassociated with the current
        AWS account. If you want to list more hosted zones, makeanother call to ListHostedZones,
        and specify the value of theNextMarker element in the marker parameter. If
        IsTruncated is false, the NextMarker element isomitted from the response.If
        you''re making the second or subsequent call to ListHostedZones, theMarker
        element matches the value that you specified in themarker parameter in the
        previous request.'
      operationId: listhostedzones
      x-api-path-slug: 20130401hostedzoneampdelegationsetiddelegationsetidmarkermarkerampmaxitemsmaxitems-get
      parameters:
      - in: path
        name: delegationsetid
        description: If youre using reusable delegation sets and you want to list
          all of the hosted zones that are associated with a reusable delegation set,
          specify the ID of that reusable delegation set
        type: string
      responses:
        200:
          description: OK
      tags:
      - Hosted Zones
  /2013-04-01/hostedzone/Id:
    delete:
      summary: Delete Hosted Zone
      description: Deletes a hosted zone. Send a DELETE request to the /Amazon Route
        53API version/hostedzone/hosted zone ID             resource.ImportantDelete
        a hosted zone only if there are no resource record sets other than the defaultSOA
        record and NS resource record sets. If the hosted zone contains other resource
        recordsets, delete them before deleting the hosted zone. If you try to delete
        a hosted zone thatcontains other resource record sets, Amazon Route 53 denies
        your request with aHostedZoneNotEmpty error. For information about deleting
        records from yourhosted zone, see ChangeResourceRecordSets.
      operationId: deletehostedzone
      x-api-path-slug: 20130401hostedzoneid-delete
      parameters:
      - in: path
        name: Id
        description: The ID of the hosted zone you want to delete
        type: string
      responses:
        200:
          description: OK
      tags:
      - Hosted Zones
    get:
      summary: Get Hosted Zone
      description: Retrieves the delegation set for a hosted zone, including the four
        name serversassigned to the hosted zone. Send a GET request to the /Amazon
        Route 53 APIversion/hostedzone/hosted zone ID             resource.
      operationId: gethostedzone
      x-api-path-slug: 20130401hostedzoneid-get
      parameters:
      - in: path
        name: Id
        description: The ID of the hosted zone for which you want to get a list of
          the name servers in thedelegation set
        type: string
      responses:
        200:
          description: OK
      tags:
      - Hosted Zones
    post:
      summary: Update Hosted Zone Comment
      description: Updates the hosted zone comment. Send a POST request to the/2013-04-01/hostedzone/hosted
        zone ID             resource.
      operationId: updatehostedzonecomment
      x-api-path-slug: 20130401hostedzoneid-post
      parameters:
      - in: body
        name: Comment
        description: The new comment for the hosted zone
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: The ID for the hosted zone for which you want to update the comment
        type: string
      - in: body
        name: UpdateHostedZoneCommentRequest
        description: Root level tag for the UpdateHostedZoneCommentRequest parameters
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Hosted Zones
  /2013-04-01/hostedzone/Id/associatevpc:
    post:
      summary: Associate V P C With Hosted Zone
      description: Associates an Amazon VPC with a private hosted zone. ImportantTo
        perform the association, the VPC and the private hosted zone must already
        exist. You can't convert a public hosted zone into a private hosted zone.Send
        a POST request to the /2013-04-01/hostedzone/hosted zone ID/associatevpc resource.
        The request body must include a document with an AssociateVPCWithHostedZoneRequest
        element. The response contains a ChangeInfo data type that you can use to
        track the progress of the request. NoteIf you want to associate a VPC that
        was created by using one AWS account with a private hosted zone that was created
        by using a different account, the AWS account that created the private hosted
        zone must first submit a CreateVPCAssociationAuthorization request. Then the
        account that created the VPC must submit an AssociateVPCWithHostedZone request.
      operationId: associatevpcwithhostedzone
      x-api-path-slug: 20130401hostedzoneidassociatevpc-post
      parameters:
      - in: body
        name: AssociateVPCWithHostedZoneRequest
        description: Root level tag for the AssociateVPCWithHostedZoneRequest parameters
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: Comment
        description: 'Optional: A comment about the association request'
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: The ID of the private hosted zone that you want to associate
          an Amazon VPC with
        type: string
      - in: body
        name: VPC
        description: A complex type that contains information about the VPC that you
          want to associate with a private hosted zone
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - VPC
  /2013-04-01/hostedzone/Id/authorizevpcassociation:
    post:
      summary: Create V P C Association Authorization
      description: Authorizes the AWS account that created a specified VPC to submit
        an AssociateVPCWithHostedZone request to associate the VPC with a specified
        hosted zone that was created by a different account. To submit a CreateVPCAssociationAuthorization
        request, you must use the account that created the hosted zone. After you
        authorize the association, use the account that created the VPC to submit
        an AssociateVPCWithHostedZone request.NoteIf you want to associate multiple
        VPCs that you created by using one account with a hosted zone that you created
        by using a different account, you must submit one authorization request for
        each VPC.Send a POST request to the /2013-04-01/hostedzone/hosted zone ID/authorizevpcassociation
        resource. The request body must include a document with a CreateVPCAssociationAuthorizationRequest
        element. The response contains information about the authorization.
      operationId: createvpcassociationauthorization
      x-api-path-slug: 20130401hostedzoneidauthorizevpcassociation-post
      parameters:
      - in: body
        name: CreateVPCAssociationAuthorizationRequest
        description: Root level tag for the CreateVPCAssociationAuthorizationRequest
          parameters
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: The ID of the private hosted zone that you want to authorize
          associating a VPC with
        type: string
      - in: body
        name: VPC
        description: A complex type that contains the VPC ID and region for the VPC
          that you want to authorize associating with your hosted zone
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - VPC
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