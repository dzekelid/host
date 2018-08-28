---
swagger: "2.0"
x-collection-name: AWS Route 53
x-complete: 0
info:
  title: AWS Route 53 API List Traffic Policy Instances By Hosted Zone
  version: 1.0.0
  description: 'Gets information about the traffic policy instances that you created
    in a specifiedhosted zone.NoteAfter you submit an UpdateTrafficPolicyInstance
    request, there''s a briefdelay while Amazon Route 53 creates the resource record
    sets that are specified in the traffic policydefinition. For more information,
    see the State response element.Send a GET request to the /Amazon Route 53 APIversion/trafficpolicyinstance
    resource and include the ID of the hostedzone.Amazon Route 53 returns a maximum
    of 100 items in each response. If you have a lot of trafficpolicy instances, you
    can use the MaxItems parameter to list them in groups of upto 100.The response
    includes four values that help you navigate from one group ofMaxItems traffic
    policy instances to the next:             IsTruncated               If the value
    of IsTruncated in the response is true, there aremore traffic policy instances
    associated with the current AWS account.If IsTruncated is false, this response
    includes the lasttraffic policy instance that is associated with the current account.             MaxItems           The
    value that you specified for the MaxItems parameter in the requestthat produced
    the current response.                  TrafficPolicyInstanceNameMarker and TrafficPolicyInstanceTypeMarker               If
    IsTruncated is true, these two values in the responserepresent the first traffic
    policy instance in the next group of MaxItemstraffic policy instances. To list
    more traffic policy instances, make another call toListTrafficPolicyInstancesByHostedZone,
    and specify these values in thecorresponding request parameters.If IsTruncated
    is false, all three elements are omittedfrom the response.'
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
  /2013-04-01/hostedzone/Id/deauthorizevpcassociation:
    post:
      summary: Delete V P C Association Authorization
      description: Removes authorization to submit an AssociateVPCWithHostedZone request
        to associate a specified VPC with a hosted zone that was created by a different
        account. You must use the account that created the hosted zone to submit a
        DeleteVPCAssociationAuthorization request.ImportantSending this request only
        prevents the AWS account that created the VPC from associating the VPC with
        the Amazon Route 53 hosted zone in the future. If the VPC is already associated
        with the hosted zone, DeleteVPCAssociationAuthorization won't disassociate
        the VPC from the hosted zone. If you want to delete an existing association,
        use DisassociateVPCFromHostedZone.Send a DELETE request to the /2013-04-01/hostedzone/hosted
        zone ID/deauthorizevpcassociation resource. The request body must include
        a document with a DeleteVPCAssociationAuthorizationRequest element.
      operationId: deletevpcassociationauthorization
      x-api-path-slug: 20130401hostedzoneiddeauthorizevpcassociation-post
      parameters:
      - in: body
        name: DeleteVPCAssociationAuthorizationRequest
        description: Root level tag for the DeleteVPCAssociationAuthorizationRequest
          parameters
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: When removing authorization to associate a VPC that was created
          by one AWS account with a hosted zone that was created with a different
          AWS account, the ID of the hosted zone
        type: string
      - in: body
        name: VPC
        description: When removing authorization to associate a VPC that was created
          by one AWS account with a hosted zone that was created with a different
          AWS account, a complex type that includes the ID and region of the VPC
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - VPC
  /2013-04-01/hostedzone/Id/disassociatevpc:
    post:
      summary: Disassociate V P C From Hosted Zone
      description: Disassociates a VPC from a Amazon Route 53 private hosted zone.
        NoteYou can't disassociate the last VPC from a private hosted zone.Send a
        POST request to the /2013-04-01/hostedzone/hosted zone ID/disassociatevpcresource.
        The request body must include a document with a DisassociateVPCFromHostedZoneRequest
        element. The response includes a DisassociateVPCFromHostedZoneResponse element.ImportantYou
        can't disassociate a VPC from a private hosted zone when only one VPC is associated
        with the hosted zone. You also can't convert a private hosted zone into a
        public hosted zone.
      operationId: disassociatevpcfromhostedzone
      x-api-path-slug: 20130401hostedzoneiddisassociatevpc-post
      parameters:
      - in: body
        name: Comment
        description: 'Optional: A comment about the disassociation request'
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: DisassociateVPCFromHostedZoneRequest
        description: Root level tag for the DisassociateVPCFromHostedZoneRequest parameters
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: The ID of the private hosted zone that you want to disassociate
          a VPC from
        type: string
      - in: body
        name: VPC
        description: A complex type that contains information about the VPC that youre
          disassociatingfrom the specified hosted zone
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - VPC
  /2013-04-01/hostedzone/Id/rrset/:
    post:
      summary: Change Resource Record Sets
      description: 'Create, change, update, or delete authoritative DNS information
        on all Amazon Route 53 servers.Send a POST request to:             /2013-04-01/hostedzone/Amazon
        Route 53 hosted ZoneID/rrset resource. The request body must include a document
        with aChangeResourceRecordSetsRequest element. The request body contains a
        list ofchange items, known as a change batch. Change batches are considered
        transactional changes.When using the Amazon Route 53 API to change resource
        record sets, Amazon Route 53 either makes all or none of thechanges in a change
        batch request. This ensures that Amazon Route 53 never partially implements
        theintended changes to the resource record sets in a hosted zone. For example,
        a change batch request that deletes the CNAME record forwww.example.com and
        creates an alias resource record set for www.example.com. Amazon Route 53
        deletesthe first resource record set and creates the second resource record
        set in a singleoperation. If either the DELETE or the CREATE action fails,
        thenboth changes (plus any other changes in the batch) fail, and the original
        CNAMErecord continues to exist.ImportantDue to the nature of transactional
        changes, you can''t delete the same resourcerecord set more than once in a
        single change batch. If you attempt to delete the same changebatch more than
        once, Amazon Route 53 returns an InvalidChangeBatch error.NoteTo create resource
        record sets for complex routing configurations, use either thetraffic flow
        visual editor in the Amazon Route 53 console or the API actions for traffic
        policies andtraffic policy instances. Save the configuration as a traffic
        policy, then associate thetraffic policy with one or more domain names (such
        as example.com) or subdomain names (suchas www.example.com), in the same hosted
        zone or in multiple hosted zones. You can roll backthe updates if the new
        configuration isn''t performing as expected. For more information, seeUsing
        Traffic Flow to Route DNSTraffic in the Amazon Route 53 Developer Guide.Use
        ChangeResourceRecordsSetsRequest to perform the following actions:                  CREATE:
        Creates a resource record set that has the specified values.                  DELETE:
        Deletes an existing resource record set that has the specified values.                  UPSERT:
        If a resource record set does not already exist, AWS createsit. If a resource
        set does exist, Amazon Route 53 updates it with the values in the request.
        The values that you need to include in the request depend on the type of resource
        record set that you''re creating, deleting, or updating:            Basic
        resource record sets (excluding alias, failover, geolocation, latency, and
        weighted resource record sets)                           Name                                 Type                                 TTL                           Failover,
        geolocation, latency, or weighted resource record sets (excluding alias resource
        record sets)                           Name                                 Type                                 TTL                                 SetIdentifier                           Alias
        resource record sets (including failover alias, geolocation alias, latency
        alias, and weighted alias resource record sets)                           Name                                 Type                                 AliasTarget
        (includes DNSName, EvaluateTargetHealth, and HostedZoneId)                  SetIdentifier
        (for failover, geolocation, latency, and weighted resource record sets)When
        you submit a ChangeResourceRecordSets request, Amazon Route 53 propagates
        your changes to all of the Amazon Route 53 authoritative DNS servers. While
        your changes are propagating, GetChange returns a status of PENDING. When
        propagation is complete, GetChange returns a status of INSYNC. Changes generally
        propagate to all Amazon Route 53 name servers in a few minutes. In rare circumstances,
        propagation can take up to 30 minutes. For more information, see GetChange       For
        information about the limits on a ChangeResourceRecordSets request, see Limits
        in the Amazon Route 53 Developer Guide.'
      operationId: changeresourcerecordsets
      x-api-path-slug: 20130401hostedzoneidrrset-post
      parameters:
      - in: body
        name: ChangeBatch
        description: A complex type that contains an optional comment and the Changeselement
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: ChangeResourceRecordSetsRequest
        description: Root level tag for the ChangeResourceRecordSetsRequest parameters
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: The ID of the hosted zone that contains the resource record sets
          that you want tochange
        type: string
      responses:
        200:
          description: OK
      tags:
      - Changes
  /2013-04-01/hostedzonecount:
    get:
      summary: Get Hosted Zone Count
      description: Retrieves a count of all your hosted zones. Send a GET request
        to the/2013-04-01/hostedzonecount resource.
      operationId: gethostedzonecount
      x-api-path-slug: 20130401hostedzonecount-get
      responses:
        200:
          description: OK
      tags:
      - Hosted Zones
  /2013-04-01/hostedzonesbyname?dnsname=DNSName&amp;hostedzoneid=HostedZoneId&amp;maxitems=MaxItems:
    get:
      summary: List Hosted Zones By Name
      description: 'Retrieves a list of your hosted zones in lexicographic order.
        Send a GETrequest to the /2013-04-01/hostedzonesbyname resource. The response
        includes aHostedZones child element for each hosted zone created by the current
        AWSaccount.             ListHostedZonesByName sorts hosted zones by name with
        the labels reversed.For example:                  com.example.www.               Note
        the trailing dot, which can change the sort order in some circumstances.If
        the domain name includes escape characters or Punycode,ListHostedZonesByName
        alphabetizes the domain name using the escaped orPunycoded value, which is
        the format that Amazon Route 53 saves in its database. For example, to createa
        hosted zone for example.com, specify ex\344mple.com for the domain name.ListHostedZonesByName
        alphabetizes it as:                  com.ex\344mple.               The labels
        are reversed and alphabetized using the escaped value. For more informationabout
        valid domain name formats, including internationalized domain names, see DNS
        Domain Name Format in theAmazon Route 53 Developer Guide.Amazon Route 53 returns
        up to 100 items in each response. If you have a lot of hosted zones, usethe
        MaxItems parameter to list them in groups of up to 100. The response includesvalues
        that help navigate from one group of MaxItems hosted zones to thenext:The
        DNSName and HostedZoneId elements in the responsecontain the values, if any,
        specified for the dnsname andhostedzoneid parameters in the request that produced
        the currentresponse.The MaxItems element in the response contains the value,
        if any, thatyou specified for the maxitems parameter in the request that produced
        thecurrent response.If the value of IsTruncated in the response is true, there
        are morehosted zones associated with the current AWS account. If IsTruncated
        is false, this response includes the last hosted zonethat is associated with
        the current account. The NextDNSName element andNextHostedZoneId elements
        are omitted from the response.The NextDNSName and NextHostedZoneId elements
        in theresponse contain the domain name and the hosted zone ID of the next
        hosted zone that isassociated with the current AWS account. If you want to
        list more hosted zones, makeanother call to ListHostedZonesByName, and specify
        the value ofNextDNSName and NextHostedZoneId in the dnsnameand hostedzoneid
        parameters, respectively.'
      operationId: listhostedzonesbyname
      x-api-path-slug: 20130401hostedzonesbynamednsnamednsnameamphostedzoneidhostedzoneidampmaxitemsmaxitems-get
      parameters:
      - in: path
        name: dnsname
        description: (Optional) For your first request to ListHostedZonesByName, include
          thednsname parameter only if you want to specify the name of the first hosted
          zonein the response
        type: string
      responses:
        200:
          description: OK
      tags:
      - Hosted Zones
  ? /2013-04-01/testdnsanswer&amp;edns0clientsubnetip=EDNS0ClientSubnetIP&amp;edns0clientsubnetmask=EDNS0ClientSubnetMask?hostedzoneid=HostedZoneId&amp;recordname=RecordName&amp;recordtype=RecordType&amp;resolverip=ResolverIP
  : get:
      summary: Test D N S Answer
      description: Gets the value that Amazon Route 53 returns in response to a DNS
        request for a specified record name and type. You can optionally specify the
        IP address of a DNS resolver, an EDNS0 client subnet IP address, and a subnet
        mask.
      operationId: testdnsanswer
      x-api-path-slug: 20130401testdnsanswerampedns0clientsubnetipedns0clientsubnetipampedns0clientsubnetmaskedns0clientsubnetmaskhostedzoneidhostedzoneidamprecordnamerecordnameamprecordtyperecordtypeampresolveripresolverip-get
      parameters:
      - in: path
        name: edns0clientsubnetip
        description: If the resolver that you specified for resolverip supports EDNS0,
          specify the IP address of a client in the applicable location
        type: string
      responses:
        200:
          description: OK
      tags:
      - DNS
  ? /2013-04-01/trafficpolicyinstances/hostedzone?id=HostedZoneId&amp;maxitems=MaxItems&amp;trafficpolicyinstancename=TrafficPolicyInstanceNameMarker&amp;trafficpolicyinstancetype=TrafficPolicyInstanceTypeMarker
  : get:
      summary: List Traffic Policy Instances By Hosted Zone
      description: 'Gets information about the traffic policy instances that you created
        in a specifiedhosted zone.NoteAfter you submit an UpdateTrafficPolicyInstance
        request, there''s a briefdelay while Amazon Route 53 creates the resource
        record sets that are specified in the traffic policydefinition. For more information,
        see the State response element.Send a GET request to the /Amazon Route 53
        APIversion/trafficpolicyinstance resource and include the ID of the hostedzone.Amazon
        Route 53 returns a maximum of 100 items in each response. If you have a lot
        of trafficpolicy instances, you can use the MaxItems parameter to list them
        in groups of upto 100.The response includes four values that help you navigate
        from one group ofMaxItems traffic policy instances to the next:             IsTruncated               If
        the value of IsTruncated in the response is true, there aremore traffic policy
        instances associated with the current AWS account.If IsTruncated is false,
        this response includes the lasttraffic policy instance that is associated
        with the current account.             MaxItems           The value that you
        specified for the MaxItems parameter in the requestthat produced the current
        response.                  TrafficPolicyInstanceNameMarker and TrafficPolicyInstanceTypeMarker               If
        IsTruncated is true, these two values in the responserepresent the first traffic
        policy instance in the next group of MaxItemstraffic policy instances. To
        list more traffic policy instances, make another call toListTrafficPolicyInstancesByHostedZone,
        and specify these values in thecorresponding request parameters.If IsTruncated
        is false, all three elements are omittedfrom the response.'
      operationId: listtrafficpolicyinstancesbyhostedzone
      x-api-path-slug: 20130401trafficpolicyinstanceshostedzoneidhostedzoneidampmaxitemsmaxitemsamptrafficpolicyinstancenametrafficpolicyinstancenamemarkeramptrafficpolicyinstancetypetrafficpolicyinstancetypemarker-get
      parameters:
      - in: path
        name: id
        description: The ID of the hosted zone for which you want to list traffic
          policyinstances
        type: string
      responses:
        200:
          description: OK
      tags:
      - Traffic Policies
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