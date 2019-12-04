var t2 = `

## Introduction

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Session Profile" src="../assets/caliper-sensor-v2.png"></div>

[Calreftest](#CALIPER-12)

The *Caliper Analytics&reg; Specification*, [version 1.2](#caliperSpec), provides a structured approach to describing, collecting and exchanging learning activity data at scale.  Establishing a common vocabulary for describing learning interactions is a central objective.  Promoting data interoperability, data sharing and data-informed decision making are also important goals.

Caliper also defines an application programming interface (the Sensor API&trade;) for marshalling and transmitting event data from instrumented applications to target endpoints for storage, analysis and use.  Industry-wide adoption of Caliper offers the tantalizing prospect of a more unified learning data environment in which to build new and innovative services designed to measure, infer, predict, report and visualize.

This document is the certification guide for Caliper [Sensors](#sensorDef). In this release of the Caliper specification, certification services are not provided for Caliper [endpoints](#endpointDef). Endpoint implementors should take note that it is the intent of the Caliper Working Group to add endpoint certification in forthcoming releases of the specification. Implementors should also note that behavioral requirements for Caliper Endpoints are provided in the *Caliper Analytics&reg; Specification*, version 1.1, [Section 6.0](https://www.imsglobal.org/spec/caliper/v1p2#endpoint).

### Status of this Document
This document is considered the _Final Release_.  This means that the Caliper Analytics&reg; Sensor Certification Guide, version 1.1, is now made available as a public document following acceptance by IMS Global member organizations, a number of whom have successfully achieved conformance certification at the time of the release of this document.

IMS Global strongly encourages its members and the greater public to provide feedback that focuses on improving the Caliper specification. To join the IMS developer and conformance certification community focused on Caliper please visit https://www.imsglobal.org/activity/caliper.

Public comments and questions can be posted at the Caliper Analytics&reg; [public forum](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum).

### Conventions
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](#rfc2119).  A Sensor implementation that fails to implement a MUST/REQUIRED/SHALL requirement or fails to abide by a MUST NOT/SHALL NOT prohibition is considered nonconformant.  SHOULD/SHOULD NOT/RECOMMENDED statements constitute a best practice.  Ignoring a best practice does not violate conformance but a decision to disregard such guidance should be carefully considered by implementers.  MAY/OPTIONAL statements indicate that implementers are entirely free to choose whether or not to implement the option.

## <a name="certPreReqs"></a>2.0 Certification Prerequisites
Certain prerequisites MUST be met before you can certify your platform, application or service as Caliper compliant.

* Your organization MUST be an IMS Contributing or Affiliate Member.
* You MUST pass the tests using this Certification service.
* The tests MUST be completed by a designated representative of the member organization and you MUST agree that there is no misrepresentation or manipulation of the results in the submitted report.
* You MUST submit your report via the Caliper Certification Service.

## <a name="profileConformance"></a>3.0 Metric Profile Certification
As described more fully in the *Caliper Analytics&reg; Specification*, [version 1.1](https://www.imsglobal.org/spec/caliper/v1p2), the Caliper information model defines a number of metric profiles, each of which models a learning activity or a supporting activity that helps facilitate learning.  Each profile provides a domain-specific set of terms for describing common user interactions.

Each Caliper profile is also a unit of certification for Caliper [Sensor](#sensorDef) implementations. Any given Sensor may apply for certification for one or more of the Caliper Metric Profiles. In the subsections below, the Minimum Conformance and Restrictions sections specified for each Profile defines the corresponding conformance criteria in detail.

#### General Requirements
* Certain [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) properties are required and MUST be specified.  Required properties include: <code>id</code>, <code>type</code>, <code>actor</code>, <code>action</code>, <code>object</code> and <code>eventTime</code>.
* All other [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) properties are considered optional and need not be referenced.  Adherence to the rules associated with each required and/or optional property specified is mandatory.
* Each [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) participating in the [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) MUST be expressed either as an object or as a string corresponding to the resource's [IRI](#iriDef).
* The actions vocabulary is limited to the supported actions described in the *Caliper Analytics&reg; Specification*, version 1.1, [Appendix A](https://www.imsglobal.org/spec/caliper/v1p2#actions), and no other.
* Serialized Events and Entities MUST conform to the syntactical requirements defined in [Section 4.0](#dataFormat) below.  This includes referencing one or more JSON-LD [contexts](#contextDef) by including the JSON-LD <code>@context</code> keyword and value as required.

### <a name="annotationProfile"></a>3.1 Annotation Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Annotation Profile" src="../assets/caliper-profile_annotation.png"></div>

The Caliper Annotation Profile models activities related to the annotation of a [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource).

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.1](https://www.imsglobal.org/spec/caliper/v1p2#profile-annotation).

#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity                                                                        | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                      | ------                                                                                              | ------               |
| [AnnotationEvent](https://www.imsglobal.org/spec/caliper/v1p2#AnnotationEvent) |                                                                                     |                                                                           |                                                                                             |                                                                                                     |                      |
|                                                                                             | [Bookmarked](https://www.imsglobal.org/spec/caliper/v1p2#bookmarked)   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | [BookmarkAnnotation](https://www.imsglobal.org/spec/caliper/v1p2#BookmarkAnnotation)   | **Required**         |
|                                                                                             | [Highlighted](https://www.imsglobal.org/spec/caliper/v1p2#highlighted) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | [HighlightAnnotation](https://www.imsglobal.org/spec/caliper/v1p2#HighlightAnnotation) | Optional             |
|                                                                                             | [Shared](https://www.imsglobal.org/spec/caliper/v1p2#shared)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | [SharedAnnotation](https://www.imsglobal.org/spec/caliper/v1p2#SharedAnnotation)       | Optional             |
|                                                                                             | [Tagged](https://www.imsglobal.org/spec/caliper/v1p2#tagged)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | [TagAnnotation](https://www.imsglobal.org/spec/caliper/v1p2#TagAnnotation)             | Optional             |

### <a name="assessmentProfile"></a>3.2 Assessment Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Assessment Profile" src="../assets/caliper-profile_assessment.png"></div>

The Caliper Assessment Profile models assessment-related activities including interactions with individual assessment items.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.2](https://www.imsglobal.org/spec/caliper/v1p2#profile-assessment).

#### Event Conformance Table

| Event                                                                                               | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity                                                  | Required or Optional |
| ------                                                                                              | ------                                                                              | ------                                                                    | ------                                                                                      | ------                                                                        | ------               |
| [AssessmentEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentEvent)         |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [Paused](https://www.imsglobal.org/spec/caliper/v1p2#paused)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Assessment](https://www.imsglobal.org/spec/caliper/v1p2#assessment)           | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
|                                                                                                     | [Reset](https://www.imsglobal.org/spec/caliper/v1p2#reset)             | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Assessment](https://www.imsglobal.org/spec/caliper/v1p2#assessment)           | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
|                                                                                                     | [Restarted](https://www.imsglobal.org/spec/caliper/v1p2#restarted)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Assessment](https://www.imsglobal.org/spec/caliper/v1p2#assessment)           | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
|                                                                                                     | [Resumed](https://www.imsglobal.org/spec/caliper/v1p2#resumed)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Assessment](https://www.imsglobal.org/spec/caliper/v1p2#assessment)           | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
|                                                                                                     | [Started](https://www.imsglobal.org/spec/caliper/v1p2#started)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Assessment](https://www.imsglobal.org/spec/caliper/v1p2#assessment)           | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
|                                                                                                     | [Submitted](https://www.imsglobal.org/spec/caliper/v1p2#submitted)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Assessment](https://www.imsglobal.org/spec/caliper/v1p2#assessment)           | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | **Required**         |
| [AssessmentItemEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentItemEvent) |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [Completed](https://www.imsglobal.org/spec/caliper/v1p2#completed)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssessmentItem](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentItem)   | [Response](https://www.imsglobal.org/spec/caliper/v1p2#response) | Optional             |
|                                                                                                     | [Skipped](https://www.imsglobal.org/spec/caliper/v1p2#skipped)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssessmentItem](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentItem)   |                                                                               | Optional             |
|                                                                                                     | [Started](https://www.imsglobal.org/spec/caliper/v1p2#started)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssessmentItem](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentItem)   | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent)         |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#navigatedTo) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                               | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)                     |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                               | Optional             |

### <a name="assignableProfile"></a>3.3 Assignable Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Assignable Profile" src="../assets/caliper-profile_assignable.png"></div>

The Assignable Profile models activities associated with the assignment of digital content to a learner for completion according to specific criteria.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.3](https://www.imsglobal.org/spec/caliper/v1p2#profile-assignable).

#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                                          | Recommended Generated Entity                                                | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                                          | ------                                                                      | ------               |
| [AssignableEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssignableEvent) |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [Activated](https://www.imsglobal.org/spec/caliper/v1p2#activated)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) |                                                                             | Optional             |
|                                                                                             | [Completed](https://www.imsglobal.org/spec/caliper/v1p2#completed)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | Optional             |
|                                                                                             | [Deactivated](https://www.imsglobal.org/spec/caliper/v1p2#deactivated) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) |                                                                             | Optional             |
|                                                                                             | [Reviewed](https://www.imsglobal.org/spec/caliper/v1p2#reviewed)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | Optional             |
|                                                                                             | [Started](https://www.imsglobal.org/spec/caliper/v1p2#started)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | **Required**         |
|                                                                                             | [Submitted](https://www.imsglobal.org/spec/caliper/v1p2#submitted)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | **Required**         |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent) |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#navigatedTo) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource)                     |                                                                             | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource)                     |                                                                             | Optional             |


### <a name="forumProfile"></a>3.4 Forum Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Forum Profile" src="../assets/caliper-profile_forum.png"></div>

The Caliper Forum Profile models learners and others participating in online forum communities.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.4](https://www.imsglobal.org/spec/caliper/v1p2#profile-forum).

#### Event Conformance Table

| Event                                                                                       | Action                                                                                    | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                                    | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [ForumEvent](https://www.imsglobal.org/spec/caliper/v1p2#ForumEvent)           |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Subscribed](https://www.imsglobal.org/spec/caliper/v1p2#subscribed)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Forum](https://www.imsglobal.org/spec/caliper/v1p2#forum)                     |                              | Optional             |
|                                                                                             | [Unsubscribed](https://www.imsglobal.org/spec/caliper/v1p2#unsubscribed)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Forum](https://www.imsglobal.org/spec/caliper/v1p2#forum)                     |                              | Optional             |
| [MessageEvent](https://www.imsglobal.org/spec/caliper/v1p2#MessageEvent)       |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [MarkedAsRead](https://www.imsglobal.org/spec/caliper/v1p2#markedAsRead)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Message](https://www.imsglobal.org/spec/caliper/v1p2#message)                 |                              | Optional             |
|                                                                                             | [MarkedAsUnRead](https://www.imsglobal.org/spec/caliper/v1p2#markedAsUnRead) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Message](https://www.imsglobal.org/spec/caliper/v1p2#message)                 |                              | Optional             |
|                                                                                             | [Posted](https://www.imsglobal.org/spec/caliper/v1p2#posted)                 | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Message](https://www.imsglobal.org/spec/caliper/v1p2#message)                 |                              | **Required**         |
| [ThreadEvent](https://www.imsglobal.org/spec/caliper/v1p2#ThreadEvent)         |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [MarkedAsRead](https://www.imsglobal.org/spec/caliper/v1p2#markedAsRead)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Thread](https://www.imsglobal.org/spec/caliper/v1p2#thread)                   |                              | Optional             |
|                                                                                             | [MarkedAsUnRead](https://www.imsglobal.org/spec/caliper/v1p2#markedAsUnRead) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Thread](https://www.imsglobal.org/spec/caliper/v1p2#thread)                   |                              | Optional             |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent) |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#navigatedTo)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)                 | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |


### <a name="gradingProfile"></a>3.5 Grading Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Grading Profile" src="../assets/caliper-profile_grading.png"></div>

The Caliper Grading Profile models grading activities performed by an [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent), typically a [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) or a [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication).

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.5](https://www.imsglobal.org/spec/caliper/v1p2#profile-grading).

#### Event Conformance Table

| Event                                                                             | Action                                                                    | Actor                                                                              | Object                                                                      | Recommended Generated Entity                                              | Required or Optional |
| ------                                                                            | ------                                                                    | ------                                                                             | ------                                                                      | ------                                                                    | ------               |
| [GradeEvent](https://www.imsglobal.org/spec/caliper/v1p2#GradeEvent) |                                                                           |                                                                                    |                                                                             |                                                                           |                      |
|                                                                                   | [Graded](https://www.imsglobal.org/spec/caliper/v1p2#graded) | [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) or subtype | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | [Score](https://www.imsglobal.org/spec/caliper/v1p2#score)   | **Required**         |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)   |                                                                           |                                                                                    |                                                                             |                                                                           |                      |
|                                                                                   | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed) | [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) or subtype | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)   | [Result](https://www.imsglobal.org/spec/caliper/v1p2#result) | Optional             |

#### Other Requirements
For auto-graded scenarios the [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) MUST be specified as the <code>actor</code>.  Otherwise, a [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) MUST be specified as the <code>actor</code> of the interaction.

### <a name="mediaProfile"></a>3.6 Media Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Media Profile" src="../assets/caliper-profile_media.png"></div>

The Caliper Media Profile models interactions between learners and rich content such as audio, images and video.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.6](https://www.imsglobal.org/spec/caliper/v1p2#profile-media).

#### Event Conformance Table

| Event                                                                                       | Action                                                                                                        | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                                                        | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [MediaEvent](https://www.imsglobal.org/spec/caliper/v1p2#MediaEvent)           |                                                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [ChangedResolution](https://www.imsglobal.org/spec/caliper/v1p2#changedResolution)               | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [ChangedSize](https://www.imsglobal.org/spec/caliper/v1p2#changedSize)                           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [ChangedSpeed](https://www.imsglobal.org/spec/caliper/v1p2#changedSpeed)                         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [ChangedVolume](https://www.imsglobal.org/spec/caliper/v1p2#changedVolume)                       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [ClosedPopout](https://www.imsglobal.org/spec/caliper/v1p2#closedPopout)                         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [DisabledClosedCaptioning](https://www.imsglobal.org/spec/caliper/v1p2#disabledClosedCaptioning) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [EnabledClosedCaptioning](https://www.imsglobal.org/spec/caliper/v1p2#enabledClosedCaptioning)   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [Ended](https://www.imsglobal.org/spec/caliper/v1p2#ended)                                       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | **Required**         |
|                                                                                             | [EnteredFullScreen](https://www.imsglobal.org/spec/caliper/v1p2#enteredFullScreen)               | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [ExitedFullScreen](https://www.imsglobal.org/spec/caliper/v1p2#exitedFullScreen)                 | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [ForwardedTo](https://www.imsglobal.org/spec/caliper/v1p2#forwardedTo)                           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [JumpedTo](https://www.imsglobal.org/spec/caliper/v1p2#jumpedTo)                                 | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [Muted](https://www.imsglobal.org/spec/caliper/v1p2#muted)                                       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [OpenedPopout](https://www.imsglobal.org/spec/caliper/v1p2#openedPopout)                         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [Paused](https://www.imsglobal.org/spec/caliper/v1p2#paused)                                     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [Restarted](https://www.imsglobal.org/spec/caliper/v1p2#restarted)                               | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [Resumed](https://www.imsglobal.org/spec/caliper/v1p2#resumed)                                   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
|                                                                                             | [Started](https://www.imsglobal.org/spec/caliper/v1p2#started)                                   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | **Required**         |
|                                                                                             | [Unmuted](https://www.imsglobal.org/spec/caliper/v1p2#unmuted)                                   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [MediaObject](https://www.imsglobal.org/spec/caliper/v1p2#MediaObject)         |                              | Optional             |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent) |                                                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#navigatedTo)                           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)                                     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |


### <a name="readingProfile"></a>3.7 Reading Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Reading Profile" src="../assets/caliper-profile_reading.png"></div>

The Caliper Reading Profile models activities associated with navigating to and viewing digital textual content.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.7](https://www.imsglobal.org/spec/caliper/v1p2#profile-reading).

#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent) |                                                                                     |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#navigatedTo) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | **Required**         |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                     |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | **Required**         |


### <a name="sessionProfile"></a>3.8 Session Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Session Profile" src="../assets/caliper-profile_session.png"></div>

The Caliper Session Profile models the creation and subsequent termination of a user session established by a [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) interacting with a [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication).

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.8](https://www.imsglobal.org/spec/caliper/v1p2#profile-session).

#### Event Conformance Table

| Event                                                                                 | Action                                                                          | Actor                                                                                               | Object                                                                                              | Recommended Generated Entity | Required or Optional |
| ------                                                                                | ------                                                                          | ------                                                                                              | ------                                                                                              | ------                       | ------               |
| [SessionEvent](https://www.imsglobal.org/spec/caliper/v1p2#SessionEvent) |                                                                                 |                                                                                                     |                                                                                                     |                              |                      |
|                                                                                       | [LoggedIn](https://www.imsglobal.org/spec/caliper/v1p2#loggedIn)   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person)                           | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | **Required**         |
|                                                                                       | [LoggedOut](https://www.imsglobal.org/spec/caliper/v1p2#loggedOut) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person)                           | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | Optional             |
|                                                                                       | [TimedOut](https://www.imsglobal.org/spec/caliper/v1p2#timedOut)   | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) | [Session](https://www.imsglobal.org/spec/caliper/v1p2#session)                         |                              | Optional             |


### <a name="toolUseProfile"></a>3.9 Tool Use Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Tool Use Profile" src="../assets/caliper-profile_tool_use.png"></div>

The Caliper Tool Use Profile models an intended interaction between a user and a tool.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.9](https://www.imsglobal.org/spec/caliper/v1p2#profile-tooluse).

#### Event Conformance Table

| Event                                                                                 | Action                                                                | Actor                                                                     | Object                                                                                              | Recommended Generated Entity | Required or Optional |
| ------                                                                                | ------                                                                | ------                                                                    | ------                                                                                              | ------                       | ------               |
| [ToolUseEvent](https://www.imsglobal.org/spec/caliper/v1p2#ToolUseEvent) |                                                                       |                                                                           |                                                                                                     |                              |                      |
|                                                                                       | [Used](https://www.imsglobal.org/spec/caliper/v1p2#used) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | **Required**         |


### <a name="generalProfile"></a>3.10 General Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="General Profile" src="../assets/caliper-profile_basic.png"></div>

The Caliper General Profile provides a generic [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) for describing learning or supporting activities that have yet to be modeled by Caliper.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.1, [Section 3.10](https://www.imsglobal.org/spec/caliper/v1p2#profile-general).

#### Event Conformance Table

| Event                                                                   | Action                                                          | Actor                                                                   | Object                                                                    | Recommended Generated Entity | Required or Optional |
| ------                                                                  | ------                                                          | ------                                                                  | ------                                                                    | ------                       | ------               |
| [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) |                                                                 |                                                                         |                                                                           |                              |                      |
|                                                                         | [*](https://www.imsglobal.org/spec/caliper/v1p2#*) | [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) | [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) |                              | **Required**         |


## <a name="dataFormat"></a>4.0 Data Interchange Format
Caliper events and entities are serialized as [JSON-LD](#jsonldDef), a JSON-based data interchange format that encourages use of shared vocabularies and discoverable key:value identifiers when constructing JSON documents.

### <a name="jsonldContext"></a>4.1 The JSON-LD Context
[JSON-LD](#jsonldDef) documents require inclusion of a *context*, denoted by the <code>@context</code> keyword, a property employed to map document [Terms](#termDef) to [IRIs](#iriDef).  [JSON-LD](#jsonldDef) contexts can be embedded inline or referenced externally in a document.  Inclusion of a [JSON-LD](#jsonldDef) context provides an economical way for Caliper to communicate document semantics to services interested in consuming Caliper event data.

IMS Global provides a remote Caliper 1.1 [JSON-LD](#jsonldDef) context document (http://purl.imsglobal.org/ctx/caliper/v1p1) for mapping Caliper [Terms](#termDef) to [IRIs](#iriDef).  Implementers are encouraged to familiarize themselves with the term definitions described therein.

#### Requirements
* Each Caliper [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) and [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) *[describe](#describeDef)* document generated by a [Sensor](#sensorDef) MUST be provisioned with a [JSON-LD](#jsonldDef) <code>@context</code> defined as a property of the top-level object.
* The top-level <code>@context</code> property type MUST be defined as a string or an array.
* If the top-level <code>@context</code> value is defined as a string it MUST be set to the Caliper remote context URL "http://purl.imsglobal.org/ctx/caliper/v1p1".
* If the top-level <code>@context</code> value is defined as an array of multiple contexts, the remote Caliper [JSON-LD](#jsonldDef) context MUST be listed last in order to ensure that Caliper terms retain their primacy given that [JSON-LD](#jsonldDef) parsers rely on a "most-recently-defined-wins" approach when evaluating duplicate terms.
* Referencing the remote Caliper [JSON-LD](#jsonldDef) context document in the top-level <code>@context</code> is mandatory.  The terms it defines MUST NOT be defined inline as an object.
* Additional remote or inline _local_ contexts may be referenced any time a JSON object is defined in order to ascribe meaning to terms not described by the model.  These contexts are additive in nature and can be defined as a string, object or array.  Duplicate context references SHOULD be omitted when serializing the object.  Moreover, nested _local_ contexts that are added to the _active_ context at processing time MUST NOT override Caliper terms defined by the top-level context.

For example [JSON-LD](#jsonldDef) context usage see *Caliper Analytics&reg; Specification*, version 1.1, [Section 4.1](https://www.imsglobal.org/spec/caliper/v1p2#jsonldContext).

### <a name="jsonldNodeIdentifiers"></a>4.2 Node Identifiers
Caliper specifies the use of [IRIs](#iriDef) for identifying nodes (i.e., the things being described) and their attributes.  [IRI](#iriDef) values MUST be absolute containing a scheme, path and optional query and fragment segments.  A [URI](#uriDef) employing the [URN](#urnDef) scheme MAY be used as an identifier although care should be taken when employing a location-independent identifier since it precludes the possibility of utilizing it in future to retrieve machine-readable data over HTTP.  If an [IRI](#iriDef) is deemed inappropriate for the resource a [blank node](#blankNodeDef) identifier may be assigned.

For additional information regarding identifiers see *Caliper Analytics&reg; Specification*, version 1.1, [Section 4.2](https://www.imsglobal.org/spec/caliper/v1p2#jsonldIdentifiers).

### <a name="jsonldTypeCoercion"></a>4.3 Type Coercion
Caliper permits [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) values to be expressed either as a JSON object or as a string corresponding to its [IRI](#iriDef).  [JSON-LD](#jsonldDef) also supports the _coercion_ of data values to specified types based on value type mappings defined in a [JSON-LD](#jsonldDef) context.  For a given <code>@type</code> the keywords <code>@id</code> or <code>@vocab</code> may be assigned as a value in order to signal to a [JSON-LD](#jsonldDef) parser that if a term's instance value is set to a string it is to be interpreted as an [IRI](#iriDef).  Type coercion of this sort provides representational flexibility that implementers are encouraged to leverage.

For examples of coerced Caliper values see *Caliper Analytics&reg; Specification*, version 1.1, [Section 4.3](https://www.imsglobal.org/spec/caliper/v1p2#jsonldTypes).

### <a name="jsonldEvents"></a>4.4 Expressing Events as JSON-LD
A Caliper [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) is a generic type that describes the relationship established between an <code>actor</code> and an <code>object</code>, formed as a result of a purposeful [action](https://www.imsglobal.org/spec/caliper/v1p2#actions) undertaken by the <code>actor</code> at a particular moment in time and within a given learning context.  Caliper defines a number of [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) subtypes, each scoped to a particular activity domain and distinguishable by a <code>type</code> attribute.  Considered as a JSON data structure an [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) constitutes an unordered set of key:value pairs that is semi-structured by design.

The [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) <code>@context</code>, <code>id</code>, <code>type</code>, <code>actor</code>, <code>action</code>, <code>object</code> and <code>eventTime</code> properties are required and MUST be specified; all other properties are optional and MAY be omitted when describing an [Event](https://www.imsglobal.org/spec/caliper/v1p2#event).  Adherence to the rules associated with each property specified is mandatory.  Custom attributes not described by the model MAY be included but MUST be added to the <code>extensions</code> property as a map of key:value pairs.  Properties with a value of *null* or empty SHOULD be excluded prior to serialization.

| Property | Disposition |
| :------- | :----------- |
| @context | A top-level [JSON-LD](jsonldDef) context MUST be specified as described above in [Section 4.1](#jsonldContext). |
| id | Set the value to a 128-bit long universally unique identifier (UUID) formatted as a [URN](#urnDef) per [RFC 4122](#rfc4122), which describes a [URN](#urnDef) namespace for [UUIDs](#uuidDef). |
| type | Set the string value to the relevant Caliper term (e.g., "AssessmentEvent"). |
| actor | Set to [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) or one of its subtypes (e.g., [Person](https://www.imsglobal.org/spec/caliper/v1p2#person)).  The <code>actor</code> value MUST be expressed as a JSON object or as a string corresponding to the actor's IRI. |
| action | Set the string value to the relevant action term (e.g., "Started") specified by the governing Metric Profile. |
| object | Set the value to the relevant [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) (e.g., [Assessment](https://www.imsglobal.org/spec/caliper/v1p2#assessment)) specified by the governing Metric Profile. The <code>object</code> value MUST be expressed as a JSON object or as a string corresponding to the object's IRI. |
| eventTime | Set the date and time value expressed with millisecond precision using the ISO 8601 format YYYY-MM-DDTHH:mm:ss.SSSZ set to UTC with no offset specified. |

For example [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) JSON-LD see *Caliper Analytics&reg; Specification*, version 1.1, [Appendix B](https://www.imsglobal.org/spec/caliper/v1p2#events).

### <a name="jsonldEntities"></a>4.5 Expressing Entities as JSON-LD
A Caliper [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) is a generic type that represents objects that participate in learning-related activities.  A variety of [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) subtypes have been defined in order to better describe people, groups, organizations, digital content, courses, software applications, and other objects that constitute the "stuff" of a Caliper [Event](https://www.imsglobal.org/spec/caliper/v1p2#event).  Like an [Event](https://www.imsglobal.org/spec/caliper/v1p2#event), an [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) is considered semi-structured data consisting of an unordered set of key:value pairs.

As noted in [Section 4.3](#jsonldTypeCoercion) above Caliper permits [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) values to be expressed either as a JSON object or as a string corresponding to its [IRI](#iriDef).

If an [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) is expressed as a JSON object the <code>id</code> and <code>type</code> properties are required and MUST be specified.  If transmitted as a _[describe](#describeDef)_ a top-level <code>@context</code> MUST also be specified.  Otherwise, omit the <code>@context</code> when the [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) is specified as a value in an [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) except in cases where custom terms are specified.  See [Section 4.1](#jsonldContext) above for more details regarding [JSON-LD](#jsonldDef) context handling.

All other properties are optional and MAY be omitted when describing an [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity).  Adherence to the rules associated with each property referenced is mandatory.  Custom attributes not described by the model MAY be included but MUST be added to the <code>extensions</code> property as a map of key:value pairs.  Properties with a value of *null* or empty SHOULD be excluded prior to serialization.

| Property | Disposition |
| :------- | :---------- |
| @context | If the [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) is transmitted as a _[describe](#describeDef)_ a top-level <code>@context</code> MUST be specified.  Otherwise, omit the <code>@context</code> when the [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) is specified as a value in an [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) except in cases where custom terms are specified. |
| id | Set the string value to a valid [IRI](#iriDef) or a blank node identifier. The [IRI](#iriDef) MUST be unique and persistent.  The [IRI](#iriDef) SHOULD be dereferenceable; i.e., capable of returning a representation of the [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity).  A [URI](#uriDef) employing the [URN](#urnDef) scheme MAY also be utilized. |
| type | Set the string value to the relevant Caliper term (e.g., "DigitalResource"). |

For example [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) JSON-LD see *Caliper Analytics&reg; Specification*, version 1.1, [Appendix C](https://www.imsglobal.org/spec/caliper/v1p2#entities).

## <a name="transportConformance"></a>5.0 Transport Conformance

A Caliper [Sensor](#sensorDef) MUST demonstrate that it is capable of transmitting Caliper data successfully to the certification service [Endpoint](#endpointDef).  Certification is limited to message exchanges using the Hypertext Transport Protocol (HTTP) with the connection encrypted with Transport Layer Security (TLS).  Messages MUST be sent using the POST request method.  For certification purposes, the [Sensor](#sensorDef) MUST also support message authentication using the <code>Authorization</code> request header, setting the value to the provided bearer token.

#### <a name="envelope"></a>5.1 The Envelope
Caliper [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) and [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) data are transmitted inside an [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope), a JSON data structure that includes metadata about the emitting [Sensor](#sensorDef) and the data payload.  Each [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) and [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) _[describe](#desribeDef)_ included in an envelope's <code>data</code> array MUST be expressed as a [JSON-LD](#jsonld) document.

The [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope) <code>sensor</code>, <code>sendTime</code>, <code>dataVersion</code> and <code>data</code> properties MUST be specified.  No custom properties are permitted.

| Required Property | Disposition |
| :---------------- | :----------- |
| sensor | Set the string value to a unique identifier assigned either to the [Sensor](#sensorDef) or to the instrumented platform, application or service utilizing the [Sensor](#sensorDef).  The identifier SHOULD be in the form of an [IRI](#iriDef). |
| eventTime | Set the date and time value expressed with millisecond precision using the ISO 8601 format YYYY-MM-DDTHH:mm:ss.SSSZ set to UTC with no offset specified that indicates the time at which the [Sensor](#sensorDef) issued the message. |
| dataVersion | Set the string value to the Caliper [JSON-LD](#jsonldDef) remote context URL "http://purl.imsglobal.org/ctx/caliper/v1p1".  This indicates that the *Caliper Analytics&reg; Specification*, [version 1.1](https://www.imsglobal.org/spec/caliper/v1p2), governs the form of the Caliper entities and events contained in the <code>data</code> payload. |
| data | An ordered collection of one or more Caliper [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) and/or [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) *[describe](#describeDef)* objects.  The Sensor MAY mix [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) and [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) *[describe](#describeDef)* data in the same [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope). |

For example [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope) JSON-LD see *Caliper Analytics&reg; Specification*, version 1.1, [Section 5.3](https://www.imsglobal.org/spec/caliper/v1p2#jsonldPayload).

#### <a name="httpRequest"></a>5.2 HTTP Message Requests
Each HTTP request message sent to the certification service MUST consist of a single serialized JSON representation of a Caliper [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope).  Messages MUST be sent using the POST request method.

The following standard HTTP request headers MUST be set for each message sent to the certification service [Endpoint](https://www.imsglobal.org/spec/caliper/v1p2#endpoint):

| Request Header | Disposition |
| :------------- | :----------- |
| Authorization | Set the string value to the bearer token provided by the certification service and associated with the test endpoint (e.g., Authorization: Bearer \<token value\>). |
| Content-Type | Set the string value to the IANA media type "application/json". |
| Host | Set the string value to the test endpoint URL provided by the certification service. |

#### <a name="httpResponse"></a>5.3 HTTP Message Responses

Following receipt of a [Sensor](#sensorDef) request message the certification service will reply with a response message.  The response will include a three-digit status code indicating whether or not the certification service was able to understand and satisfy the request as defined by [RFC 7231](#rfc7231).

* To signal a Caliper sensor that it has successfully received a message the certification service endpoint will reply with a <code>2xx</code> class status code.  The body of a successful response will be empty.
* If a Caliper sensor sends a message containing events and or entities without an enclosing [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope), the certification service will reply with a <code>400 Bad Request</code> response.
* If a Caliper sensor sends a malformed Caliper endpoint (it does not contain <code>sensor</code>, <code>sendTime</code>, <code>dataVersion</code> and <code>data</code> properties of the required form), the certification service will reply with a <code>400 Bad Request</code> response.
* If a Caliper sensor sends a message without an <code>Authorization</code> request header of the RECOMMENDED form or sends a token credential that the certification service is unable to either validate or determine has sufficient privileges to submit Caliper data, the certification service will reply with a <code>401 Unauthorized</code> response.
* If a Caliper sensor sends a message with a <code>Content-Type</code> other than "application/json", the certification service will reply with a <code>415 Unsupported Media Type</code> response.
* If a Caliper sensor sends a message with an [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope) that contains a <code>dataVersion</code> value that the endpoint cannot support the certification service will reply with a <code>422 Unprocessable Entity</code> response.

The certification service MAY respond to [Sensor](#sensorDef) messages with other standard HTTP status codes to indicate result dispositions that vary from the cases described above.  The certification service MAY also communicate more detailed information about problem states, using the standard method for reporting problem details described in [RFC 7807](#rfc7807).

#### <a name="otherTransports"></a>5.4 Other Transport Protocols
*Caliper Analytics&reg; Specification*, [version 1.1](https://www.imsglobal.org/spec/caliper/v1p2) defines the use of a single transport protocol (HTTP/HTTPS).  However, IMS Global is interested in specifying the use of other transport protocols that can support the exchange of Caliper data.  Organizations wishing to work with IMS Global to add other transport protocols to the Caliper specification should contact the Caliper Working Group directly or indicate interest via the [public forum](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum).

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

3. An "Instructions" page provides both a test endpoint URL and a bearer token.  Configure your software to send Caliper messages to the test endpoint URL.  For each request, set the HTTP <code>Authorization</code> header field value to the provided bearer token and the HTTP <code>Host</code> header field value to the provided endpoint URL.

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
| Bracken Mosbacker | IMS Global |
| Joshua McGhee | IMS Global |
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

`;
