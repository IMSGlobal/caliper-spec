<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="IMS Global Learning Consortium, Inc. Logo" src="../assets/ims-logo-h170w600.png"></div>

# IMS Global Learning Consortium, Inc.

# Caliper Analytics&reg; Sensor Certification Guide, version 1.1

## IPR and Distribution Notices

Recipients of this document are requested to submit, with their comments, notification of any relevant patent claims or other intellectual property rights of which they may be aware that might be infringed by any implementation of the specification set forth in this document, and to provide supporting documentation.

IMS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on IMS’s procedures with respect to rights in IMS specifications can be found at the IMS Intellectual Property Rights web page: [http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Copyright &copy; 2018 IMS Global Learning Consortium. All Rights Reserved.

Use of this guide to develop products or services is governed by the license with IMS found on the IMS website: http://www.imsglobal.org/speclicense.html.

Permission is granted to all parties to use excerpts from this document as needed in producing requests for proposals.

The limited permissions granted above are perpetual and will not be revoked by IMS or its successors or assigns.

THIS GUIDE IS BEING OFFERED WITHOUT ANY WARRANTY WHATSOEVER, AND IN PARTICULAR, ANY WARRANTY OF NON INFRINGEMENT IS EXPRESSLY DISCLAIMED. ANY USE OF THIS GUIDE SHALL BE MADE ENTIRELY AT THE IMPLEMENTER'S OWN RISK, AND NEITHER THE CONSORTIUM, NOR ANY OF ITS MEMBERS OR SUBMITTERS, SHALL HAVE ANY LIABILITY WHATSOEVER TO ANY IMPLEMENTER OR THIRD PARTY FOR ANY DAMAGES OF ANY NATURE WHATSOEVER, DIRECTLY OR INDIRECTLY, ARISING FROM THE USE OF THIS GUIDE.

## Table of Contents
* 1.0 [Introduction](#introduction)
  * 1.1 [Status of this Document](#docStatus)
  * 1.2 [Conventions](#conventions)
  * 1.3 [Terminology](#terminology)
* 2.0 [Certification Prerequisites](#certPreReqs)
* 3.0 [Metric Profile Conformance](#profileConformance)
  * 3.1 [Annotation Profile](#annotationProfile)
  * 3.2 [Assessment Profile](#assessmentProfile)
  * 3.3 [Assignable Profile](#assignableProfile)
  * 3.4 [Forum Profile](#forumProfile)
  * 3.5 [Grading Profile](#gradingProfile)
  * 3.6 [Media Profile](#mediaProfile)
  * 3.7 [Reading Profile](#readingProfile)
  * 3.8 [Session Profile](#sessionProfile)
  * 3.9 [Tool Use Profile](#toolUseProfile)
  * 3.10 [General Profile](#generalProfile)
* 4.0 [Data Interchange Format](#dataFormat)
  * 4.1 [JSON-LD Context](#jsonldContext)
  * 4.2 [Node Identifiers](#jsonldNodeIdentifiers)
  * 4.3 [Type Coercion](#jsonldNodeIdentifiers)
  * 4.4 [Expressing Events as JSON-LD](#jsonldEvents)
  * 4.5 [Expressing Entities as JSON-LD](#jsonldEntities)
* 5.0 [Transport Conformance](#transportConformance)
  * 5.1 [The Envelope](#envelope)
  * 5.2 [HTTP Message Requests](#httpRequest)
  * 5.3 [HTTP Message Responses](#httpResponse)
  * 5.4 [Other Transport Protocols](#otherTransports)
* 6.0 [Using the Certification Service](#usingCertService)
* 7.0 [Certification Mark](#certMark)
* 8.0 [Certification Expiration and Renewal](#certRenewal)
* [List of Contributors](#contributors)
* [References](#references)
* [About this Document](#aboutThisDoc)

## <a name="introduction"></a>1.0 Introduction

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Session Profile" src="../assets/caliper-sensor-v2.png"></div>

The *Caliper Analytics&reg; Specification*, [version 1.1](#caliperSpec), provides a structured approach to describing, collecting and exchanging learning activity data at scale.  Establishing a common vocabulary for describing learning interactions is a central objective.  Promoting data interoperability, data sharing and data-informed decision making are also important goals.

Caliper also defines an application programming interface (the Sensor API&trade;) for marshalling and transmitting event data from instrumented applications to target endpoints for storage, analysis and use.  Industry-wide adoption of Caliper offers the tantalizing prospect of a more unified learning data environment in which to build new and innovative services designed to measure, infer, predict, report and visualize.

This document is the certification guide for Caliper [Sensors](#sensorDef). In this release of the Caliper specification, certification services are not provided for Caliper [endpoints](#endpointDef). Endpoint implementors should take note that it is the intent of the Caliper Working Group to add endpoint certification in forthcoming releases of the specification. Implementors should also note that behavioral requirements for Caliper Endpoints are provided in the *Caliper Analytics&reg; Specification*, version 1.1, [Section 6.0](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#endpoint).

### <a name="docStatus"></a>1.1 Status of this Document
This document is considered the _Final Release_.  This means that the Caliper Analytics&reg; Sensor Certification Guide, version 1.1, is now made available as a public document following acceptance by IMS Global member organizations, a number of whom have successfully achieved conformance certification at the time of the release of this document.
    
IMS Global strongly encourages its members and the greater public to provide feedback that focuses on improving the Caliper specification. To join the IMS developer and conformance certification community focused on Caliper please visit https://www.imsglobal.org/activity/caliper.
    
Public comments and questions can be posted at the Caliper Analytics&reg; [public forum](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum).

### <a name="conventions"></a>1.2 Conventions
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](#rfc2119).  A Sensor implementation that fails to implement a MUST/REQUIRED/SHALL requirement or fails to abide by a MUST NOT/SHALL NOT prohibition is considered nonconformant.  SHOULD/SHOULD NOT/RECOMMENDED statements constitute a best practice.  Ignoring a best practice does not violate conformance but a decision to disregard such guidance should be carefully considered by implementers.  MAY/OPTIONAL statements indicate that implementers are entirely free to choose whether or not to implement the option.

### <a name="terminology"></a>1.3 Terminology
<a name="actorDef"></a>__Actor__: An actor is an [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent) capable of initiating or performing an [action](#actionDef) on a thing or as part of a process.  A Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) includes an `actor` attribute for representing the [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent). 

<a name="blankNodeDef"></a>__Blank Node Identifier__: a string that begins with "_:" that is used to identify an [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) for which an [IRI](#iriDef) is not provided.  An [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) provisioned with a blank node identifier is neither dereferenceable nor has meaning outside the scope of the [JSON-LD](#jsonldDef) document within which it resides.

<a name="actionDef"></a>__Action__: something performed or done to accomplish a purpose.  Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) subtypes define a controlled vocabulary of one or more [actions](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#actions) relevant to the activity domain.  A Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) includes an `action` attribute for expressing the associated action.     

<a name="contextDef"></a>__Context__: a special [JSON-LD](http://json-ld.org/spec/latest/json-ld/) keyword that maps the terms employed in a JSON document to [IRIs](https://www.ietf.org/rfc/rfc3987.txt) that link to one or more published vocabularies.  Inclusion of a [JSON-LD](http://json-ld.org/spec/latest/json-ld/) context provides an economical way of communicating document semantics to services interested in consuming Caliper event data.

<a name="describeDef"></a>__Describe__: a Caliper message containing an [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) that is not directly associated with an [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event). Entities can be sent asynchronously from events using `Describe` messages in order to reduce verbosity (e.g. sending a [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) entity as a `Describe` avoids having to repeat the [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) object in each [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) that includes it).

<a name="endpointDef"></a>__Endpoint__: a receiver or consumer of Caliper data that is bound to a specific network protocol.  

<a name="entityDef"></a>__Entity__: an object or a thing that participates in learning-related activity.  Caliper [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) types provide coarse-grained representations of applications, people, groups and resources that constitute the "stuff" of a Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event).  Each [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) corresponds to a node in a directed graph.

<a name="envelopeDef"></a>__Envelope__: a data structure that serves as a transport container of Caliper [Event](#eventDef) and [Entity](#entityDef) data.  The envelope also includes metadata about the emitting [Sensor](#sensorDef) and the data payload.

<a name="eventDef"></a>__Event__: describes a relationship established between an [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent) (the `actor`) and an [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) (the `object`) formed as a result of a purposeful `action` undertaken by the `actor` in connection to the `object` at a particular moment in time.

<a name="jsonldDef"></a>__JSON-LD__: a specification providing a JSON-based data serialization and messaging format, processing algorithms and API for working with [Linked Data](#linkedDataDef).  The messages described in this guide are intended to be used in programming environments that support [JSON-LD](http://json-ld.org/spec/latest/json-ld/).

<a name="iriDef"></a>__IRI__: The Internationalized Resource Identifier (IRI) extends the Uniform Resource Identifier ([URI](#uriDef)) scheme by using characters drawn from the Universal character set rather than US-ASCII per [RFC 3987](https://www.ietf.org/rfc/rfc3987.txt).  [Linked Data](#linkedDataDef) rely on IRIs to refer to most nodes and properties.

<a name="iso8601Def"></a>__ISO 8601__: Caliper data and time values are formatted per ISO 8601 with the addition of millisecond precision.  The format is yyyy-MM-ddTHH:mm:ss.SSSZ where 'T' separates the date from the time while 'Z' indicates that the time is set to UTC.

<a name="linkedDataDef"></a>__Linked Data__: A set of design principles first articulated by Tim Berners-Lee for discovering, connecting, and sharing structured data over the Web.  The principles can be summarized as follows: use [IRIs](#iriDef)/[URIs](#uriDef) as names for things; use HTTP [IRIs](#iriDef)/[URIs](#uriDef) so that information about things (e.g., people, objects, concepts) can be retrieved using a standard format; link out to other relevant things by way of their [IRIs](#iriDef)/[URIs](#uriDef) in order to promote discovery of new relationships between things.

<a name="metricProfileDef"></a>__Metric Profile__: models a learning activity or a supporting activity that helps facilitate learning.  Each profile provides a domain-specific set of terms and concepts that application designers and developers can draw upon to describe common user interactions in a consistent manner using a shared vocabulary.

<a name="objectDef"></a>__Object__: an [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) that an [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent) interacts with that becomes the focus, target or object of an interaction.  A Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) includes an `object` attribute for representing the resource.

<a name="sensorDef"></a>__Sensor__: Software assets deployed within a learning application that implement the [Sensor API&trade;](#sensorAPIDef) for marshalling and transmitting Caliper data to the certification service endpoint.

<a name="sensorAPIDef"></a>__Sensor API&trade;__: The standard set of methods and supported parameters that a [Sensor](#sensorDef) implements according to the *Caliper Analytics&reg; Specification*, version 1.1, [Section 5.0](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#sensor) in order to transmit Caliper data in an interoperable way.

<a name="termDef"></a>__Term__: a word or short expression that expands to an [IRI](#iriDef) when mapped to a JSON-LD [context](#contextDef) document. Terms are employed by Caliper as `type` property string values in order to distinguish between various JSON representations of entities and events defined by the Caliper information model.

<a name="typeCoercionDef"></a>__Type Coercion__: the process of coercing values to a particular data type.

<a name="uriDef"></a>__URI__:  the Uniform Resource Identifier ([URI](#uriDef)) utilizes the US-ASCII character set to identify a resource.  Per [RFC 2396](#rfc2396) a [URI](#uriDef) "can be further classified as a locator, a name or both."  Both the Uniform Resource Locator ([URL](#urlDef)) and the Uniform Resource Name ([URN](#urnDef)) are considered subspaces of the more general [URI](#uriDef) space. 

<a name="urlDef"></a>__URL__: A Uniform Resource Locator ([URL](#urlDef)) is a type of [URI](#uriDef) that provides a reference to resource that specifies both its location and a means of retrieving a representation of it.  An HTTP [URI](#uriDef) is a [URL](#urlDef) and using HTTP IRIs/URIs to identify things is fundamental to [Linked Data](#linkedDataDef).

<a name="urnDef"></a>__URN__: A Uniform Resource Name ([URN](#urnDef)) is a type of [URI](#uriDef) that provides a persistent identifier for a resource that is bound to a defined namespace.  Unlike a [URL](#urlDef) a [URN](#urnDef) is location-independent and provides no means of accessing a representation of the named resource.  

<a name="uuidDef"></a>__UUID__: a 128-bit identifier that does not require a registration authority to assure uniqueness.  However, absolute uniqueness is not guaranteed although the collision probability is considered extremely low. Caliper recommends use of randomly or pseudo-randomly generated version 4 UUIDs.  Each Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) MUST be assigned a UUID that is expressed as a [URN](#urnDef) using the form `urn:uuid:<UUID>` as described in [RFC 4122](#rfc4122).

## <a name="certPreReqs"></a>2.0 Certification Prerequisites
Certain prerequisites MUST be met before you can certify your platform, application or service as Caliper compliant. 

* Your organization MUST be an IMS Contributing or Affiliate Member.
* You MUST pass the tests using this Certification service.
* The tests MUST be completed by a designated representative of the member organization and you MUST agree that there is no misrepresentation or manipulation of the results in the submitted report.
* You MUST submit your report via the Caliper Certification Service.

## <a name="profileConformance"></a>3.0 Metric Profile Certification
As described more fully in the *Caliper Analytics&reg; Specification*, [version 1.1](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1), the Caliper information model defines a number of metric profiles, each of which models a learning activity or a supporting activity that helps facilitate learning.  Each profile provides a domain-specific set of terms for describing common user interactions. 

Each Caliper profile is also a unit of certification for Caliper [Sensor](#sensorDef) implementations. Any given Sensor may apply for certification for one or more of the Caliper Metric Profiles. In the subsections below, the Minimum Conformance and Restrictions sections specified for each Profile defines the corresponding conformance criteria in detail.

#### General Requirements 
* Certain [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) properties are required and MUST be specified.  Required properties include: `id`, `type`, `actor`, `action`, `object` and `eventTime`.  
* All other [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) properties are considered optional and need not be referenced.  Adherence to the rules associated with each required and/or optional property specified is mandatory.
* Each [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) participating in the [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) MUST be expressed either as an object or as a string corresponding to the resource's [IRI](#iriDef).  
* The actions vocabulary is limited to the supported actions described in the *Caliper Analytics&reg; Specification*, version 1.1, [Appendix A](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#actions), and no other.
* Serialized Events and Entities MUST conform to the syntactical requirements defined in [Section 4.0](#dataFormat) below.  This includes referencing one or more JSON-LD [contexts](#contextDef) by including the JSON-LD `@context` keyword and value as required.  

### <a name="annotationProfile"></a>3.1 Annotation Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Annotation Profile" src="../assets/caliper-profile_annotation.png"></div>

The Caliper Annotation Profile models activities related to the annotation of a [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource).  

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.1](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#annotationProfile).

#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity                                                                        | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                      | ------                                                                                              | ------               |
| [AnnotationEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#annotationEvent) |                                                                                     |                                                                           |                                                                                             |                                                                                                     |                      |
|                                                                                             | [Bookmarked](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#bookmarked)   | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) | [BookmarkAnnotation](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#bookmarkAnnotation)   | **Required**         |
|                                                                                             | [Highlighted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#highlighted) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) | [HighlightAnnotation](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#highlightAnnotation) | Optional             |
|                                                                                             | [Shared](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#shared)           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) | [SharedAnnotation](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#sharedAnnotation)       | Optional             |
|                                                                                             | [Tagged](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#tagged)           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) | [TagAnnotation](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#tagAnnotation)             | Optional             |

### <a name="assessmentProfile"></a>3.2 Assessment Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Assessment Profile" src="../assets/caliper-profile_assessment.png"></div>

The Caliper Assessment Profile models assessment-related activities including interactions with individual assessment items.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.2](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessmentProfile).  

#### Event Conformance Table

| Event                                                                                               | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity                                                  | Required or Optional |
| ------                                                                                              | ------                                                                              | ------                                                                    | ------                                                                                      | ------                                                                        | ------               |
| [AssessmentEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessmentEvent)         |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [Paused](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#paused)           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Assessment](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessment)           | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt)   | Optional             |
|                                                                                                     | [Reset](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#reset)             | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Assessment](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessment)           | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt)   | Optional             |
|                                                                                                     | [Restarted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#restarted)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Assessment](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessment)           | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt)   | Optional             |
|                                                                                                     | [Resumed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#resumed)         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Assessment](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessment)           | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt)   | Optional             |
|                                                                                                     | [Started](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#started)         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Assessment](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessment)           | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt)   | Optional             |
|                                                                                                     | [Submitted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#submitted)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Assessment](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessment)           | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt)   | **Required**         |
| [AssessmentItemEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessmentItemEvent) |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [Completed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#completed)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssessmentItem](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessmentItem)   | [Response](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#response) | Optional             |
|                                                                                                     | [Skipped](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#skipped)         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssessmentItem](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessmentItem)   |                                                                               | Optional             |
|                                                                                                     | [Started](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#started)         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssessmentItem](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessmentItem)   | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt)   | Optional             |
| [NavigationEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigationEvent)         |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [NavigatedTo](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigatedTo) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                                                                               | Optional             |
| [ViewEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewEvent)                     |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [Viewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewed)           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                                                                               | Optional             |

### <a name="assignableProfile"></a>3.3 Assignable Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Assignable Profile" src="../assets/caliper-profile_assignable.png"></div>

The Assignable Profile models activities associated with the assignment of digital content to a learner for completion according to specific criteria.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.3](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableProfile).
 
#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                                          | Recommended Generated Entity                                                | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                                          | ------                                                                      | ------               |
| [AssignableEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableEvent) |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [Activated](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#activated)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssignableDigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableDigitalResource) |                                                                             | Optional             |
|                                                                                             | [Completed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#completed)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssignableDigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableDigitalResource) | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt) | Optional             |
|                                                                                             | [Deactivated](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#deactivated) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssignableDigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableDigitalResource) |                                                                             | Optional             |
|                                                                                             | [Reviewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#reviewed)       | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssignableDigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableDigitalResource) | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt) | Optional             |
|                                                                                             | [Started](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#started)         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssignableDigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableDigitalResource) | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt) | **Required**         |
|                                                                                             | [Submitted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#submitted)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [AssignableDigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assignableDigitalResource) | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt) | **Required**         |
| [NavigationEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigationEvent) |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigatedTo) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource)                     |                                                                             | Optional             |
| [ViewEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewEvent)             |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewed)           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource)                     |                                                                             | Optional             |

 
### <a name="forumProfile"></a>3.4 Forum Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Forum Profile" src="../assets/caliper-profile_forum.png"></div>

The Caliper Forum Profile models learners and others participating in online forum communities.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.4](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#forumProfile).

#### Event Conformance Table

| Event                                                                                       | Action                                                                                    | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                                    | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [ForumEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#forumEvent)           |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Subscribed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#subscribed)         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Forum](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#forum)                     |                              | Optional             |
|                                                                                             | [Unsubscribed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#unsubscribed)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Forum](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#forum)                     |                              | Optional             |
| [MessageEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#messageEvent)       |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [MarkedAsRead](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#markedAsRead)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Message](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#message)                 |                              | Optional             |
|                                                                                             | [MarkedAsUnRead](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#markedAsUnRead) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Message](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#message)                 |                              | Optional             |
|                                                                                             | [Posted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#posted)                 | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Message](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#message)                 |                              | **Required**         |
| [ThreadEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#threadEvent)         |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [MarkedAsRead](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#markedAsRead)     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Thread](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#thread)                   |                              | Optional             |
|                                                                                             | [MarkedAsUnRead](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#markedAsUnRead) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [Thread](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#thread)                   |                              | Optional             |
| [NavigationEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigationEvent) |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigatedTo)       | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                              | Optional             |
| [ViewEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewEvent)             |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewed)                 | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                              | Optional             |
 
 
### <a name="gradingProfile"></a>3.5 Grading Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Grading Profile" src="../assets/caliper-profile_grading.png"></div>

The Caliper Grading Profile models grading activities performed by an [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent), typically a [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) or a [SoftwareApplication](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#softwareApplication).

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.5](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#gradingProfile).

#### Event Conformance Table

| Event                                                                             | Action                                                                    | Actor                                                                              | Object                                                                      | Recommended Generated Entity                                              | Required or Optional |
| ------                                                                            | ------                                                                    | ------                                                                             | ------                                                                      | ------                                                                    | ------               |
| [GradeEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#gradeEvent) |                                                                           |                                                                                    |                                                                             |                                                                           |                      |
|                                                                                   | [Graded](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#graded) | [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent) or subtype | [Attempt](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#attempt) | [Score](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#score)   | **Required**         |
| [ViewEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewEvent)   |                                                                           |                                                                                    |                                                                             |                                                                           |                      |
|                                                                                   | [Viewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewed) | [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent) or subtype | [Viewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewed)   | [Result](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#result) | Optional             |

#### Other Requirements
For auto-graded scenarios the [SoftwareApplication](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#softwareApplication) MUST be specified as the `actor`.  Otherwise, a [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) MUST be specified as the `actor` of the interaction.
 
### <a name="mediaProfile"></a>3.6 Media Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Media Profile" src="../assets/caliper-profile_media.png"></div>

The Caliper Media Profile models interactions between learners and rich content such as audio, images and video.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.6](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaProfile).

#### Event Conformance Table

| Event                                                                                       | Action                                                                                                        | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                                                        | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [MediaEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaEvent)           |                                                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [ChangedResolution](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#changedResolution)               | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [ChangedSize](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#changedSize)                           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [ChangedSpeed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#changedSpeed)                         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [ChangedVolume](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#changedVolume)                       | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [ClosedPopout](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#closedPopout)                         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [DisabledClosedCaptioning](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#disabledClosedCaptioning) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [EnabledClosedCaptioning](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#enabledClosedCaptioning)   | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [Ended](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#ended)                                       | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | **Required**         |
|                                                                                             | [EnteredFullScreen](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#enteredFullScreen)               | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [ExitedFullScreen](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#exitedFullScreen)                 | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [ForwardedTo](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#forwardedTo)                           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [JumpedTo](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#jumpedTo)                                 | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [Muted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#muted)                                       | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [OpenedPopout](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#openedPopout)                         | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [Paused](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#paused)                                     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [Restarted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#restarted)                               | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [Resumed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#resumed)                                   | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
|                                                                                             | [Started](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#started)                                   | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | **Required**         |
|                                                                                             | [Unmuted](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#unmuted)                                   | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [MediaObject](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#mediaObject)         |                              | Optional             |
| [NavigationEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigationEvent) |                                                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigatedTo)                           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                              | Optional             |
| [ViewEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewEvent)             |                                                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewed)                                     | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                              | Optional             |

 
### <a name="readingProfile"></a>3.7 Reading Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Reading Profile" src="../assets/caliper-profile_reading.png"></div>

The Caliper Reading Profile models activities associated with navigating to and viewing digital textual content.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.7](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#readingProfile).

#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [NavigationEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigationEvent) |                                                                                     |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#navigatedTo) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                              | **Required**         |
| [ViewEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewEvent)             |                                                                                     |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#viewed)           | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [DigitalResource](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#digitalResource) |                              | **Required**         |


### <a name="sessionProfile"></a>3.8 Session Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Session Profile" src="../assets/caliper-profile_session.png"></div>

The Caliper Session Profile models the creation and subsequent termination of a user session established by a [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) interacting with a [SoftwareApplication](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#softwareApplication).

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.8](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#sessionProfile).

#### Event Conformance Table

| Event                                                                                 | Action                                                                          | Actor                                                                                               | Object                                                                                              | Recommended Generated Entity | Required or Optional |
| ------                                                                                | ------                                                                          | ------                                                                                              | ------                                                                                              | ------                       | ------               |
| [SessionEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#sessionEvent) |                                                                                 |                                                                                                     |                                                                                                     |                              |                      |
|                                                                                       | [LoggedIn](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#loggedIn)   | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person)                           | [SoftwareApplication](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#softwareApplication) |                              | **Required**         |
|                                                                                       | [LoggedOut](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#loggedOut) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person)                           | [SoftwareApplication](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#softwareApplication) |                              | Optional             |
|                                                                                       | [TimedOut](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#timedOut)   | [SoftwareApplication](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#softwareApplication) | [Session](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#session)                         |                              | Optional             |


### <a name="toolUseProfile"></a>3.9 Tool Use Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Tool Use Profile" src="../assets/caliper-profile_tool_use.png"></div>

The Caliper Tool Use Profile models an intended interaction between a user and a tool.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.9](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#toolUseProfile).

#### Event Conformance Table

| Event                                                                                 | Action                                                                | Actor                                                                     | Object                                                                                              | Recommended Generated Entity | Required or Optional |
| ------                                                                                | ------                                                                | ------                                                                    | ------                                                                                              | ------                       | ------               |
| [ToolUseEvent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#toolUseEvent) |                                                                       |                                                                           |                                                                                                     |                              |                      |
|                                                                                       | [Used](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#used) | [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person) | [SoftwareApplication](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#softwareApplication) |                              | **Required**         |


### <a name="generalProfile"></a>3.10 General Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="General Profile" src="../assets/caliper-profile_basic.png"></div>

The Caliper General Profile provides a generic [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) for describing learning or supporting activities that have yet to be modeled by Caliper. 

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.10](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#generalProfile).

#### Event Conformance Table

| Event                                                                   | Action                                                          | Actor                                                                   | Object                                                                    | Recommended Generated Entity | Required or Optional |
| ------                                                                  | ------                                                          | ------                                                                  | ------                                                                    | ------                       | ------               |
| [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) |                                                                 |                                                                         |                                                                           |                              |                      |
|                                                                         | [*](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#*) | [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent) | [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) |                              | **Required**         |


## <a name="dataFormat"></a>4.0 Data Interchange Format
Caliper events and entities are serialized as [JSON-LD](#jsonldDef), a JSON-based data interchange format that encourages use of shared vocabularies and discoverable key:value identifiers when constructing JSON documents.

### <a name="jsonldContext"></a>4.1 The JSON-LD Context
[JSON-LD](#jsonldDef) documents require inclusion of a *context*, denoted by the `@context` keyword, a property employed to map document [Terms](#termDef) to [IRIs](#iriDef).  [JSON-LD](#jsonldDef) contexts can be embedded inline or referenced externally in a document.  Inclusion of a [JSON-LD](#jsonldDef) context provides an economical way for Caliper to communicate document semantics to services interested in consuming Caliper event data.

IMS Global provides a remote Caliper 1.1 [JSON-LD](#jsonldDef) context document (http://purl.imsglobal.org/ctx/caliper/v1p1) for mapping Caliper [Terms](#termDef) to [IRIs](#iriDef).  Implementers are encouraged to familiarize themselves with the term definitions described therein. 

#### Requirements
* Each Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) and [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) *[describe](#describeDef)* document generated by a [Sensor](#sensorDef) MUST be provisioned with a [JSON-LD](#jsonldDef) `@context` defined as a property of the top-level object.  
* The top-level `@context` property type MUST be defined as a string or an array.
* If the top-level `@context` value is defined as a string it MUST be set to the Caliper remote context URL "http://purl.imsglobal.org/ctx/caliper/v1p1".
* If the top-level `@context` value is defined as an array of multiple contexts, the remote Caliper [JSON-LD](#jsonldDef) context MUST be listed last in order to ensure that Caliper terms retain their primacy given that [JSON-LD](#jsonldDef) parsers rely on a "most-recently-defined-wins" approach when evaluating duplicate terms.
* Referencing the remote Caliper [JSON-LD](#jsonldDef) context document in the top-level `@context` is mandatory.  The terms it defines MUST NOT be defined inline as an object.
* Additional remote or inline _local_ contexts may be referenced any time a JSON object is defined in order to ascribe meaning to terms not described by the model.  These contexts are additive in nature and can be defined as a string, object or array.  Duplicate context references SHOULD be omitted when serializing the object.  Moreover, nested _local_ contexts that are added to the _active_ context at processing time MUST NOT override Caliper terms defined by the top-level context.

For example [JSON-LD](#jsonldDef) context usage see *Caliper Analytics&reg; Specification*, version 1.1, [Section 4.1](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#jsonldContext).

### <a name="jsonldNodeIdentifiers"></a>4.2 Node Identifiers
Caliper specifies the use of [IRIs](#iriDef) for identifying nodes (i.e., the things being described) and their attributes.  [IRI](#iriDef) values MUST be absolute containing a scheme, path and optional query and fragment segments.  A [URI](#uriDef) employing the [URN](#urnDef) scheme MAY be used as an identifier although care should be taken when employing a location-independent identifier since it precludes the possibility of utilizing it in future to retrieve machine-readable data over HTTP.  If an [IRI](#iriDef) is deemed inappropriate for the resource a [blank node](#blankNodeDef) identifier may be assigned.

For additional information regarding identifiers see *Caliper Analytics&reg; Specification*, version 1.1, [Section 4.2](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#jsonldIdentifiers).

### <a name="jsonldTypeCoercion"></a>4.3 Type Coercion
Caliper permits [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) values to be expressed either as a JSON object or as a string corresponding to its [IRI](#iriDef).  [JSON-LD](#jsonldDef) also supports the _coercion_ of data values to specified types based on value type mappings defined in a [JSON-LD](#jsonldDef) context.  For a given `@type` the keywords `@id` or `@vocab` may be assigned as a value in order to signal to a [JSON-LD](#jsonldDef) parser that if a term's instance value is set to a string it is to be interpreted as an [IRI](#iriDef).  Type coercion of this sort provides representational flexibility that implementers are encouraged to leverage.

For examples of coerced Caliper values see *Caliper Analytics&reg; Specification*, version 1.1, [Section 4.3](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#jsonldTypes).

### <a name="jsonldEvents"></a>4.4 Expressing Events as JSON-LD
A Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) is a generic type that describes the relationship established between an `actor` and an `object`, formed as a result of a purposeful [action](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#actions) undertaken by the `actor` at a particular moment in time and within a given learning context.  Caliper defines a number of [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) subtypes, each scoped to a particular activity domain and distinguishable by a `type` attribute.  Considered as a JSON data structure an [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) constitutes an unordered set of key:value pairs that is semi-structured by design.  

The [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) `@context`, `id`, `type`, `actor`, `action`, `object` and `eventTime` properties are required and MUST be specified; all other properties are optional and MAY be omitted when describing an [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event).  Adherence to the rules associated with each property specified is mandatory.  Custom attributes not described by the model MAY be included but MUST be added to the `extensions` property as a map of key:value pairs.  Properties with a value of *null* or empty SHOULD be excluded prior to serialization.

| Property | Disposition |
| :------- | :----------- |
| @context | A top-level [JSON-LD](jsonldDef) context MUST be specified as described above in [Section 4.1](#jsonldContext). |
| id | Set the value to a 128-bit long universally unique identifier (UUID) formatted as a [URN](#urnDef) per [RFC 4122](#rfc4122), which describes a [URN](#urnDef) namespace for [UUIDs](#uuidDef). | 
| type | Set the string value to the relevant Caliper term (e.g., "AssessmentEvent"). |
| actor | Set to [Agent](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#agent) or one of its subtypes (e.g., [Person](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#person)).  The `actor` value MUST be expressed as a JSON object or as a string corresponding to the actor's IRI. |
| action | Set the string value to the relevant action term (e.g., "Started") specified by the governing Metric Profile. |
| object | Set the value to the relevant [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) (e.g., [Assessment](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#assessment)) specified by the governing Metric Profile. The `object` value MUST be expressed as a JSON object or as a string corresponding to the object's IRI. |
| eventTime | Set the date and time value expressed with millisecond precision using the ISO 8601 format YYYY-MM-DDTHH:mm:ss.SSSZ set to UTC with no offset specified. |

For example [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) JSON-LD see *Caliper Analytics&reg; Specification*, version 1.1, [Appendix B](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#events).
  
### <a name="jsonldEntities"></a>4.5 Expressing Entities as JSON-LD
A Caliper [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) is a generic type that represents objects that participate in learning-related activities.  A variety of [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) subtypes have been defined in order to better describe people, groups, organizations, digital content, courses, software applications, and other objects that constitute the "stuff" of a Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event).  Like an [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event), an [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) is considered semi-structured data consisting of an unordered set of key:value pairs.  

As noted in [Section 4.3](#jsonldTypeCoercion) above Caliper permits [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) values to be expressed either as a JSON object or as a string corresponding to its [IRI](#iriDef).

If an [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) is expressed as a JSON object the `id` and `type` properties are required and MUST be specified.  If transmitted as a _[describe](#describeDef)_ a top-level `@context` MUST also be specified.  Otherwise, omit the `@context` when the [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) is specified as a value in an [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) except in cases where custom terms are specified.  See [Section 4.1](#jsonldContext) above for more details regarding [JSON-LD](#jsonldDef) context handling.  

All other properties are optional and MAY be omitted when describing an [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity).  Adherence to the rules associated with each property referenced is mandatory.  Custom attributes not described by the model MAY be included but MUST be added to the `extensions` property as a map of key:value pairs.  Properties with a value of *null* or empty SHOULD be excluded prior to serialization. 

| Property | Disposition |
| :------- | :---------- |
| @context | If the [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) is transmitted as a _[describe](#describeDef)_ a top-level `@context` MUST be specified.  Otherwise, omit the `@context` when the [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) is specified as a value in an [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) except in cases where custom terms are specified. |
| id | Set the string value to a valid [IRI](#iriDef) or a blank node identifier. The [IRI](#iriDef) MUST be unique and persistent.  The [IRI](#iriDef) SHOULD be dereferenceable; i.e., capable of returning a representation of the [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity).  A [URI](#uriDef) employing the [URN](#urnDef) scheme MAY also be utilized. | 
| type | Set the string value to the relevant Caliper term (e.g., "DigitalResource"). |

For example [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) JSON-LD see *Caliper Analytics&reg; Specification*, version 1.1, [Appendix C](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entities).
  
## <a name="transportConformance"></a>5.0 Transport Conformance
 
A Caliper [Sensor](#sensorDef) MUST demonstrate that it is capable of transmitting Caliper data successfully to the certification service [Endpoint](#endpointDef).  Certification is limited to message exchanges using the Hypertext Transport Protocol (HTTP) with the connection encrypted with Transport Layer Security (TLS).  Messages MUST be sent using the POST request method.  For certification purposes, the [Sensor](#sensorDef) MUST also support message authentication using the `Authorization` request header, setting the value to the provided bearer token.
 
#### <a name="envelope"></a>5.1 The Envelope
Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) and [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) data are transmitted inside an [Envelope](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#envelope), a JSON data structure that includes metadata about the emitting [Sensor](#sensorDef) and the data payload.  Each [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) and [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) _[describe](#desribeDef)_ included in an envelope's `data` array MUST be expressed as a [JSON-LD](#jsonld) document. 

The [Envelope](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#envelope) `sensor`, `sendTime`, `dataVersion` and `data` properties MUST be specified.  No custom properties are permitted.

| Required Property | Disposition |
| :---------------- | :----------- |
| sensor | Set the string value to a unique identifier assigned either to the [Sensor](#sensorDef) or to the instrumented platform, application or service utilizing the [Sensor](#sensorDef).  The identifier SHOULD be in the form of an [IRI](#iriDef). |
| eventTime | Set the date and time value expressed with millisecond precision using the ISO 8601 format YYYY-MM-DDTHH:mm:ss.SSSZ set to UTC with no offset specified that indicates the time at which the [Sensor](#sensorDef) issued the message. |
| dataVersion | Set the string value to the Caliper [JSON-LD](#jsonldDef) remote context URL "http://purl.imsglobal.org/ctx/caliper/v1p1".  This indicates that the *Caliper Analytics&reg; Specification*, [version 1.1](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1), governs the form of the Caliper entities and events contained in the `data` payload. |
| data | An ordered collection of one or more Caliper [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) and/or [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) *[describe](#describeDef)* objects.  The Sensor MAY mix [Event](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#event) and [Entity](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#entity) *[describe](#describeDef)* data in the same [Envelope](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#envelope). |

For example [Envelope](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#envelope) JSON-LD see *Caliper Analytics&reg; Specification*, version 1.1, [Section 5.3](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#jsonldPayload).

#### <a name="httpRequest"></a>5.2 HTTP Message Requests
Each HTTP request message sent to the certification service MUST consist of a single serialized JSON representation of a Caliper [Envelope](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#envelope).  Messages MUST be sent using the POST request method.
 
The following standard HTTP request headers MUST be set for each message sent to the certification service [Endpoint](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#endpoint):
  
| Request Header | Disposition |
| :------------- | :----------- |
| Authorization | Set the string value to the bearer token provided by the certification service and associated with the test endpoint (e.g., Authorization: Bearer \<token value\>). |
| Content-Type | Set the string value to the IANA media type "application/json". |
| Host | Set the string value to the test endpoint URL provided by the certification service. |
 
#### <a name="httpResponse"></a>5.3 HTTP Message Responses
 
Following receipt of a [Sensor](#sensorDef) request message the certification service will reply with a response message.  The response will include a three-digit status code indicating whether or not the certification service was able to understand and satisfy the request as defined by [RFC 7231](#rfc7231).  
  
* To signal a Caliper sensor that it has successfully received a message the certification service endpoint will reply with a `2xx` class status code.  The body of a successful response will be empty.
* If a Caliper sensor sends a message containing events and or entities without an enclosing [Envelope](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#envelope), the certification service will reply with a `400 Bad Request` response.
* If a Caliper sensor sends a malformed Caliper endpoint (it does not contain `sensor`, `sendTime`, `dataVersion` and `data` properties of the required form), the certification service will reply with a `400 Bad Request` response.
* If a Caliper sensor sends a message without an `Authorization` request header of the RECOMMENDED form or sends a token credential that the certification service is unable to either validate or determine has sufficient privileges to submit Caliper data, the certification service will reply with a `401 Unauthorized` response.
* If a Caliper sensor sends a message with a `Content-Type` other than "application/json", the certification service will reply with a `415 Unsupported Media Type` response.
* If a Caliper sensor sends a message with an [Envelope](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1#envelope) that contains a `dataVersion` value that the endpoint cannot support the certification service will reply with a `422 Unprocessable Entity` response.
  
The certification service MAY respond to [Sensor](#sensorDef) messages with other standard HTTP status codes to indicate result dispositions that vary from the cases described above.  The certification service MAY also communicate more detailed information about problem states, using the standard method for reporting problem details described in [RFC 7807](#rfc7807).
  
#### <a name="otherTransports"></a>5.4 Other Transport Protocols
*Caliper Analytics&reg; Specification*, [version 1.1](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1) defines the use of a single transport protocol (HTTP/HTTPS).  However, IMS Global is interested in specifying the use of other transport protocols that can support the exchange of Caliper data.  Organizations wishing to work with IMS Global to add other transport protocols to the Caliper specification should contact the Caliper Working Group directly or indicate interest via the [public forum](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum).

## <a name="usingCertService"></a> 6.0 Using the Certification Service
Visit the Caliper Certification service at [https://www.imsglobal.org/sso/launch.php/caliper](https://www.imsglobal.org/sso/launch.php/caliper).  You MUST be logged in to the IMS Global website to access the Caliper certification service.  If you do not have an account, please register at [https://www.imsglobal.org/user/register](https://www.imsglobal.org/user/register).
 
The certification service provides a playground for testing your Caliper messages.  Click the "Start Testing" link under __Test Your Product__ to access the playground.

Once you are ready to commence certification testing, click the "Certify Your Product" link under __Certify Your Product__ to commence testing.  The following steps will guide you through the process.  A [screencast](https://youtu.be/iLCsB2CI7aw) of the certification workflow is available for review.
 
1. Complete the online form by providing the following information:
 
   * Product name
   * Product version
   * Product URL
   * Product description
   * Caliper specification version
   * Member name
   * Member email address
   * Member organization
 
2. Click the green "Start Certification" button.  To terminate testing click the white "Cancel" button.
 
3. An "Instructions" page provides both a test endpoint URL and a bearer token.  Configure your software to send Caliper messages to the test endpoint URL.  For each request, set the HTTP `Authorization` header field value to the provided bearer token and the HTTP `Host` header field value to the provided endpoint URL.
 
4. Initiate the product test, sending messages to the certification service endpoint.  
 
5. When the first message is received by the Certification service the "Instructions" page will be replaced with a view displaying conformance progress.  A list of available Caliper metric profiles is displayed on the left side of the page.  A log of submitted messages or "items" is displayed on the right side of the page.  As messages are processed metric profile certifications that have been attained will be indicated by check marks.  Clicking a profile's plus (+) link will display a list of profile events and actions processed successfully.  Clicking the log "items" link provides additional information regarding events processed, errors encountered and individual message JSON-LD documents received.

6. Once testing is complete click the "Complete Certification" button.

7. Read the confirmation statement and then click the "Submit Certification Results" button.

8. Repeat the test as necessary in order to certify against additional metric profiles or address previous failed tests.

## <a name="certMark"></a>7.0 Certification Mark
After submitting your successful conformance information and receiving confirmation and a registration number from IMS Global you may then apply the appropriate conformance mark. The IMS Global conformance chart will list your conformance details. If you have any questions, please feel free to contact us at any point.  Products without an IMS conformance registration number are not considered compliant by IMS Global.

## <a name="certRenewal"></a>8.0 Certification Expiration and Renewal
Caliper certification covers individual metric profiles only and is scoped to the specific version of the Caliper specification tested.  Major or minor releases of the Caliper specification and/or associated metric profiles will require recertification of your upgraded platform, application or service. All IMS Certifications require that you renew and retest your certification after one year.

## <a name="contributors"></a>Contributors
The following Caliper Working Group participants contributed to the writing of this guide:

#### Authors

| Name | Organization |
| :--- | :----------- |
| Anthony Whyte | University of Michigan |
| Markus Gylling | IMS Global |
| Lisa Mattson | IMS Global |

## <a name="references"></a>References
<a name="caliperSpec"></a>__Caliper Spec__.  IMS Global.  Anthony Whyte, Viktor Haag, Linda Feng, Markus Gylling, Matt Ashbourne, Wes LaMarche and Etienne Pelaprat.  Caliper Analytics® Specification, version 1.1.  12 January 2018.  URL: http://www.imsglobal.org/caliper-spec-v1p1

<a name="jsonldSyntax"></a>__JSON-LD Syntax__.  W3C.  M. Sporny, D. Longley, G. Kellog, M. Lanthaler and N. Lindström.  JSON-LD 1.1.  A JSON-based Serialization for Linked Data. 15 February 2017.  URL: http://json-ld.org/spec/latest/json-ld/

<a name="jsonldProcessing"></a>__JSON-LD Processing__.  D. Longley, G. Kellog, M. Lanthaler, M. Sporny.  JSON-LD 1.1 Processing Algorithms and API.  15 February 2017.  URL: http://json-ld.org/spec/latest/json-ld-api/

<a name="linkedData"></a>__Linked Data__.  Tim Berners-Lee.  "Linked Data."  W3C internal document.  July 2006, rev. June 2009.  URL: https://www.w3.org/DesignIssues/LinkedData.html

<a name="rfc2119"></a>__RFC 2119__.  IETF.  S. Bradner.  "Key words for use in RFCs to Indicate Requirement Levels."  March 1997.  URL: https://tools.ietf.org/html/rfc2119

<a name="rfc2396"></a>__RFC 2396__.  IETF.  T. Berners-Lee, R. Fielding, L. Masinter.  "Uniform Resource Identifiers (URI): Generic Syntax."  August 1998.  URL: https://www.ietf.org/rfc/rfc2396.txt

<a name="rfc3987"></a>__RFC 3987__.  IETF. M. Duerst and M. Suignard.  "Internationalized Resource Identifiers (IRIs).  January 2005.  URL: https://www.ietf.org/rfc/rfc3987.txt

<a name="rfc4122"></a>__RFC 4122__.  IETF. P. Leach, M. Mealling and R. Salz.  "A Universally Unique Identifier (UUID) URN Namespace."  July 2005.  URL: https://tools.ietf.org/html/rfc4122

<a name="rfc6750"></a>__RFC 6750__.  IETF.  M. Jones and D. Hardt.  "The OAuth 2.0 Authorization Framework: Bearer Token Usage."  October 2012.  URL: https://tools.ietf.org/html/rfc6750

<a name="rfc7231"></a>__RFC 7231__.  IETF.  R. Fielding and J. Reschke, eds.  Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content.  June 2014.  URL: https://tools.ietf.org/html/rfc7231.

<a name="rfc7807"></a>__RFC 7807__.  IETF.  M. Nottingham, E. Wilde.  "Problem Details for HTTP APIs."  March 2017.  URL: https://tools.ietf.org/html/rfc7807

## <a name="aboutThisDoc"></a>About this Document
IMS Global Learning Consortium, Inc. ("IMS Global") is publishing the information contained in this document ("Guide") for purposes of scientific, experimental, and scholarly collaboration only.

IMS Global makes no warranty or representation regarding the accuracy or completeness of the Guide.

This material is provided on an "As Is" and "As Available" basis.

The Guide is at all times subject to change and revision without notice.

It is your sole responsibility to evaluate the usefulness, accuracy, and completeness of the Guide as it relates to you.

IMS Global would appreciate receiving your comments and suggestions.

Please contact IMS Global through our website at [http://www.imsglobal.org](http://www.imsglobal.org).

Please refer to Document Name: IMS Caliper Analytics&reg; Certification Guide, version 1.1

Date: 12 January 2018

This document contains trademarks of the IMS Global Learning Consortium including the IMS Logos, Learning Tools Interoperability&reg; (LTI&reg;), Accessible Portable Item Protocol&reg; (APIP&reg;), Question and Test Interoperability&reg; (QTI&reg;), Common Cartridge&reg; (CC&reg;), AccessForAll&trade;, OneRoster&reg;, Caliper Analytics&reg; and SensorAPI&trade;. For more information on the IMS trademark usage policy see trademark policy page - https://www.imsglobal.org/trademarks
