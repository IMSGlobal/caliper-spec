var t2 = `


## Abstract

IMS Caliper Analytics&reg; is a technical specification that describes a structured set of vocabulary that assists institutions in collecting learning and usage data from digital resources and learning tools. This data can be used to present information to students, instructors, advisers, and administrators in in order to drive effective decision making to improve learner success.  **TODO: improve section**

Caliper can help to answer various questions about learner activity, a few examples questions that Caliper might help answer.

* How often is a learner logging in to view their digital resources?
* Are learners interacting with a forum post?
* How often is a learner consuming course readings or videos?
* What activities is a learner interacting with while taking an assessment?
* Are learners annotating certain digital resources?
* **TODO add better/more examples of how Caliper can be Used/link to Use Cases Section**

With the answers to these questions in tow, decision makers can drive analysis that answers critical questions such as:

* Is there a performance difference between learners who interact with a certain digital resource versus learners who do not?

The sky is the limit with the ways to use Caliper data to measurably improve the learning ecosystem.

## Introduction

### What is this document?

This document is an informative part of the
[Caliper Analytics <sup>&copy;</sup> 1.2 document set](https://www.imsglobal.org/example/v1p1/#document-set).
As such, it may be revised without the specification version being incremented.
Please refer to the [revision history](#revision-history) below for more information
about revisions to this document.

As an informative resource it does not include any normative requirements. Occurrences in this document of terms such as MAY, MUST, MUST NOT, SHOULD or RECOMMENDED have no impact on the conformance criteria for implementors of this specification.

The primary goal of this document is to lead you to successful implementation of the Caliper Analytics&reg; v1.2 specification. More than that, this guide helps you along the way to achieving conformance certification.

### How to use this document

This document is intended as a starting point for those looking to implement the Caliper Analytics&reg; standard in their educational software ecosystem.

* Developers can use this document to review specific examples of caliper events and explanations of best practices aligned with the transmitting and collecting of Caliper Analytics&reg; events.
* Product managers can use this document and it's best practices while building out a product plan/roadmap as well as determining the best Caliper Metric Profiles to be used to capture or transmit the information relevant to the questions they are attempting to answer.


To review the use case collection that drove the development of this specification,
please refer to [the use cases section](https://www.imsglobal.org/example/v1p1/#use-cases) **This is a dead link - JWM.**.

## Terminology

Learning this vocabulary in the context of the Caliper specification will be very helpful when using this document.  Caliper Analytics describes events using triples, a combination of an *action* being undertaken by an *actor* to an *object*.  A good way to think of it as *someone* (*actor*) did *something* (*action*) to *someone/something* (*object*)

Here are a few useful definitions for terms used throughout this document.  Full Caliper terminology list is available in the [Terminology section of the Caliper Spec](https://www.imsglobal.org/sites/default/files/caliper/v1p1/caliper-spec-v1p1/caliper-spec-v1p1.html#terminology).

<dl>
  <dt>Action</dt><dd>Part of an Event that describes the *what* .</dd>
  <dt>Actor</dt><dd>Part of an Event that describes the *who*.</dd>
  <dt>Entity</dt><dd>Part of an Event that describes the *to whom*.</dd>
  <dt>Agent</dt><dd>Part of an Event that represents a generic form of an *Entity* and describes the *to whom* when a more specific *Entity* is not available.</dd>
  <dt>Event</dt><dd>A collection of an Actor, an Action, and an Object</dd>
  <dt>Envelope</dt><dd>A JSON payload that can contain one ore many Caliper events</dd>
  <dt>Object</dt><dd>Part of an Event that describes the *to whom*.</dd>
  <dt>Metric Profile</dt><dd>Groupings of Caliper vocabulary that model a learning activity or a supporting activity. Each Metric Profile provides a domain-specific set of terms and concepts that application designers and developers can draw upon to describe common user interactions in a consistent manner.  Metric Profiles also serve as the unit of certification for the Caliper Analytics&reg; specification </dd>
  <dt>Sensor</dt><dd> Software deployed within a learning application that capture and transmit Caliper data to a target endpoint</dd>
  <dt></dt><dd></dd>
</dl>

Here is a short explanation of how Caliper works using this vocabulary. If you can understand this you're well on your way to understanding Caliper!

When a Caliper-observable interaction, as defined by a _Metric Profile_, is detected by a _Sensor_, an _Event_ is created which consists of an _Actor_, an _Object_, and an _Action_. (The Actor did the Action to the Object) To emit an _Event_ to another system via an API call, it is described as a JSON object which is wrapped in an _Envelope_ with a little metadata about the _Sensor_. The JSON is then sent via a secured HTTP call with an authentication token in an HTTP header.

### Links for your convenience

- [Caliper Analytics&reg; Public Forums](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum)
- [Caliper Analytics&reg; version 1.1 full specification](https://www.imsglobal.org/sites/default/files/caliper/v1p1/caliper-spec-v1p1/caliper-spec-v1p1.html)
- [Metric Profile Summaries](https://www.imsglobal.org/caliper-analytics-v11-profiles-summaries)
- [Caliper Analytics&reg; Conformance Information](https://www.imsglobal.org/caliper-analytics-conformance)
- [Caliper Analytics&reg; Conformance Test Suite](https://caliper.imsglobal.org/sec/index.html)
- [Caliper-central GitHub Repository](https://github.com/IMSGlobal/caliper-central)
- [How to use with LTI](https://github.com/IMSGlobal/LTI-spec-Caliper/blob/master/docs/lti-spec-caliper.md)

## Conformance Certification

IMS offers a process for testing the conformance of products using the IMS certification test suite. Certification designates passing a set of tests that verify the standard has been implemented correctly and guarantees a product’s interoperability across hundreds of other certified products. The Caliper Analytics Conformance Certification Guide [[CERTGUIDE URL]] provides details on about the testing process, requirements, and how to get started.

Conformance certification offers more than claims of “compliance,". The only way IMS can guarantee interoperability is by obtaining certification for the latest version of the standard. Only products listed in the official IMS Certified Product Directory can claim conformance certification. IMS certification provides the assurance that a solution will integrate securely and seamlessly into an institution's digital learning ecosystem.

Certification for Caliper Analytics involves certifying against one or more Metric Profiles.

 **TODO**: Should it reference how extension conformance works or leave that to a different section?


## How to create a Caliper Event

### Events

[Link to full Event docs](#events)

An Event is the combination of an *Actor*, an *Action*, and an *Object*. In a sentence, an Event describes what an Actor _did_ (Action) to an Object. Each of those will be described in the following sections.

It's important to have a clear understanding of Caliper Events since they describe the semantics of what's happening in the system.


#### Event Types

TODO: EventType....

[AnnotationEvent](#annotationEvent), [AssignableEvent](#assignableEvent), [AssessmentEvent](#assessmentEvent), [AssessmentItemEvent](#assessmentItemEvent), [ForumEvent](#forumEvent), [MediaEvent](#mediaEvent), [MessageEvent](#messageEvent), [NavigationEvent](#navigationEvent), [GradeEvent](#gradeEvent), [SessionEvent](#sessionEvent), [ToolUseEvent](#toolUseEvent), [ThreadEvent](#threadEvent), [ViewEvent](#viewEvent)

#### Event Required Properties

[Link to full Event Properties docs section](#event Properties)

TODO?? Simplify these descriptions since the full technical version is in the docs.


| Property | Type | Description | Disposition |
| :------- | :--- | ----------- | :---------: |
| id | [UUID](#uuidDef) | A version 4 [UUID](#uuidDef).  The UUID MUST be expressed as a [URN](#urnDef) using the form `urn:uuid:<UUID>` per [RFC 4122](#rfc4122). | Required |
| type | [Term](#termDef) | A string value for the Event Sub Type, or for a generic [Event](#event) set the `type` to the string value `Event`. | Required |
| actor | [Agent](#agent) &#124; [IRI](#iriDef) | The [Agent](#agent) who initiated the [Event](#event), typically though not always a [Person](#person).  The `actor` value MUST be expressed either as an object or as a string corresponding to the actor's [IRI](#iriDef). | Required |
| action | [Term](#termDef) | The action or predicate that binds the actor or subject to the object.  The `action` range is limited to the set of [actions](#actions) described in this specification and may be further constrained by the chosen [Event](#event) type.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [Entity](#entity) &#124; [IRI](#iriDef) | The [Entity](#entity) that comprises the object of the interaction.  The `object` value MUST be expressed either as an object or as a string corresponding to the object's [IRI](#iriDef). | Required |
| eventTime | DateTime | An ISO 8601 date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred.  The value MUST be expressed using the format YYYY-MM-DDTHH:mm:ss.SSSZ set to UTC with no offset specified. | Required |

#### Other Event Properties

TODO: talk about profiles defining more properties both required and optional.

#### Event JSON stub

```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:3a648e68-f00d-4c08-aa59-8738e1884f2c",
  "type": "ViewEvent",
  "eventTime": "2018-11-15T10:15:00.000Z",
  "actor": {},
  "action": "",
  "object": {}
}
```

### Actors

[Link to full Actor docs](#actors)

TODO: Explain Actors and their basic properties then link to main spec document where appropriate for more details.

#### Actor JSON

```json
{
  "id": "https://example.edu/users/554433",
  "type": "Person"
}
```

### Action

[Link to full Action docs](#actions)

TODO: Explain Actions and their basic properties then link to main spec document where appropriate for more details.

#### Action JSON

```json
"Viewed"
```

### Object

[Link to full Object docs](#objects)

TODO: Explain Objects and their basic properties then link to main spec document where appropriate for more details.

#### Object JSON

```json
{
  "id": "https://example.edu/terms/201801/courses/7/sections/1/readings/1",
  "type": "DigitalResource",
  "name": "Chapter 1 reading"
}
```

### Complete Event Example JSON

To bring it all together, and Event would look something like this:

TODO: Explain how to find sample JSON for their specific event/action/profile by pointing to docs and fixtures, etc. Since we can't put every example in this document, teach how to find examples they need. (This might be worthy of it's own top-level section just for discoverability. Coming to this doc to find example JSON will be one of the primary activities for developers)

#### Complete JSON

```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:a2f41f9c-d57d-4400-b3fe-716b9026334e",
  "type": "ViewEvent",
  "eventTime": "2018-11-15T10:16:00.000Z",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Viewed",
  "object": {
    "id": "https://example.edu/terms/201801/courses/7/sections/1/readings/1",
    "type": "DigitalResource",
    "name": "Chapter 1 reading"
  }
}
```

This Event is read as something like: "This Person Viewed this DigitalResource at this eventTime"

#### Smaller, ID-Only JSON

TODO: Short explanation about using ID only (or "Type Coercion") instead of full object and then _link_ to more in-depth explanations around proper use. Maybe make a best practice section about when you should generally use object vs just ID and how it needs to be agreed upon between the parties so that they remain interoperable?

```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:a2f41f9c-d57d-4400-b3fe-716b9026334e",
  "type": "ForumEvent",
  "eventTime": "2018-11-15T10:16:00.000Z",
  "actor": "https://example.edu/users/554433",
  "action": "Subscribed",
  "object": "https://example.edu/terms/201801/courses/7/sections/1/forums/1"
}
```

### Additional properties on Events

While the base information required by most Events is represented in the above example, each Event type could require more properties, and allow for more properties and context as desired by the implementors. To understand what information is required and possible you should consult the Metric Profiles for the activities you're trying to implement.

## Metric Profiles

[Link to full Metric Profile docs](#profiles)

TODO: Profiles are so amazing! Here's why: TODO
TODO: How to use profile documents

TODO: Table with all profiles and links to their documentations and their certification requirements in the certification guide

###

A great way to think of a Metric Profile is by the questions it can help answer. For example the Reading Profile could help Instructors and researchers answer questions such as:

 - Who is consuming the content?
 - What materials are being accessed?
 - When are the resources accessed?
 - How often is the content viewed?
 - What paths are taken to reach the content?


TODO: Talk about how `@context` changes for extensions and explain how it works? Then point to the Release Schedule section.

TODO: Emphasize this is the level of certification. That's possibly also discussed in the Certification header above, and possibly in the release schedule stuff below. Maybe the repetition is good since this is an important point to understand.


## Custom Extensions

TODO: how to do this. Don't know where best to put this section. Might be mostly pointing to other JSON-LD resources.


## Sending an Event to an endpoint

### Envelopes

TODO: Talk about Envelopes and give example. (are Envelopes best discussed in a different section?)

An Envelope must have the properties

#### Base Envelope JSON

```json
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2018-11-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": [ {event1}, {event2}, {eventN}]
}
```

TODO: Talk about what can be in data: just an event, multiple events, or even mixed payloads of objects and events.

#### Envelope with an Event JSON

```json
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2018-11-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": [{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "urn:uuid:7e10e4f3-a0d8-4430-95bd-783ffae4d916",
    "type": "ToolUseEvent",
    "eventTime": "2018-11-15T10:15:00.000Z",
    "actor": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "action": "Used",
    "object": {
      "id": "https://example.edu",
      "type": "SoftwareApplication"
    }
  }]
}
```

#### Mixed payload Envelope JSON

In this example, the Person and SoftwareApplication are part of the data array and referenced from the events for reuse.

```json
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2018-11-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": [
   {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "https://example.edu/users/554433",
    "type": "Person",
    "dateCreated": "2018-08-01T06:00:00.000Z",
    "dateModified": "2018-09-02T11:30:00.000Z"
  },
  {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "urn:uuid:7e10e4f3-a0d8-4430-95bd-783ffae4d916",
    "type": "ToolUseEvent",
    "eventTime": "2018-11-15T10:15:00.000Z",
    "actor": "https://example.edu/users/554433",
    "action": "Used",
    "object": "https://example.edu"
  },
  {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "urn:uuid:9r34jdfj-a0d8-4430-95bd-783ffae4d916",
    "type": "ToolUseEvent",
    "eventTime": "2018-11-15T11:15:00.000Z",
    "actor": "https://example.edu/users/554433",
    "action": "Used",
    "object": "https://example.edu"
  }
  ]
}
```



### Sending to a secured HTTP endpoint

TODO: Short description of how it's done then link to the LTI service definition: https://github.com/IMSGlobal/LTI-spec-Caliper/blob/develop/lti-spec-caliper.md#23-communicating-the-availability-of-the-service

TODO: Also explain how 2 vendors can work out keys and endpoints independent of LTI.


## Receiving Caliper Events

TODO: Talk about LRS/LRW? Talk about validating events and doing something with them right away vs throwing into a bucket super fast for later analysis?

TODO: Talk about auth header check

TODO: Talk about credentials? Or just reference the LTI doc again?


## Release Schedule Expectations

- Core specification to be released at most once a year
  - new base context is updated

- Profiles can be extended during year
 - profile is described in core
 - and might be extensions
 - manifested in JSON as a different @context string by adding `-extension`

- Talk about how upgrades happen for both sides. Should receiver of events try to understand all previous versions of a profile? Explain everything needed to understand the scope of implementing upgraded core versions and profiles.


## Code Libraries, Examples, and Test Servers

- talk about the sensor libraries and their maintenance
- examples of usage for emitting and consuming
- if there is one, point to testing endpoint for development


## Use Cases

### Value Statement

 As the online educational ecosystem grows, it becomes increasingly important to be able to measure the efficacy of tools and programs with the ultimate goal of improving learner successes.  To that end, the industry has embraced the need for "Big Data" analytics to drive insight.  Caliper Analytics&reg; structured, standards based approach provides a strong foundation for both providers and consumers of learning analytics data to make better decisions based off of a shared curated vocabulary. Caliper Analytics&reg; provides the necessary alignment and structure to what is and should be measured, along with a framework to support the capture and marshaling of data,

### Understanding learner interactions across vendor tools

An instructor, seeking to augment the classroom environment for her learners, utilizes a video platform to create and post video assignments. Class discussions and Q&A sessions are conducted online using another service and she administers her course using a learning management system. These three services are provided by three vendors, three potential sources of learning data. Analyzing the interaction behaviors of her students in relation to the questions they pose about her course content is vital to understanding student comprehension and performance. Caliper allows the collection of learning data and addresses important issues such as who owns the data, managing privacy requirements, and bringing together data from diverse systems to analyze.

### Understanding licensed value

Using the same Caliper data being collected at the course level in the prior scenario, but at the cohort or system level, can be leveraged to determine in aggregate how much usage a licensed tool is getting across a cohort or within a segment of students. This data could be used to determine when it is safe to perform upgrades when it is time to begin migration planning or other operational concerns with various learning tools

### Profile Use Cases

Caliper Metric profiles represent foundational usage cases.  Each Metric Profile has it's own subset of use cases listed in it's primary specification document as linked to in this document.

- TODO: Find some demonstrative use cases and explain how they'd be solved by talking through what questions they want answered, then what Metric Profiles and Events are needed to answer them.

Make sure to get a use case that decides why and how to add custom extensions.

Need to add use cases for all action types for each profile ( request from issue #196)

### Best Practices

TODO: talk with current implementors and ask what best practices they'd suggest.

### Tool Provider perspective LTI launch.
- Tool Providers should use the federated session ID as the `id` of the federatedSession entity you include in events
- Tool Providers should pick out the system identifiers from the LTI message that are relevant to you as a Tool, and put them in as `SystemIdentifiers` on the _entities_ in your events that are relevant. This helps
  - Bind identifiers to the items they belong to, and not to the _session_
  - Helps data consumers easily find those properties rather than having to dig through a big bag of `Event.federatedSession.messageProperties` keys.

With some platforms the identifier might be the "user's login session"; in other platforms, it might be "just the individual launch".

Receivers of events should/could expect that they'd get single def'ns of dimensional data to keep the event stream lean -- like an endpoint could get raw Entity "describes" in the event stream, or they might get a full object for a User at the "beginning" of a report of 100s of events of activity, and then only the Person's "id" IRI in the following events...

### Sending full objects vs just the ID/IRI

TODO: We should probably suggest in the implementation guide that receivers of events should|could expect that they'd get single def'ns of dimensional data to keep the event stream lean -- like an endpoint could get raw Entity "describes" in the event stream, or they might get a full object for a User at the "beginning" of a report of 100s of events of activity, and then only the Person's "id" IRI in the following events...

TODO: This should be merged with the next item in list

### Deciding what and how much data to send in events

- Data generated by the app which would otherwise be lost (i.e. not persisted) is a good candidate to convey in a Caliper event.
- Data that is readily accessible via dereferenceble IRI's, it is OK to include just the IRI's.
- If there are cases where downstream processes would need quick access to the actual generated data, it is ok to include those data values as well.
- It can be good to only emit what you generate: in other words, if your application has to do any extra work to retrieve related information, it's not recommended to include it in the event payload.


### LTI Sessions and Identifiers

TODO: Link to the "Learning Tools Interoperability® (LTI) Caliper Analytics® Endpoint Service Specification, version 1.0" spec when it's published somewhere.

#### Federated session ID

TODO: Link to the official spec section for this when it exists: https://github.com/IMSGlobal/caliper-spec/blob/develop/caliper-spec.md#ltiSession

When receiving an LTI Launch use the `caliper_federated_session_id` as the `id` of the `LtiSession` you include in events:

```json
 {
   "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
   "type": "LtiSession"
 }
