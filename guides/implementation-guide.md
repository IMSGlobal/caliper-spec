var t2 = `
## Overview

### What is this document?

This document is an informative part of the 
[Caliper 1.2 document set](https://www.imsglobal.org/example/v1p1/#document-set).
As such, it may be revised without the specification version being incremented.
Please refer to the [revision history](#revision-history) below for more information 
about revisions to this document. 

To review the use case collection that drove the development of this specification, 
please refer to [the use cases section](https://www.imsglobal.org/example/v1p1/#use-cases) 
in [[EXAMPLE10]].

### What is Caliper?

Caliper is a technical specification to help institutions collect learning and usage data from digital resources and learning tools. This can help you present this information to students, instructors, and advisers in meaningful ways.

Caliper defines a common vocabulary for what activities can be observed (via a "Sensor") and how those activities should be described in JSON. These JSON payloads can be sent to an endpoint via a secure HTTP request for processing or storage. 

Some examples of observable activities are how a learner interacts in a forum, while taking an assessment, or when consuming course readings and videos. 

### Links to documents for your convenience

Many documents will be referenced in this guide. Here are links that will be useful for finding help and further information.

- Public Forums
- Full Specification
- Profiles
- Certification stuff
- How to use with LTI document
- Others?


## Conformance

TODO: Talk about how conformance works and point to certification suite. 
 
 - Should it talk about profiles as central to conformance here? Or leave it to profile area? A little of both?
 - Should it reference how extension conformance works or leave that to a different section?


## Terminology

Learning this vocabulary in the context of the Caliper specification will be very helpful when using this document.

TODO: Add definitions, and Figure out what definitions to include here vs leaving to the full spec.

<dl>
  <dt>Action</dt><dd>Part of an Event.</dd>
  <dt>Actor</dt><dd>Part of an Event.</dd>
  <dt>Agent</dt><dd></dd>
  <dt>Entity</dt><dd></dd>
  <dt>Envelope</dt><dd></dd>
  <dt>Event</dt><dd>A collection of an Actor, an Action, and an Object</dd>
  <dt>Metric Profile</dt><dd></dd>
  <dt>Object</dt><dd>Part of an Event.</dd>
  <dt>Sensor</dt><dd></dd>
  <dt></dt><dd></dd>
</dl>

Here is a short explanation of how Caliper works using this vocabulary. If you can understand this you're well on your way to understanding Caliper!

When a Caliper-observable interaction, as defined by a _Metric Profile_, is detected by a _Sensor_, an _Event_ is created which consists of an _Actor_, an _Object_, and an _Action_. (The Actor did the Action to the Object) To emit an _Event_ to another system via an API call, it is described as a JSON object which is wrapped in an _Envelope_ with a little metadata about the _Sensor_. The JSON is then sent via a secured HTTP call with an authentication token in an HTTP header.


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

A great way to think of a Metric Profile is by the questions it can help answer. For example the Reading Profile could help Instructors and researchers answer questions such as:

 - Who is consuming the content?
 - What materials are being accessed?
 - When are the resources accessed?
 - How often is the content viewed?
 - What paths are taken to reach the content?
 

TODO: Talk about how `@context` changes for extensions and explain how it works? Then point to the Release Schedule section. 

TODO: Emphasise this is the level of certification. That's possibly also discussed in the Certification header above, and possibly in the release schedule stuff below. Maybe the repetition is good since this is an important point to understand.
 
 
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


## Release Schedule stuff

- Core spec once a year
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

TODO: Find some demonstrative use cases and explain how they'd be solved by talking through what questions they want answered, then what Metric Profiles and Events are needed to answer them.

Make sure to get a use case that decides why and how to add custom extensions.

Need to add use cases for all action types for each profile ( request from issue #196) 

## Best Practices 

TODO: talk with current implementors and ask what best practices they'd suggest.

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


### Deciding what and how much data to send in events

How much "actual" information should be included in Caliper events? On the one hand, if all objects are persisted and accessible via dereferencable IRIs, why not streamline all Caliper payloads to reference ids and timestamps only?

These guidelines might be useful to help application designers and researchers decide what data to send and collect.

- Data generated by the app which would otherwise be lost (i.e. not persisted) would be a good candidate to convey in a Caliper event.
- For data which is readily accessible via dereferenceble IRI's, it is OK to include just the IRI's.
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


### Sending full objects vs just the ID/IRI

TODO: We should probably suggest in the implementation guide that receivers of events should|could expect that they'd get single def'ns of dimensional data to keep the event stream lean -- like an endpoint could get raw Entity "describes" in the event stream, or they might get a full object for a User at the "beginning" of a report of 100s of events of activity, and then only the Person's "id" IRI in the following events...


### JSON-LD

TODO: The implementation guide probably doesn't need to dive very deeply into JSON-LD, so give some notes about what JSON-LD is and how Caliper uses it then links to Caliper docs and JSON-LD docs for further learning if necessary


## List of Contributors
The following individuals contributed to the development of this document:

| Contributor | Affiliation |
| :---------- | :---------- |
| Anthony Whyte | University of Michigan |
| Viktor Haag | D2L |
| Linda Feng | Unicon |
| Oxana Jurosevic | Instructure |
| Bracken Mosbacker | IMS Global |
        
## Revision History
      
Release Date | Comments
------------ | -------------
Never 12th, 2019 | The original release of the implementation guide

`;
