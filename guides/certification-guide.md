var t2 = `

## Introduction

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Session Profile" src="../assets/caliper-sensor-v2.png"></div>

The *Caliper Analytics&reg; Specification*, [version 1.2](https://www.imsglobal.org/spec/caliper/v1p2), provides a structured approach to describing, collecting, and exchanging learning activity data at scale.  Establishing a common vocabulary for describing learning interactions is a central objective.  Promoting data interoperability, data sharing, and data-informed decision making are also important goals.

Caliper also defines an application programming interface (the Sensor API&trade;), commonly referred to as [Sensors](https://www.imsglobal.org/spec/caliper/v1p2#sensor), for marshalling and transmitting event data from instrumented applications to target [endpoints](https://www.imsglobal.org/spec/caliper/v1p2#endpoint) for storage, analysis and use.  Industry-wide adoption of Caliper offers the tantalizing prospect of a more unified learning data environment in which to build new and innovative services designed to measure, infer, predict, report and visualize.


This document is the certification guide for Caliper Sensors. In this release of the Caliper specification, certification services are not provided for Caliper endpoints. Endpoint implementors should take note that it is the intent of the Caliper Working Group to add endpoint certification in forthcoming releases of the specification. Implementors should also note that behavioral requirements for Caliper Endpoints are provided in the *Caliper Analytics&reg; Specification*, version 1.2, [Section 6.0](https://www.imsglobal.org/spec/caliper/v1p2#endpoint).

### Status of this Document
This document is considered the _Final Release_.  This means that the Caliper Analytics&reg; Sensor Certification Guide, version 1.2, is now made available as a public document following acceptance by IMS Global member organizations, a number of whom have successfully achieved conformance certification at the time of the release of this document.

IMS Global strongly encourages its members and the greater public to provide feedback that focuses on improving the Caliper specification. To join the IMS developer and conformance certification community focused on Caliper please visit https://www.imsglobal.org/activity/caliper.

Public comments and questions can be posted at the Caliper Analytics&reg; [public forum](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum).

### Conventions
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [[RFC2119]].  A Sensor implementation that fails to implement a MUST/REQUIRED/SHALL requirement or fails to abide by a MUST NOT/SHALL NOT prohibition is considered nonconformant.  SHOULD/SHOULD NOT/RECOMMENDED statements constitute a best practice.  Ignoring a best practice does not violate conformance but a decision to disregard such guidance should be carefully considered by implementers.  MAY/OPTIONAL statements indicate that implementers are entirely free to choose whether or not to implement the option.

## The Conformance Process

<section id="conformance">
  <h3>Conformance Statements</h3>
</section>

### <a name="certPreReqs"></a>Certification Prerequisites
The following prerequisites MUST be met before your organization can begin the process of getting your product Caliper Analytics&reg; certified.

* Your organization MUST be an IMS Contributing or Affiliate Member.
* You MUST pass the tests using the Caliper Certification Service.
* The tests MUST be completed by a designated representative of the member organization and you MUST agree that there is no misrepresentation or manipulation of the results in the submitted report.
* You MUST submit your report via the Caliper Certification Service.

### <a name="confTestProc"></a> Conformance Testing Process
Visit the Caliper Certification service at [https://www.imsglobal.org/sso/launch.php/caliper](https://www.imsglobal.org/sso/launch.php/caliper).  You MUST be logged in to the IMS Global website to access the Caliper certification service.  If you do not have an account, please register at [https://www.imsglobal.org/user/register](https://www.imsglobal.org/user/register).

The certification service provides a playground for testing your Caliper messages.  Click the "Caliper Playground" link under __Test Your Product__ to access the playground.

Once you are ready to commence certification testing, click the "Certify Your Product" link under __Certify Your Product__ to commence testing.  The following steps will guide you through the process.  A [screencast](https://youtu.be/iLCsB2CI7aw) of the certification workflow is available for review.

1. Complete the online form by providing the following information:

   * Product name
   * Product version
   * Product URL
   * Product description
   * Caliper specification version
   * Member organization
   * Representative name
   * Representative email address
   * Information for who should be contacted about certification expiration

2. Click the green "Start Certification" button.  To terminate testing click the white "Cancel" button.

3. An "Instructions" page provides both a test endpoint URL and a bearer token.  Configure your software to send Caliper messages to the test endpoint URL.  For each request, set the HTTP <code>Authorization</code> header field value to the provided bearer token, for example: <code>Authorization: Bearer 16b33d7e-32ae-4c12-ba10-1a1f08a0d5d7</code> and the HTTP <code>Host</code> header field value to the provided endpoint URL.

4. Initiate the product test, sending messages to the certification service endpoint.

5. When the first message is received by the Certification service the "Instructions" page will be replaced with a view displaying conformance progress.  A list of available Caliper metric profiles is displayed on the left side of the page.  A log of submitted messages or "items" is displayed on the right side of the page.  As messages are processed metric profile certifications that have been attained will be indicated by check marks.  Clicking a profile's plus (+) link will display a list of profile events and actions processed successfully.  Clicking the log "items" link provides additional information regarding events processed, errors encountered and individual message JSON-LD documents received.

6. Once testing is complete click the "Complete Certification" button.

7. Read the confirmation statement and then click the "Submit Certification Results" button.

8. Repeat the test as necessary in order to certify against additional metric profiles or address previous failed tests.

#### <a name="certMark"></a>Certification Mark
After submitting your successful conformance information and receiving confirmation and a registration number from IMS Global via email you may then apply the appropriate conformance mark. The IMS Global conformance chart will list your conformance details. If you have any questions, please feel free to contact us at any point.  Products without an IMS conformance registration number are not considered compliant by IMS Global.

#### <a name="certRenewal"></a>Certification Expiration and Renewal
Caliper certification covers individual metric profiles only and is scoped to the specific version of the Caliper specification tested.  Major or minor releases of the Caliper specification and/or associated metric profiles will require recertification of your upgraded platform, application or service. All IMS Certifications require that you renew and retest your certification after one year.


## <a name="profileConformance"></a>Metric Profile Certification
As described more fully in the *Caliper Analytics&reg; Specification*, [version 1.2 section 3](https://www.imsglobal.org/spec/caliper/v1p2#profiles), the Caliper information model defines a number of metric profiles, each of which models a learning activity or a supporting activity that helps facilitate learning.  Each profile provides a domain-specific set of terms for describing common user interactions.

Each Caliper profile is also a unit of certification for Caliper [Sensor](https://www.imsglobal.org/spec/caliper/v1p2#sensor) implementations. Any given Sensor may apply for certification for one or more of the Caliper Metric Profiles. In the subsections below, the Minimum Conformance and Restrictions sections specified for each Profile defines the corresponding conformance criteria in detail.

#### General Requirements
* Certain [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) properties are required and MUST be specified.  Required properties include: <code>id</code>, <code>type</code>, <code>actor</code>, <code>action</code>, <code>object</code> and <code>eventTime</code>.
* All other [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) properties are considered optional and need not be referenced.  Adherence to the rules associated with each required and/or optional property specified is mandatory.
* Each [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) participating in the [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) MUST be expressed either as an object or as a string corresponding to the resource's [IRI](https://www.imsglobal.org/spec/caliper/v1p2#iriDef).
* The actions vocabulary is limited to the supported actions described in the *Caliper Analytics&reg; Specification*, version 1.2, [Actions Appendix](https://www.imsglobal.org/spec/caliper/v1p2#actions), and no other.
* Serialized Events and Entities MUST conform to the syntactical requirements defined in the Caliper specification, and be contained within a Caliper [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope) using proper [JSON-LD context and serialization](https://www.imsglobal.org/spec/caliper/v1p2#serialization)

### <a name="generalProfile"></a>General Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="General Profile" src="../assets/caliper-profile_basic.png"></div>

The Caliper General Profile provides a generic [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) for describing learning or supporting activities that have yet to be modeled by Caliper.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.10](https://www.imsglobal.org/spec/caliper/v1p2#profile-general).

#### Event Conformance Table

| Event                                                                   | Action                                                          | Actor                                                                   | Object                                                                    | Recommended Generated Entity | Required or Optional |
| ------                                                                  | ------                                                          | ------                                                                  | ------                                                                    | ------                       | ------               |
| [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) |                                                                 |                                                                         |                                                                           |                              |                      |
|                                                                         | * | [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) | [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) |                              | **Required**         |


### <a name="annotationProfile"></a>Annotation Profile

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

### <a name="assessmentProfile"></a>Assessment Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Assessment Profile" src="../assets/caliper-profile_assessment.png"></div>

The Caliper Assessment Profile models assessment-related activities including interactions with individual assessment items.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.2](https://www.imsglobal.org/spec/caliper/v1p2#profile-assessment).

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
|                                                                                                     | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#action-navigatedTo) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                               | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)                     |                                                                                     |                                                                           |                                                                                             |                                                                               |                      |
|                                                                                                     | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                               | Optional             |

### <a name="assignableProfile"></a>Assignable Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Assignable Profile" src="../assets/caliper-profile_assignable.png"></div>

The Assignable Profile models activities associated with the assignment of digital content to a learner for completion according to specific criteria.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.3](https://www.imsglobal.org/spec/caliper/v1p2#profile-assignable).

#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                                          | Recommended Generated Entity                                                | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                                          | ------                                                                      | ------               |
| [AssignableEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssignableEvent) |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [Activated](https://www.imsglobal.org/spec/caliper/v1p2#activated)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) |                                                                             | Optional             |
|                                                                                             | [Completed](https://www.imsglobal.org/spec/caliper/v1p2#completed)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | Optional             |
|                                                                                             | [Deactivated](https://www.imsglobal.org/spec/caliper/v1p2#deactivated) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) |                                                                             | Optional             |
|                                                                                             | [Reviewed](https://www.imsglobal.org/spec/caliper/v1p2#reviewed)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | Optional             |
|                                                                                             | [Started](https://www.imsglobal.org/spec/caliper/v1p2#started)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | Optional         |
|                                                                                             | [Submitted](https://www.imsglobal.org/spec/caliper/v1p2#submitted)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [AssignableDigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#AssignableDigitalResource) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | **Required**         |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent) |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#action-navigatedTo) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource)                     |                                                                             | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                     |                                                                           |                                                                                                                 |                                                                             |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource)                     |                                                                             | Optional             |


### <a name="feedbackProfile"></a>Feedback Profile


The Caliper Feedback Profile models providing feedback and comments on Entities.

#### Profile Description

See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.4](https://www.imsglobal.org/spec/caliper/v1p2#profile-feedback).

#### Event Conformance Table

The Feedback Profile only has two actions for the FeedbackEvent and they can each solve different use-cases. To achieve conformance for this profile at least one of the actions must be used.

| Event                                                                                   | Action                                                                          | Actor                                                                     | Object                                                                    | Recommended Generated Entity | Required or Optional |
| ------                                                                                  | ------                                                                          | ------                                                                    | ------                                                                    | ------                       | ------               |
| [FeedbackEvent](https://www.imsglobal.org/spec/caliper/v1p2#FeedbackEvent) |                                                                                 |                                                                           |                                                                           |                              |                      |
|                                                                                         | [Commented](https://www.imsglobal.org/spec/caliper/v1p2#commented) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) |                              | **At least 1 Required** |
|                                                                                         | [Ranked](https://www.imsglobal.org/spec/caliper/v1p2#ranked)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) |                              | **At least 1 Required** |


### <a name="forumProfile"></a>Forum Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Forum Profile" src="../assets/caliper-profile_forum.png"></div>

The Caliper Forum Profile models learners and others participating in online forum communities.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.5](https://www.imsglobal.org/spec/caliper/v1p2#profile-forum).

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
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#action-navigatedTo)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                           |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)                 | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |


### <a name="gradingProfile"></a>Grading Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Grading Profile" src="../assets/caliper-profile_grading.png"></div>

The Caliper Grading Profile models grading activities performed by an [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent), typically a [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) or a [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication).

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.6](https://www.imsglobal.org/spec/caliper/v1p2#profile-grading).

#### Event Conformance Table

| Event                                                                             | Action                                                                    | Actor                                                                              | Object                                                                      | Recommended Generated Entity                                              | Required or Optional |
| ------                                                                            | ------                                                                    | ------                                                                             | ------                                                                      | ------                                                                    | ------               |
| [GradeEvent](https://www.imsglobal.org/spec/caliper/v1p2#GradeEvent) |                                                                           |                                                                                    |                                                                             |                                                                           |                      |
|                                                                                   | [Graded](https://www.imsglobal.org/spec/caliper/v1p2#graded) | [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) or subtype | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt) | [Score](https://www.imsglobal.org/spec/caliper/v1p2#score)   | **Required**         |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)   |                                                                           |                                                                                    |                                                                             |                                                                           |                      |
|                                                                                   | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed) | [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) or subtype | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)   | [Result](https://www.imsglobal.org/spec/caliper/v1p2#result) | Optional             |

#### Other Requirements
For auto-graded scenarios the [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) MUST be specified as the <code>actor</code>.  Otherwise, a [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) MUST be specified as the <code>actor</code> of the interaction.

### <a name="mediaProfile"></a>Media Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Media Profile" src="../assets/caliper-profile_media.png"></div>

The Caliper Media Profile models interactions between learners and rich content such as audio, images and video.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.7](https://www.imsglobal.org/spec/caliper/v1p2#profile-media).

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
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#action-navigatedTo)                           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)                                     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | Optional             |


### <a name="readingProfile"></a>Reading Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Reading Profile" src="../assets/caliper-profile_reading.png"></div>

The Caliper Reading Profile models activities associated with navigating to and viewing digital textual content.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.8](https://www.imsglobal.org/spec/caliper/v1p2#profile-reading).

#### Event Conformance Table

| Event                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent) |                                                                                     |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#action-navigatedTo) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | **Required**         |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)             |                                                                                     |                                                                           |                                                                                             |                              |                      |
|                                                                                             | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | **Required**         |

### <a name="resourceManagementProfile"></a>3.10 Resource Management Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Results Management Profile" src="../assets/caliper-profile_resource_management.png"></div>

The Caliper Resource Management Profile models a [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) managing a [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource)

#### Profile Description

See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.9](https://www.imsglobal.org/spec/caliper/v1p2#profile-resourcemanagement).

#### Event Conformance Table

| Event                                                                                                       | Action                                                                              | Actor                                                                     | Object                                                                                      | Recommended Generated Entity                                                                | Required or Optional |
| ------                                                                                                      | ------                                                                              | ------                                                                    | ------                                                                                      | ------                                                                                      | ------               |
| [ResourceManagementEvent](https://www.imsglobal.org/spec/caliper/v1p2#ResourceManagementEvent) |                                                                                     |                                                                           |                                                                                             |                                                                                             |                      |
|                                                                                                             | [Archived](https://www.imsglobal.org/spec/caliper/v1p2#archived)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Copied](https://www.imsglobal.org/spec/caliper/v1p2#copied)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | Optional             |
|                                                                                                             | [Created](https://www.imsglobal.org/spec/caliper/v1p2#created)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) | **Required**         |
|                                                                                                             | [Deleted](https://www.imsglobal.org/spec/caliper/v1p2#deleted)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Described](https://www.imsglobal.org/spec/caliper/v1p2#described)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Downloaded](https://www.imsglobal.org/spec/caliper/v1p2#downloaded)   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Modified](https://www.imsglobal.org/spec/caliper/v1p2#modified)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Printed](https://www.imsglobal.org/spec/caliper/v1p2#printed)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Published](https://www.imsglobal.org/spec/caliper/v1p2#published)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Restored](https://www.imsglobal.org/spec/caliper/v1p2#restored)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Retrieved](https://www.imsglobal.org/spec/caliper/v1p2#retrieved)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Saved](https://www.imsglobal.org/spec/caliper/v1p2#saved)             | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Unpublished](https://www.imsglobal.org/spec/caliper/v1p2#unpublished) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |
|                                                                                                             | [Uploaded](https://www.imsglobal.org/spec/caliper/v1p2#uploaded)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                                                                                             | Optional             |



### <a name="searchProfile"></a>3.11 Search Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Search  Profile" src="../assets/caliper-profile_search.png"></div>

The Caliper Search Profile models an <code>actor</code>, typically a learner, querying a resource for information. The profile provides a [SearchEvent](https://www.imsglobal.org/spec/caliper/v1p2#SearchEvent) and a [Searched](https://www.imsglobal.org/spec/caliper/v1p2#searched) action for describing information retrieval activities. An optional [SearchResponse](https://www.imsglobal.org/spec/caliper/v1p2#SearchResponse) entity can be employed to describe the [Query](https://www.imsglobal.org/spec/caliper/v1p2#Query) submitted by a user as well as any <code>searchResults</code> returned as a result of the search.
#### Profile Description

See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.10](https://www.imsglobal.org/spec/caliper/v1p2#profile-search).

#### Event Conformance Table

| Event                                                                               | Action                                                                        | Actor                                                                     | Object                                                                                      | Recommended Generated Entity | Required or Optional |
| ------                                                                              | ------                                                                        | ------                                                                    | ------                                                                                      | ------                       | ------               |
| [SearchEvent](https://www.imsglobal.org/spec/caliper/v1p2#SearchEvent) |                                                                               |                                                                           |                                                                                             |                              |                      |
|                                                                                     | [Searched](https://www.imsglobal.org/spec/caliper/v1p2#searched) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) |                              | **Required**         |



### <a name="sessionProfile"></a>3.12 Session Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Session Profile" src="../assets/caliper-profile_session.png"></div>

The Caliper Session Profile models the creation and subsequent termination of a user session established by a [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) interacting with a [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication).

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.11](https://www.imsglobal.org/spec/caliper/v1p2#profile-session).

#### Event Conformance Table

| Event                                                                                 | Action                                                                          | Actor                                                                                               | Object                                                                                              | Recommended Generated Entity | Required or Optional |
| ------                                                                                | ------                                                                          | ------                                                                                              | ------                                                                                              | ------                       | ------               |
| [SessionEvent](https://www.imsglobal.org/spec/caliper/v1p2#SessionEvent) |                                                                                 |                                                                                                     |                                                                                                     |                              |                      |
|                                                                                       | [LoggedIn](https://www.imsglobal.org/spec/caliper/v1p2#loggedIn)   | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person)                           | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | **Required**         |
|                                                                                       | [LoggedOut](https://www.imsglobal.org/spec/caliper/v1p2#loggedOut) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person)                           | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | Optional             |
|                                                                                       | [TimedOut](https://www.imsglobal.org/spec/caliper/v1p2#timedOut)   | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) | [Session](https://www.imsglobal.org/spec/caliper/v1p2#session)                         |                              | Optional             |


### <a name="surveyProfile"></a>3.13 Survey Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Survey Profile" src="../assets/caliper-profile_survey.png"></div>

The Caliper Survey Profile provides a vocabulary for describing events associated with a respondent's participation in online surveys. A key use case involves instrumenting platforms that provide online surveys that explore the student learning experience, student engagement, learning activities, learning progress, and learning performance. The profile models a [Person](https://www.imsglobal.org/spec/caliper/v1p2#Person), typically a respondent or a rater, participating in a survey in order to provide feedback on their learning and academic experiences.

#### Profile Description

See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.12](https://www.imsglobal.org/spec/caliper/v1p2#profile-survey).

#### Event Conformance Table

| Event                                                                                                     | Action                                                                              | Actor                                                                     | Object                                                                                          | Recommended Generated Entity                                                  | Required or Optional |
| ------                                                                                                    | ------                                                                              | ------                                                                    | ------                                                                                          | ------                                                                        | ------               |
| [SurveyInvitationEvent](https://www.imsglobal.org/spec/caliper/v1p2#SurveyInvitationEvent)   |                                                                                     |                                                                           |                                                                                                 |                                                                               |                      |
|                                                                                                           | [Accepted](https://www.imsglobal.org/spec/caliper/v1p2#accepted)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [SurveyInvitation](https://www.imsglobal.org/spec/caliper/v1p2#SurveyInvitation)   |                                                                               | Optional             |
|                                                                                                           | [Declined](https://www.imsglobal.org/spec/caliper/v1p2#declined)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [SurveyInvitation](https://www.imsglobal.org/spec/caliper/v1p2#SurveyInvitation)   |                                                                               | Optional             |
|                                                                                                           | [Sent](https://www.imsglobal.org/spec/caliper/v1p2#sent)               | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [SurveyInvitation](https://www.imsglobal.org/spec/caliper/v1p2#SurveyInvitation)   |                                                                               | Optional             |
| [SurveyEvent](https://www.imsglobal.org/spec/caliper/v1p2#SurveyEvent)                       |                                                                                     |                                                                           |                                                                                                 |                                                                               |                      |
|                                                                                                           | [OptedIn](https://www.imsglobal.org/spec/caliper/v1p2#optedIn)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Survey](https://www.imsglobal.org/spec/caliper/v1p2#survey)                       |                                                                               | Optional             |
|                                                                                                           | [OptedOut](https://www.imsglobal.org/spec/caliper/v1p2#optedOut)       | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Survey](https://www.imsglobal.org/spec/caliper/v1p2#survey)                       |                                                                               | Optional             |
| [QuestionnaireEvent](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireEvent)         |                                                                                     |                                                                           |                                                                                                 |                                                                               |                      |
|                                                                                                           | [Started](https://www.imsglobal.org/spec/caliper/v1p2#started)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Questionnaire](https://www.imsglobal.org/spec/caliper/v1p2#questionnaire)         | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
|                                                                                                           | [Submitted](https://www.imsglobal.org/spec/caliper/v1p2#submitted)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Questionnaire](https://www.imsglobal.org/spec/caliper/v1p2#questionnaire)         | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | **Required**         |
| [QuestionnaireItemEvent](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireItemEvent) |                                                                                     |                                                                           |                                                                                                 |                                                                               |                      |
|                                                                                                           | [Completed](https://www.imsglobal.org/spec/caliper/v1p2#completed)     | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [QuestionnaireItem](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireItem) | [Response](https://www.imsglobal.org/spec/caliper/v1p2#response) | Optional             |
|                                                                                                           | [Skipped](https://www.imsglobal.org/spec/caliper/v1p2#skipped)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [QuestionnaireItem](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireItem) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
|                                                                                                           | [Started](https://www.imsglobal.org/spec/caliper/v1p2#started)         | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [QuestionnaireItem](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireItem) | [Attempt](https://www.imsglobal.org/spec/caliper/v1p2#attempt)   | Optional             |
| [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent)               |                                                                                     |                                                                           |                                                                                                 |                                                                               |                      |
|                                                                                                           | [NavigatedTo](https://www.imsglobal.org/spec/caliper/v1p2#action-navigatedTo) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Questionnaire](https://www.imsglobal.org/spec/caliper/v1p2#questionnaire)         |                                                                               | Optional             |
| [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)                           |                                                                                     |                                                                           |                                                                                                 |                                                                               |                      |
|                                                                                                           | [Viewed](https://www.imsglobal.org/spec/caliper/v1p2#viewed)           | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [Questionnaire](https://www.imsglobal.org/spec/caliper/v1p2#questionnaire)         |                                                                               | Optional             |


### <a name="toolLaunchProfile"></a>3.14 Tool launch Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Tool Launch Profile" src="../assets/caliper-profile_tool_launch.png"></div>

The Caliper Tool Launch Profile is intended to capture the utilization of learning tools from a centralized location, such as an LTI Tool Platform (often an LMS). As such, it is distinct from the Caliper [Tool Use Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-toollaunch), also defined in this specification, which captures tool usage as reported by the individual tools themselves (i.e. decentralized capture).

#### Profile Description

See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.13](https://www.imsglobal.org/spec/caliper/v1p2#profile-toollaunch).

#### Event Conformance Table

| Event                                                                                       | Action                                                                        | Actor                                                                     | Object                                                                                              | Recommended Generated Entity | Required or Optional |
| ------                                                                                      | ------                                                                        | ------                                                                    | ------                                                                                              | ------                       | ------               |
| [ToolLaunchEvent](https://www.imsglobal.org/spec/caliper/v1p2#ToolLaunchEvent) |                                                                               |                                                                           |                                                                                                     |                              |                      |
|                                                                                             | [Launched](https://www.imsglobal.org/spec/caliper/v1p2#launched) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | **Required**         |
|                                                                                             | [Returned](https://www.imsglobal.org/spec/caliper/v1p2#returned) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | Optional             |


### <a name="toolUseProfile"></a>3.15 Tool Use Profile

<div style="design: block;margin: 0 auto"><img class="img-responsive" alt="Tool Use Profile" src="../assets/caliper-profile_tool_use.png"></div>

The Caliper Tool Use Profile models an intended interaction between a user and a tool.

#### Profile Description
See *Caliper Analytics&reg; Specification*, version 1.2, [Section 3.14](https://www.imsglobal.org/spec/caliper/v1p2#profile-tooluse).

#### Event Conformance Table

| Event                                                                                 | Action                                                                | Actor                                                                     | Object                                                                                              | Recommended Generated Entity | Required or Optional |
| ------                                                                                | ------                                                                | ------                                                                    | ------                                                                                              | ------                       | ------               |
| [ToolUseEvent](https://www.imsglobal.org/spec/caliper/v1p2#ToolUseEvent) |                                                                       |                                                                           |                                                                                                     |                              |                      |
|                                                                                       | [Used](https://www.imsglobal.org/spec/caliper/v1p2#used) | [Person](https://www.imsglobal.org/spec/caliper/v1p2#person) | [SoftwareApplication](https://www.imsglobal.org/spec/caliper/v1p2#SoftwareApplication) |                              | **Required**         |


## <a name="transportConformance"></a>Transport Conformance

A Caliper [Sensor](https://www.imsglobal.org/spec/caliper/v1p2#sensor) MUST demonstrate that it is capable of transmitting Caliper data successfully to the certification service [Endpoint](https://www.imsglobal.org/spec/caliper/v1p2#endpoint).  Certification is limited to message exchanges using the Hypertext Transport Protocol (HTTP) with the connection encrypted with Transport Layer Security (TLS).  Messages MUST be sent using the POST request method.  For certification purposes, the [Sensor](https://www.imsglobal.org/spec/caliper/v1p2#sensor) MUST also support message authentication using the <code>Authorization</code> request header, setting the value to the provided bearer token.

See the [IMS Security Framework documentation](https://www.imsglobal.org/ims-security-framework) for more information on security best practices.

#### <a name="envelope"></a>The Envelope
Caliper [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) and [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) data are transmitted inside an [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope), a JSON data structure that includes metadata about the emitting [Sensor](https://www.imsglobal.org/spec/caliper/v1p2#sensor) and the data payload.  Each [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) and [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) _[describe](https://www.imsglobal.org/spec/caliper/v1p2#describeDef)_ included in an envelope's <code>data</code> array MUST be expressed as a [JSON-LD](https://www.imsglobal.org/spec/caliper/v1p2#serialization) document.

For example [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope) JSON-LD see *Caliper Analytics&reg; Specification*, version 1.2, [Section 5.3](https://www.imsglobal.org/spec/caliper/v1p2#jsonldPayload).

#### <a name="httpRequest"></a>HTTP Message Requests
Each HTTP request message sent to the certification service MUST consist of a single serialized JSON representation of a Caliper [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope).  Messages MUST be sent using the POST request method.

The following standard HTTP request headers MUST be set for each message sent to the certification service [Endpoint](https://www.imsglobal.org/spec/caliper/v1p2#endpoint):

| Request Header | Disposition |
| :------------- | :----------- |
| Authorization | Set the <code>Bearer</code> token provided by the certification service and associated with the test endpoint. For example: <code>Authorization: Bearer 2YotnFZFEjr1zCsicMWpAA</code> |
| Content-Type | Set the string value to the IANA media type <code>application/json</code>. |
| Host | Set the string value to the test endpoint URL provided by the certification service. |

#### <a name="httpResponse"></a>HTTP Message Responses

Following receipt of a [Sensor](https://www.imsglobal.org/spec/caliper/v1p2#sensor) request message the certification service will reply with a response message.  The response will include a three-digit status code indicating whether or not the certification service was able to understand and satisfy the request as defined by [[RFC7231]].

* To signal a Caliper sensor that it has successfully received a message the certification service endpoint will reply with a <code>2xx</code> class status code.  The body of a successful response will be empty.
* If a Caliper sensor sends a message containing events and or entities without an enclosing [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope), the certification service will reply with a <code>400 Bad Request</code> response.
* If a Caliper sensor sends a malformed Caliper envelope (it does not contain <code>sensor</code>, <code>sendTime</code>, <code>dataVersion</code> and <code>data</code> properties of the required form), the certification service will reply with a <code>400 Bad Request</code> response.
* If a Caliper sensor sends a message without an <code>Authorization</code> request header of the REQUIRED form or sends a token credential that the certification service is unable to either validate or determine has sufficient privileges to submit Caliper data, the certification service will reply with a <code>401 Unauthorized</code> response.
* If a Caliper sensor sends a message with a <code>Content-Type</code> other than "application/json", the certification service will reply with a <code>415 Unsupported Media Type</code> response.
* If a Caliper sensor sends a message with an [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope) that contains a <code>dataVersion</code> value that the endpoint cannot support the certification service will reply with a <code>422 Unprocessable Entity</code> response.

The certification service MAY respond to [Sensor](https://www.imsglobal.org/spec/caliper/v1p2#sensor) messages with other standard HTTP status codes to indicate result dispositions that vary from the cases described above.  The certification service MAY also communicate more detailed information about problem states, using the standard method for reporting problem details described in [[RFC7807]].

#### <a name="otherTransports"></a>Other Transport Protocols
*Caliper Analytics&reg; Specification*, [version 1.2](https://www.imsglobal.org/spec/caliper/v1p2) defines the use of a single transport protocol (HTTP/HTTPS).  However, IMS Global is interested in specifying the use of other transport protocols that can support the exchange of Caliper data.  Organizations wishing to work with IMS Global to add other transport protocols to the Caliper specification should contact the Caliper Working Group directly or indicate interest via the [public forum](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum).

<section class="appendix informative" id="references">
## <a name="references"></a>References
<a name="caliperSpec"></a>__Caliper Spec__.  IMS Global.  Anthony Whyte, Viktor Haag, Linda Feng, Markus Gylling, Matt Ashbourne, Wes LaMarche and Etienne Pelaprat.  Caliper Analytics® Specification, version 1.2.  12 January 2018.  URL: http://www.imsglobal.org/caliper-spec-v1p2

<a name="jsonldSyntax"></a>__JSON-LD Syntax__.  W3C.  M. Sporny, D. Longley, G. Kellog, M. Lanthaler and N. Lindström.  JSON-LD 1.1.  A JSON-based Serialization for Linked Data. 15 February 2017.  URL: http://json-ld.org/spec/latest/json-ld/

<a name="jsonldProcessing"></a>__JSON-LD Processing__.  D. Longley, G. Kellog, M. Lanthaler, M. Sporny.  JSON-LD 1.1 Processing Algorithms and API.  15 February 2017.  URL: http://json-ld.org/spec/latest/json-ld-api/

<a name="linkedData"></a>__Linked Data__.  Tim Berners-Lee.  "Linked Data."  W3C internal document.  July 2006, rev. June 2009.  URL: https://www.w3.org/DesignIssues/LinkedData.html

</section>

<section class="appendix informative" id="aboutthisdocument">
## <a name="aboutThisDoc"></a>About this Document
IMS Global Learning Consortium, Inc. ("IMS Global") is publishing the information contained in this document ("Guide") for purposes of scientific, experimental, and scholarly collaboration only.

IMS Global makes no warranty or representation regarding the accuracy or completeness of the Guide.

This material is provided on an "As Is" and "As Available" basis.

The Guide is at all times subject to change and revision without notice.

It is your sole responsibility to evaluate the usefulness, accuracy, and completeness of the Guide as it relates to you.

IMS Global would appreciate receiving your comments and suggestions.

Please contact IMS Global through our website at [http://www.imsglobal.org](http://www.imsglobal.org).

Please refer to Document Name: IMS Caliper Analytics&reg; Certification Guide, version 1.2

Date: 5 December 2019

This document contains trademarks of the IMS Global Learning Consortium including the IMS Logos, Learning Tools Interoperability&reg; (LTI&reg;), Accessible Portable Item Protocol&reg; (APIP&reg;), Question and Test Interoperability&reg; (QTI&reg;), Common Cartridge&reg; (CC&reg;), AccessForAll&trade;, OneRoster&reg;, Caliper Analytics&reg; and SensorAPI&trade;. For more information on the IMS trademark usage policy see trademark policy page - https://www.imsglobal.org/trademarks


</section>


<section class="appendix informative" id="revisionhistory">
## Revision History

| Release Date  | Comments                |
|---------------|-------------------------|
| 21 October, 2020 | Base Document Release |
| 27 March, 2020 | Candidate Final Release |

</section>

`;