```

You add it to an event using the `federatedSession` key:

```json
 {
   "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
   "id": "urn:uuid:9r34jdfj-a0d8-4430-95bd-783ffae4d916",
   "type": "ToolUseEvent",
   "eventTime": "2018-11-15T11:15:00.000Z",
   "actor": "https://example.edu/users/554433",
   "action": "Used",
   "object": "https://example.edu",
   "federatedSession": {
     "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
     "type": "LtiSession"
   }
 }
```

#### Other IDs and launch information

There is a lot of other information that can be passed along with an LTI Launch. Here are some guidelines to consider when deciding what information to include with your Caliper events:

- pick out the system identifiers from the LTI message that are relevant to you as a Tool, and put them in as SystemIdentifiers on the _entities_ in your events that are relevant.
 - This helps (a) bind those identifiers to the things they belong to, and not to the "session", and
 - (b) helps data consumers easily find those properties rather than having to dig through a big bag of `Event.federatedSession.messageProperties` keys.
 - TODO: Link to the area of the spec for how to add other identifiers to objects
 - Any identifiers generated by your app should be represented as first class properties in the Caliper event; however any identifiers which were passed into your application (say as LTI launch parameters) should be included as federatedSession properties.

You might want to capture the `messageParameters` from an LTI launch message and include those in the federated session property, but the message bodies are quite large, and you should prefer to rely in the federated session ID to retrieve any needed information unless you have a specific purpose for including all that information.

Here is an example of adding extra LTI information into the `LtiSession` object:

```json
{
   "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
   "type": "LtiSession",
   "user": "https://example.edu/users/554433",
   "messageParameters": {
     "lti_message_type": "basic-lti-launch-request",
     "lti_version": "LTI-2p0",
     "context_id": "4f1a161f-59c3-43e5-be37-445ad09e3f76",
     "context_type": "CourseSection",
     "resource_link_id": "6b37a950-42c9-4117-8f4f-03e6e5c88d24",
     "roles": [ "Learner" ],
     "user_id": "0ae836b9-7fc9-4060-006f-27b2066ac545",
     "custom": {
       "caliper_session_id": "1c519ff7-3dfa-4764-be48-d2fb35a2925a",
       "tool_consumer_instance_url": "https://example.edu"
     },
     "ext": {
       "edu_example_course_section": "https://example.edu/terms/201801/courses/7/sections/1",
       "edu_example_course_section_roster": "https://example.edu/terms/201801/courses/7/sections/1/rosters/1",
       "edu_example_course_section_learner": "https://example.edu/users/554433",
       "edu_example_course_section_instructor": "https://example.edu/faculty/1234"
     }
   },
   "dateCreated": "2018-11-15T10:15:00.000Z",
   "startedAtTime": "2018-11-15T10:15:00.000Z"
 }
```

### Robustness expectations

As an _analytics_ specification, Caliper is not generally well suited to other uses that require more robust guarantees around timeliness and completeness.

TODO: Notes of what to cover:
- Caliper is _not_ specified as a messaging or transaction service
- There are no guarantees around delivery timing
- Events in Caliper are _not_ ordered and may come much later, or in batches, etc.
- If two vendors need plan to use events as transaction they should work that out in their vendor agreements
- Other reasons why it might not be a good idea to rely on Caliper for user-facing production problems.
- Do _not_ rely on it for grades! Use: list other standards & services?
_ Do not rely on it for course and enrollment information. Use: list other standards & services?


### Industry Analytics and Data Retention Standards

TODO: Explain and link to industry best practices around ethics, data retention best practices and laws, and other stuff? I assume there are some good resources out there for researchers and IRB training.


### JSON-LD

[JSON-LD](https://www.w3.org/2018/jsonld-cg-reports/json-ld/) is a specification providing a JSON-based data serialization and messaging format, processing algorithms and API for working with Linked Data. The messages described in this specification are intended to be used in programming environments that support JSON-LD

TODO: How Caliper uses JSON-LD and links to Caliper docs for further learning if necessary


## List of Contributors
The following individuals contributed to the development of this document:

| Contributor | Affiliation |
| :---------- | :---------- |
| Anthony Whyte | University of Michigan |
| Viktor Haag | D2L |
| Linda Feng | Unicon |
| Oxana Jurosevic | Instructure |
| Bracken Mosbacker | IMS Global |
| Joshua McGhee | IMS Global |

## Revision History

Release Date | Comments
------------ | -------------
Never 12th, 2019 | The original release of the implementation guide
29 May, 2019 | Added desriptive text in intro, and profiles section

`;
