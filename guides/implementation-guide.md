var t2 = `


## Abstract

IMS Caliper Analytics&reg; is a technical specification that describes a structured set of vocabulary that assists institutions in collecting learning and usage data from digital resources and learning tools. This data can be used to present information to students, instructors, advisers, and administrators in order to drive effective decision making and promote learner success.

Caliper can help to answer various questions about learner activity, a few examples questions that Caliper might help answer.

* How often is a learner logging in to view their digital resources?
* Are learners interacting with a forum post?
* How often is a learner consuming course readings or videos?
* What activities is a learner interacting with while taking an assessment?
* Are learners annotating certain digital resources?

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

This guide can be used to get a fundamental understanding of the Caliper messaging structure, review specific code examples of Caliper events, and as a central hub containing links to conformance requirements and other important resources. The document can also be used as a reference for collated best practices on how to use Caliper in their digital ecosystem and guidance on using Caliper in collaboration with other IMS specifications.

This document is also meant to assist the reader in learning how to use the main Caliper specification to look up specific items during implementation.

## Terminology

Learning this vocabulary in the context of the Caliper specification will be very helpful when using this document.  Caliper Analytics describes events using [_triples_](https://en.wikipedia.org/wiki/Semantic_triple), a semantic structure that consists of the combination of an **action** being undertaken by an **actor** to an **object**.  A good way to think of it as _someone_ (**actor**) did _something_ (**action**) to _someone/something_ (**object**)

Here are a few useful definitions for terms used throughout this document.  Full Caliper terminology list is available in the [Terminology section of the Caliper Spec](https://www.imsglobal.org/spec/caliper/v1p2#terminology).

<dl>
  <dt>Action</dt><dd>Part of an Event that describes the <em>what</em>.</dd>
  <dt>Actor</dt><dd>Part of an Event that describes the <em>who</em>.</dd>
  <dt>Entity</dt><dd>Part of an Event that describes the <em>to whom</em>.</dd>
  <dt>Agent</dt><dd>Part of an Event that represents a generic form of an <em>Entity</em> and describes the <em>to whom</em> when a more specific <em>Entity</em> is not available.</dd>
  <dt>Event</dt><dd>A collection of an Actor, an Action, and an Object.</dd>
  <dt>Envelope</dt><dd>A JSON payload that can contain one or many Caliper events.</dd>
  <dt>Object</dt><dd>Part of an Event that describes the <em>to whom</em> or <em>to what</em>.</dd>
  <dt>Metric Profile</dt><dd>Groupings of Caliper vocabulary that model a learning activity or a supporting activity. Each Metric Profile provides a domain-specific set of terms and concepts that application designers and developers can draw upon to describe common user interactions in a consistent manner.  Metric Profiles also serve as the unit of certification for the Caliper Analytics&reg; specification.</dd>
  <dt>Sensor</dt><dd> Software deployed within a learning application that capture and transmit Caliper data to a target endpoint.</dd>
</dl>

Here is a short explanation of how Caliper works using this vocabulary. If you can understand this you're well on your way to understanding Caliper!

When a Caliper-observable interaction, as defined by a _Metric Profile_, is detected by a _Sensor_, an _Event_ is created which consists of an _Actor_, an _Object_, and an _Action_. (The Actor did the Action to the Object) To emit an _Event_ to another system via an API call, it is described as a JSON object which is wrapped in an _Envelope_ with a little metadata about the _Sensor_. The JSON is then sent via a secured HTTP call with an authentication token in an HTTP header.

### Links to documentation and related resources

Below is a useful set of resources related to the Caliper Analytics&reg; specification

- [[[CALIPER-12]]]
- [Caliper Analytics&reg; Metric Profile Summaries](https://www.imsglobal.org/caliper-analytics-v11-profiles-summaries)
- [Caliper Analytics&reg; Public Forums](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum)
- [Caliper Analytics&reg; Conformance Information](https://www.imsglobal.org/caliper-analytics-conformance)
- [Caliper Analytics&reg; Conformance Test Suite](https://caliper.imsglobal.org/sec/index.html)
- [Caliper Analytics&reg; On the Web](https://www.imsglobal.org/activity/caliper)
- [Caliper-central GitHub Repository](https://github.com/IMSGlobal/caliper-central)
- [How to use Caliper Analytics&reg; with LTI](#learning-tools-interoperability)

## Conformance Certification

<section id="conformance">
  <h3>Conformance Statements</h3>
</section>

### What is Conformance Certification?
IMS offers a process for testing the conformance of products using the IMS certification test suite. Certification designates passing a set of tests that verify the standard has been implemented correctly and guarantees a product’s interoperability across hundreds of other certified products. The Caliper Analytics [Conformance Certification Guide](https://www.imsglobal.org/spec/caliper/v1p2/cert) provides details about the testing process, requirements, and how to get started.

### What are the benefits of Conformance Certification?
Conformance certification offers more than claims of "compliance,". The only way IMS can guarantee interoperability is by obtaining certification for the latest version of the standard. Only products listed in the official IMS Certified Product Directory can claim conformance certification. IMS certification provides the assurance that a solution will integrate securely and seamlessly into an institution's digital learning ecosystem.

### How does my product get certified?
Certification for Caliper Analytics involves certifying against one or more Metric Profiles.  This means  passing the appropriate tests for the profile or profiles that you are implementing using  the IMS Global suite of Caliper Analytics certification tools.  For more information on the conformance and certification process, please refer to the The Caliper Analytics [Conformance Certification Guide](https://www.imsglobal.org/spec/caliper/v1p2/cert).

## What's new in Caliper 1.2?

In addition to improvements and additions to vocabulary throughout the Caliper 1.2 information model, Caliper introduces 6 new metric profiles built based on market need and member feedback.  Please follow the associated links below to learn more about them.  Those profiles are:

- [Feedback Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-feedback)
- [Resource Management Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-resourcemanagement)
- [Search Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-search)
- [Survey Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-survey)
- [Tool Launch Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-toollaunch)

Additionally, the [Tool Use Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-tooluse) has been improved to account for the collection of measures that track student progress via the collection of aggregate measures.

## How to create a Caliper Event

### Events

[Link to full Event documentation](https://www.imsglobal.org/spec/caliper/v1p2#Event)

An Event is the combination of an **Actor**, an **Action**, and an **Object**. In a sentence, an Event describes what an Actor _did_ (Action) to an Object. Each of those will be described in the following sections.

It's important to have a clear understanding of Caliper Events since they describe the semantics of what's happening in the system.


#### Event Types

Caliper Events each specify which type of event they are.  Events of the same type have several things in common, like required and optional properties. Some event types include:

[AnnotationEvent](https://www.imsglobal.org/spec/caliper/v1p2#AnnotationEvent), [AssignableEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssignableEvent), [AssessmentEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentEvent), [AssessmentItemEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentItemEvent), [ForumEvent](https://www.imsglobal.org/spec/caliper/v1p2#ForumEvent), [MediaEvent](https://www.imsglobal.org/spec/caliper/v1p2#MediaEvent), [MessageEvent](https://www.imsglobal.org/spec/caliper/v1p2#MessageEvent), [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent), [GradeEvent](https://www.imsglobal.org/spec/caliper/v1p2#GradeEvent), [SessionEvent](https://www.imsglobal.org/spec/caliper/v1p2#SessionEvent), [ToolUseEvent](https://www.imsglobal.org/spec/caliper/v1p2#ToolUseEvent), [ThreadEvent](https://www.imsglobal.org/spec/caliper/v1p2#ThreadEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)

A full list of event types is available in the Caliper Spec (See "Subtype" subsection of [Event](https://www.imsglobal.org/spec/caliper/v1p2#Event)).

#### Choosing the appropriate Event

To choose the best Event for your situation you can scan the list of event types and see which one seems to match best, or you can also start by looking at a Metric Profile and see what events are described there that might meet your needs already.

If there is no existing Event that meets your needs you can use a "generic" event from the [General Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-general). These events allow any actor, action, and object you need and aren't constrained like the specific events from other profiles. This should provide you with the flexibility you need when your use case isn't already met by existing profiles.

#### Event Required Properties

Each [Event Type](https://www.imsglobal.org/spec/caliper/v1p2#Event) can have different required properties. To review what's required, find the specific event you're creating in the Caliper spec document and review the table there. For example, you can look at the [Annotation Event's](https://www.imsglobal.org/spec/caliper/v1p2#AnnotationEvent) properties table.

All property tables will look like the following table. This table shows the base Event property requirements that all events share.


| Property | Type | Description | Disposition |
| :------- | :--- | ----------- | :---------: |
| id | [UUID](https://www.imsglobal.org/spec/caliper/v1p2#uuidDef) | A version 4 [UUID](https://www.imsglobal.org/spec/caliper/v1p2#uuidDef).  The UUID MUST be expressed as a [URN](https://www.imsglobal.org/spec/caliper/v1p2#urnDef) using the form <code>urn:uuid:<UUID></code>. | Required |
| type | [Term](https://www.imsglobal.org/spec/caliper/v1p2#termDef) | A string value for the Event Sub Type, or for a generic [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) set the <code>type</code> to the string value <code>Event</code>. | Required |
| actor | [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) or [IRI](https://www.imsglobal.org/spec/caliper/v1p2#iriDef) | The [Agent](https://www.imsglobal.org/spec/caliper/v1p2#agent) who initiated the [Event](https://www.imsglobal.org/spec/caliper/v1p2#event).  This must be either:  <ul><li>An [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) of the type Agent or one of its subtypes (e.g., Person, SoftwareApplication, etc.).</li><li>A unique [IRI](https://www.imsglobal.org/spec/caliper/v1p2#iriDef) that represents an [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) as described above.  Ideally this should refer to an [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) previously defined in the payload containing the [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) or in an eventstore that contains the [Event](https://www.imsglobal.org/spec/caliper/v1p2#event).| Required |
| action | [Term](https://www.imsglobal.org/spec/caliper/v1p2#termDef) | The action or predicate that binds the actor or subject to the object.  The <code>action</code> range is limited to the set of [actions](https://www.imsglobal.org/spec/caliper/v1p2#actions) described in this specification and may be further constrained by the chosen [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) type.  Only one <code>action</code> [Term](https://www.imsglobal.org/spec/caliper/v1p2#termDef) may be specified per [Event](https://www.imsglobal.org/spec/caliper/v1p2#event). | Required |
| object | [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) or [IRI](https://www.imsglobal.org/spec/caliper/v1p2#iriDef) | The [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) that comprises the object of the interaction.  The <code>object</code> value MUST be expressed either as an object or as a string corresponding to the object's [IRI](https://www.imsglobal.org/spec/caliper/v1p2#iriDef). | Required |
| eventTime | DateTime | An ISO 8601 date and time value expressed with millisecond precision that indicates when the [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) occurred.  The value MUST be expressed using the format YYYY-MM-DDTHH:mm:ss.SSSZ set to UTC with no offset specified. | Required |
| profile | [Profile Term](https://www.imsglobal.org/spec/caliper/v1p2#profile-terms) | A string value corresponding to the [Profile Term](https://www.imsglobal.org/spec/caliper/v1p2#profile-terms) value defined for the Profile that governs the rules of interpretation for this [Event](https://www.imsglobal.org/spec/caliper/v1p2#event). For a generic Event set the <code>profile</code> property value to the string term <code>GeneralProfile</code>. | Optional |

#### Additional properties on Events

While the base information required by most Events is represented in the above example, each Event type could require more properties, and allow for more properties and context as desired by the implementors. To understand what information is required and possible you should consult each [Event Type's](https://www.imsglobal.org/spec/caliper/v1p2#Event) documentation for the activities you're trying to implement.

#### Entity or IRI
Properties with the type "[Entity](https://www.imsglobal.org/spec/caliper/v1p2#entity) or [IRI](https://www.imsglobal.org/spec/caliper/v1p2#iriDef)" may be represented as a Caliper entity or an IRI string.  An IRI may be used to refer to an entity that has been defined earlier, either in the same event, in another event in the same payload, or even in another event in the same eventstore.  The IRI may be a URL, but it's not required.  It could be a URN instead, using the "urn" scheme rather than the "http" or "https" schemes commonly used with URLs.  Often, using a blank node scheme (represented by a single underscore character, "\_") offers flexibility to specify an IRI without the burden of requiring it to resolve to a resource like a URL or to follow specific syntax, like a URN.

#### Event JSON stub

This is an example of what an Event's JSON looks like without the actor/action/object. A full example will be given below.

<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:3a648e68-f00d-4c08-aa59-8738e1884f2c",
  "type": "ViewEvent",
  "profile": "ReadingProfile",
  "eventTime": "2020-01-15T10:15:00.000Z",
  "actor": {},
  "action": "",
  "object": {}
}
</code></pre>

### Actors

In a Caliper Event, the <code>Actor</code> performs the action related to a learning activity. The value of an Event's actor attribute must be an [Agent](https://www.imsglobal.org/spec/caliper/v1p2#Agent) or one of its subtypes. While often the Actor is a Person, it could also be another Entity type, such as an Organization or SoftwareApplication.

Each Event type further limits what Agents can be used as the value of the actor property; for example, the actor for a [QuestionnaireEvent](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireEvent) must be a Person, while the actor for a [GradeEvent](https://www.imsglobal.org/spec/caliper/v1p2#GradeEvent) could be either a Person or a SoftwareApplication (such as an autograder).

The generic Event allows any Agent declared in the specification.

#### Actor JSON

<pre><code class="json">
{
  "id": "https://example.edu/users/554433",
  "type": "Person"
}
</code></pre>

### Action

[Link to full Action documentation](https://www.imsglobal.org/spec/caliper/v1p2#actions)

An <code>Action</code> connects an Actor with an Object, helping to describe what learning activity has taken place. Examples include <code>Bookmarked</code>, <code>Launched</code>, <code>OptedIn</code>, and <code>Skipped</code>.

A specific [Event Type](https://www.imsglobal.org/spec/caliper/v1p2#Event) specifies what actions are valid for that type. For example, you can look at the [Annotation Event's](https://www.imsglobal.org/spec/caliper/v1p2#AnnotationEvent) properties table to see that the Action must be one of: <code>Bookmarked</code>, <code>Highlighted</code>, <code>Shared</code>, or <code>Tagged</code>.

The generic Event allows any Action declared in the specification.

#### Action JSON

<pre><code class="json">
"Viewed"
</code></pre>

### Object

The <code>Object</code> of an Event must be an [Entity](https://www.imsglobal.org/spec/caliper/v1p2#entities) or one of its subtypes.

A specific [Event Type](https://www.imsglobal.org/spec/caliper/v1p2#Event) specifies what types of Entities are valid for that type. For example, you can look at the [Annotation Event's](https://www.imsglobal.org/spec/caliper/v1p2#AnnotationEvent) properties table to see that the Object must be a [DigitalResource](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource).

The generic Event allows any Entity declared in the specification.

#### Object JSON

<pre><code class="json">
{
  "id": "https://example.edu/terms/202001/courses/7/sections/1/readings/1",
  "type": "DigitalResource",
  "name": "Chapter 1 reading"
}
</code></pre>

### Caliper Event JSON Examples

There are many examples of events to help you learn how to construct them. Below is an example combining the above documentation.

Other sources for example Event JSON:

* The main Caliper spec document has many examples for each Event Type. For example see the [AnnotationEvent](https://www.imsglobal.org/spec/caliper/v1p2#AnnotationEvent) and scroll past the requirements table to the examples below.
* The public Github repository has many examples for testing purposes: [Caliper 1.2 JSON Examples](https://github.com/IMSGlobal/caliper-spec/tree/develop/fixtures/v1p2)
* If you're an IMS member and have access to the [Caliper certification tool](https://caliper.imsglobal.org/sec/index.html), you can access those same examples in the Caliper Playground's "Manual Testing" area.

#### Complete JSON

To bring the above examples together, an Event would look something like this:

<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:a2f41f9c-d57d-4400-b3fe-716b9026334e",
  "type": "ViewEvent",
  "profile": "ReadingProfile",
  "eventTime": "2020-01-15T10:16:00.000Z",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Viewed",
  "object": {
    "id": "https://example.edu/terms/202001/courses/7/sections/1/readings/1",
    "type": "DigitalResource",
    "name": "Chapter 1 reading"
  }
}
</code></pre>

This Event can be read as "This Person Viewed this DigitalResource at this eventTime".

#### Smaller, ID-Only JSON

As explained in the [Entity or IRI](#entity-or-iri) section above, Caliper allows the use just the ID string instead of the whole JSON object if the size of your events needs to be smaller.

This ID-only example is equivalent to the full example above:

<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:a2f41f9c-d57d-4400-b3fe-716b9026334e",
  "type": "ForumEvent",
  "profile": "ForumProfile",
  "eventTime": "2020-01-15T10:16:00.000Z",
  "actor": "https://example.edu/users/554433",
  "action": "Subscribed",
  "object": "https://example.edu/terms/202001/courses/7/sections/1/forums/1"
}
</code></pre>

## Metric Profiles

Each [Caliper Metric Profile](https://www.imsglobal.org/spec/caliper/v1p2#profiles) is a domain-specific set of terms and concepts to describe common education learning activities. Their purpose is to help ensure users of Caliper have _consistent syntax and semantics_ when describing these events. Some examples of what profiles attempt to describe are Annotating a reading, playing a video, taking a test, or grading an assignment submission.

A great way to think of a Metric Profile is **what questions it can help answer**. For example the [Reading Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-reading) could help Instructors and researchers answer questions such as:

 - Who is consuming the content?
 - What materials are being accessed?
 - When are the resources accessed?
 - How often is the content viewed?
 - What paths are taken to reach the content?

 These examples are given in each profile section in the Caliper specification document.

### Profile Requirements

 Each profile is a collection of one or more Caliper events that together help describe a set of related activities. Each Event type included in a profile places constraints on the entities and actions that can be used. Vocabulary restrictions are outlined in each profile description under the following headings:

* supported events
* supported actors
* supported actions
* supported objects
* supported target entities
* supported generated entities
* other requirements

For example, the [Forum Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-forum) models a set of activities associated with online discussions involving instructors and learners. The profile currently includes a <code>ForumEvent</code>, <code>MessageEvent</code>, <code>NavigationEvent</code>, <code>ThreadEvent</code> and <code>ViewEvent</code>. You can see those events clearly defined in the table in the Forum Profile documentation.

The sequence of events from a Forum Profile implementation might involve a learner navigating to a forum, subscribing to it, viewing a thread, posting a message in reply to an earlier post and then marking the message as read.

### List of Profiles

|Profile|Description|Events Quick-Reference|
|------|------|------|
|[General Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-general)|provides a generic [Event](https://www.imsglobal.org/spec/caliper/v1p2#event) for describing learning or supporting activities that have yet to be modeled by Caliper.|[Event](https://www.imsglobal.org/spec/caliper/v1p2#Event)|
|[Annotation Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-annotation)|models activities related to the annotation of a DigitalResource|[AnnotationEvent](https://www.imsglobal.org/spec/caliper/v1p2#AnnotationEvent)|
|[Assessment Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-assessment)|models assessment-related activities including interactions with individual assessment items.|[AssessmentEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentEvent), [AssessmentItemEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssessmentItemEvent), [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)|
|[Assignable Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-assignable)|models activities associated with the assignment of digital content to a learner for completion according to specific criteria.|[AssignableEvent](https://www.imsglobal.org/spec/caliper/v1p2#AssignableEvent), [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)|
|[Feedback Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-feedback)|models providing feedback and comments on Entities.|[FeedbackEvent](https://www.imsglobal.org/spec/caliper/v1p2#FeedbackEvent)|
|[Forum Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-forum)|models learners and others participating in online forum communities.|[ForumEvent](https://www.imsglobal.org/spec/caliper/v1p2#ForumEvent), [MessageEvent](https://www.imsglobal.org/spec/caliper/v1p2#MessageEvent), [ThreadEvent](https://www.imsglobal.org/spec/caliper/v1p2#ThreadEvent), [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)|
|[Grading Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-grading)|models grading activities performed by an Agent or a SoftwareApplication|[GradeEvent](https://www.imsglobal.org/spec/caliper/v1p2#GradeEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)|
|[Media Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-media)|models interactions between learners and rich content such as audio, images and video.|[MediaEvent](https://www.imsglobal.org/spec/caliper/v1p2#MediaEvent), [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)|
|[Reading Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-reading)|models activities associated with navigating to and viewing digital textual content.|[NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)|
|[Resource Management Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-resourcemanagement)|models a person managing a digital resource|[ResourceManagementEvent](https://www.imsglobal.org/spec/caliper/v1p2#ResourceManagementEvent)|
|[Search Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-search)|models an actor, typically a learner, querying a resource for information|[SearchEvent](https://www.imsglobal.org/spec/caliper/v1p2#SearchEvent)|
|[Session Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-session)|models the creation and subsequent termination of a user session|[SessionEvent](https://www.imsglobal.org/spec/caliper/v1p2#SessionEvent)|
|[Survey Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-survey)|provides a vocabulary for describing events associated with a respondent's participation in online surveys|[SurveyInvitationEvent](https://www.imsglobal.org/spec/caliper/v1p2#SurveyInvitationEvent), [SurveyEvent](https://www.imsglobal.org/spec/caliper/v1p2#SurveyEvent), [QuestionnaireEvent](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireEvent), [QuestionnaireItemEvent](https://www.imsglobal.org/spec/caliper/v1p2#QuestionnaireItemEvent), [NavigationEvent](https://www.imsglobal.org/spec/caliper/v1p2#NavigationEvent), [ViewEvent](https://www.imsglobal.org/spec/caliper/v1p2#ViewEvent)|
|[Tool launch Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-toollaunch)| captures the utilization of learning tools from a centralized location, such as an LTI Tool Platform (often an LMS). As such, it is distinct from the Caliper Tool Use Profile, also defined in this specification, which captures tool usage as reported by the individual tools themselves (i.e. decentralized capture)|[ToolLaunchEvent](https://www.imsglobal.org/spec/caliper/v1p2#ToolLaunchEvent)|
|[Tool Use Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-tooluse)|models an intended interaction between a user and a tool.|[ToolUseEvent](https://www.imsglobal.org/spec/caliper/v1p2#ToolUseEvent)|


### Profiles are used for certification

Profiles also serve as the unit of certification for Caliper. The [Caliper Conformance and Certification Guide](https://www.imsglobal.org/spec/caliper/v1p2/cert) describes the certification process and requirements. Each profile has a section that, in addition to clearly displaying what the certification requirements are, gives an excellent overview of each Event Type and the supported Actions.

### Creating new profiles

The official Caliper specification will never be able to describe every Event or activity needed for all institutions, districts, and vendors. The Caliper workgroup and Product Steering committee are charged with working with all parties to help create new profiles as needed to help the community continue to move forward. Caliper has a profile extension mechanism for adding new profiles without having to release a whole new version of Caliper.


## Sending Events to an endpoint

### Envelopes are required

Caliper Event and Entity data MUST be transmitted inside a Caliper [Envelope](https://www.imsglobal.org/spec/caliper/v1p2#envelope), a purpose-built JSON data structure that includes metadata about the emitting [Sensor](https://www.imsglobal.org/spec/caliper/v1p2#sensor) and the data payload.

A Caliper envelope MUST contain the <code>sensor</code>, <code>sendTime</code>, <code>dataVersion</code> and <code>data</code> properties.  Each property MUST be referenced only once. No custom properties are permitted.

The <code>data</code> element can contain multiple Events and Entities. It is good practice to batch related Events if your Sensor is structured to do so.

#### Base Envelope JSON

<pre><code class="json">
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2020-01-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": [ {event1}, {event2}, {eventN} ]
}
</code></pre>

#### Example Envelope with an Event JSON

<pre><code class="json">
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2020-01-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": [
      {
        "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
        "id": "urn:uuid:7e10e4f3-a0d8-4430-95bd-783ffae4d916",
        "type": "ToolUseEvent",
        "profile": "ToolUseProfile",
        "eventTime": "2020-01-15T10:15:00.000Z",
        "actor": {
          "id": "https://example.edu/users/554433",
          "type": "Person"
        },
        "action": "Used",
        "object": {
          "id": "https://example.edu",
          "type": "SoftwareApplication"
        }
      }
  ]
}
</code></pre>

#### Mixed payload Envelope JSON

In this example, the Person and SoftwareApplication are part of the data array and referenced from the events for reuse.

<pre><code class="json">
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2020-01-15T11:05:01.000Z",
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
    "profile": "ToolUseProfile",
    "eventTime": "2020-01-15T10:15:00.000Z",
    "actor": "https://example.edu/users/554433",
    "action": "Used",
    "object": "https://example.edu"
  },
  {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "urn:uuid:9r34jdfj-a0d8-4430-95bd-783ffae4d916",
    "type": "ToolUseEvent",
    "profile": "ToolUseProfile",
    "eventTime": "2020-01-15T11:15:00.000Z",
    "actor": "https://example.edu/users/554433",
    "action": "Used",
    "object": "https://example.edu"
  }
  ]
}
</code></pre>


### Sending to a secured HTTP endpoint

The current standard way of sending Caliper events is via a secured HTTP endpoint using an <code>Authorization</code> header with a <code>Bearer</code> token. This is described in the Caliper spec [HTTP Request](https://www.imsglobal.org/spec/caliper/v1p2#httpRequest) section.

This is currently the only method supported for [Caliper Conformance](https://www.imsglobal.org/spec/caliper/v1p2/cert).

An application that wants to send these events must either work with a Caliper Consumer directly to get an endpoint URL and authorization token, or use the connection passed via an [LTI service connection](#learning-tools-interoperability).

### Other ways to send Events

Although HTTP messages with an authorization header is the only method currently supported for certification, there are many other ways a Caliper Sensor could send events to a Caliper Consumer. Each integration should use the mechanisms that work best for them and allow the desired scaling possibilities.

For example, a common method is putting Caliper Events into a queue provided by a IaaS provider's queueing service and providing the Caliper Consumer the ability to connect to the queue for consumption.


## Consuming Caliper Events

There are many considerations for consuming Caliper Events. This document will discuss some high-level issues, but the many privacy and security implications of receiving and holding learner data must be managed by a team capable of implementing the proper infrastructure.

### Authorization

As discussed above in [Sending to a secured HTTP endpoint](#sending-to-a-secured-http-endpoint), the current standard for authenticating Caliper Events from a sender is via an <code>Authorization</code> header with a <code>Bearer</code> token. This is described in the Caliper spec [HTTP Request](https://www.imsglobal.org/spec/caliper/v1p2#httpRequest) section. Each learning tool a Caliper Consumer wishes to receive events from will require an exchange of an HTTPS endpoint to send the events to and an authorization token. Another method is using the LTI Caliper Connector service.

If a consumer of Caliper data is utilizing the [LTI service connection](#learning-tools-interoperability) in conjunction with an LMS implementing that LTI service, they will have to work together to establish the needed connection and authorization infrastructure.

There are many other methods of sending and receiving events such as utilizing a queueing system. These are excellent options but they're not covered in this document.

### What implementation considerations exist for Caliper Consumers?
Several implementation considerations exist for Caliper Consumers. Typically, these consumers play a role during the initial ingestion portion of an overall data "pipeline". In such a pipeline, raw source data is emitted or generated, then ingested into a "Data Lake".  A Data Lake is a storage repository than can store large amounts of structured, semi-structured or unstructured data.  Ultimately, the benefit of a data lake approach is to enable flexibility, providing a place for data to be gathered from multiple sources in a variety of formats.

The following best practices are typically recommended for data pipeline components that process Caliper data:

- **Use Cheap Storage to Preserve Raw Event Messages.** When storing event data, it's important not to lose the resolution of information available in the original, raw event data. Because of the volume, and size, of event data en masse, many Caliper consumers might use inexpensive, cloud-hosted persistent storage solutions to preserve raw event messages. Some available solutions can support annotation with metadata for cataloguing and lifecycle purposes, and integrate with other cloud-hosted services that can act as different functional components of a data lake.
- **Take Advantage of Stream Processing Components.** Many existing cloud infrastructure components are useful for bundling groups of Caliper messages arriving at the same time into JSON files, which are then kept in folders organized by year/month/day/hour. In addition, these existing components from IaaS providers can be used to keep running totals or to detect anomalies in event streams.
- **Set Up Ingest Processes With Known Mapping and Transform Rules.** Examples of tasks which may need to be performed with inbound Caliper data are as follows:
   - Identify and locate common identifiers across the incoming data records.
   - Identify mappings between similar but differently named data fields and define logic for any transformations (parsing out specific identifiers from string fields, for example).
   - Determine how to handle display fields that contain strings that might be too long or have unsupported characters
   - Some data records may not contain an identifier that can be used to commonly join them across sources.  In those cases, you will need to maintain a set of mapping tables with locally-sourced identifiers and their mappings to global identifiers.
   - This may mean that you need to manufacture a global set of identifiers to unify the data across systems.
   - Coordinate and communicate with any departments/groups who own or can help locate the "source of truth" for identifiers.
- **Don’t Forget About Reference Data.** Set up processes to bring in reference data (users, departments, calendar events, work project names).


## Code Libraries

Caliper makes available reference implementations for Sensors in the following programming languages.  Links are provided to the GitHub repositories for each

- [Caliper-JS](https://github.com/IMSGlobal/caliper-js)
- [Caliper-Java](https://github.com/IMSGlobal/caliper-java)
- [Caliper-Python](https://github.com/IMSGlobal/caliper-python)
- [Caliper-php](https://github.com/IMSGlobal/caliper-php)
- [Caliper-Ruby](https://github.com/IMSGlobal/caliper-ruby)
- [Caliper-.net](https://github.com/IMSGlobal/caliper-net)

These libraries are written and maintained by IMS Global Learning Consortium members. They should be considered as reference implementations only and as such are offered without any warranty. Use of these code libraries in a production environment should be thoroughly vetted by your development team. We welcome the posting of issues by non IMS Global Learning Consortium members (e.g., feature requests, bug reports, questions, etc.) but we do not accept contributions in the form of pull requests from non-members. For more information, please refer to the readme in the associated repo.

## Use Cases
This section describes a handful common scenarios for the Caliper Specification.  This section is in no way comprehensive but is intended to give the reader an idea of the type of education ecosystem questions that Caliper Analytics&reg; can help to answer for.

### Student Facing Analytics

As students interact with content within an LMS course site, Caliper events are triggered and transported to an event store. The Caliper events are represented in the controlled vocabulary of the Caliper metric profiles. The events are then parsed to extract commonly sought values into columns in a relational database. For example, information such as the event type, the event action, event time, actor, and course is extracted. The event record can also be enriched using related information based on global identifiers such as the course and actor which facilitates joining data from multiple sources.

Downstream analytics applications can then query the event store for events that represent select interactions the students within a course have had with learning content such as a student previewing a file, starting a video, or reviewing a lecture recording. Those events are then visualized so that a student can see what percentage of the class has viewed those resources, when I as the student last viewed that file, and how many times I’ve viewed it. Students can use this information to gauge their performance against their peers and take corrective actions where there may be an issue.

### Understanding value of licensed learning tools

Using the same Caliper data being collected at the course level in the prior scenario, but at the cohort or system level, can be leveraged to determine in aggregate how much usage a licensed tool is getting across a cohort or within a segment of students. This data could be used to determine when it is safe to perform upgrades when it is time to begin migration planning or other operational concerns with various learning tools

### Profile Use Cases

Caliper Metric profiles represent foundational usage cases.  Each Metric Profile has it's own subset of use cases and user stories listed in it's primary specification document as linked to in this document.

For example, the [Assessment Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-assessment) presents the following use case:

 The Caliper Assessment Profile models assessment-related activities including interactions with individual assessment items. Caliper provides <code>Assessment</code>
 and <code>AssessmentItem</code> entities for describing the object of these activities, as well as a learner's Attempt for recording a count of the number of times
 an assigned resource has been attempted.

## Best Practices

Below are some of the collected best practices from members who have successfully implemented the Caliper Analytics&reg; standard.

### Extending Caliper

Major Caliper releases of the base specification will not be released more frequently than every 18 months. This is to help the market have confidence in upgrading to the latest version each time. However, there are extension mechanisms in place to provide sufficient flexibility for all use cases. [New Metric Profiles](#creating-new-profiles) can also be created and published without a new release of Caliper.

#### Extending Entities and Events

All Entities and Events have an optional property called <code>extensions</code> which is a map of undefined key:value pairs. Other than syntax, this property is ignored during certification. Since these properties are not defined as part of Caliper the emitter and consumer of these events will need to work together to understand the meanings of extension properties and it should not be assumed all consumers will understand the data included in the <code>extensions</code> area.

There are no restrictions on key names, but it is best practice to use a name less likely to collide with others who are also using custom extensions. A common practice for this is using a name like <code>"com.toolVendor.identifier_type"</code>.

The values can also be any type or complex objects, though simpler values are recommended.

Using extension properties is encouraged, but they should still be used with caution and purpose since over-use can limit interoperability, and increase payload sizes. There are other such considerations discussed in this section: [Deciding how much data to send in an Event](#deciding-how-much-data-to-send-in-an-event)

##### Example: Extended AssessmentItem Entity

It is recommended that extra information needed for analytics purposes is retrievable by using the ID of an entity, but that isn't always a viable or scalable option so in this example the implementors decided to include the <code>questionType</code> with each assessment item in the extensions area.


<pre><code class="json">
{
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/6",
  "type": "AssessmentItem",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "datePublished": "2016-08-15T09:30:00.000Z",
  "maxScore": 5.0,
  "extensions": {
    "questionType": "Short Answer",
    "questionText": "Define a Caliper Event and provide examples."
  }
}
</code></pre>

### Deciding how much data to send in an Event

Deciding what data to send depends heavily on the context and use-case. The consumer and producers of the Caliper Events should work together to figure what is needed. Here are some considerations for this conversation:

- Data generated by the emitter which would otherwise be lost (i.e. not persisted) is a good candidate to convey in a Caliper event.
- If an object is readily accessible via dereferenceble IRI's then use those instead of including all the object details.
- If there are cases where downstream processes would need quick access to the actual generated data, it is ok to include those data values as well.
- It can be good to only emit what you generate: in other words, if your application has to do any extra work to retrieve related information, it's not recommended to include it in the event payload.

### Tracking sessions across multiple LTI tools

When receiving an LTI Launch via the [LTI service connection](#learning-tools-interoperability) use the <code>caliper_federated_session_id</code> as the <code>id</code> of the <code>LtiSession</code> you include in events:

<pre><code class="json">
 {
   "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
   "type": "LtiSession"
 }
</code></pre>

You add it to an event using the <code>federatedSession</code> key:

<pre><code class="json">
 {
   "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
   "id": "urn:uuid:9r34jdfj-a0d8-4430-95bd-783ffae4d916",
   "type": "ToolUseEvent",
   "profile": "ToolUseProfile",
   "eventTime": "2020-01-15T11:15:00.000Z",
   "actor": "https://example.edu/users/554433",
   "action": "Used",
   "object": "https://example.edu",
   "federatedSession": {
     "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
     "type": "LtiSession"
   }
 }
</code></pre>

For more details about the <code>LtiSession</code> see the [Creating a ToolLaunchEvent](#creating-a-toollaunchevent) section.

#### Other LTI Entity IDs

There is a lot of other information that can be passed along with an LTI Launch. Here are some guidelines to consider when deciding what information to include with your Caliper events:

- pick out the system identifiers from the LTI message that are relevant to you as a Tool, and put them in as SystemIdentifiers on the _entities_ in your events that are relevant. This helps:
   - bind those identifiers to the things they belong to, and not to the "session"
   - data consumers easily find those properties rather than having to dig through a big bag of <code>Event.federatedSession.messageProperties</code> keys.
 - Any identifiers generated by your app should be represented as first class properties in the Caliper event; however any identifiers which were passed into your application (say as LTI launch parameters) should be included as federatedSession properties.

### Including Identifiers from other systems

All Entities support an ordered collection of [SystemIdentifier](https://www.imsglobal.org/spec/caliper/v1p2#SystemIdentifier) entities that represent other identifiers for the Entity that are known to the Sensor. The list of supported types and their descriptions can be found in the main Caliper specification here: [identifierTypes](https://www.imsglobal.org/spec/caliper/v1p2#systemidentifiertype).

Here is an example of adding an extra <code>LisSourcedId</code> identifier to a course offering:
<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "https://example.edu/terms/201601/courses/7",
  "type": "CourseOffering",
  "courseNumber": "CPS 435",
  "academicSession": "Fall 2016",
  "name": "CPS 435 Learning Analytics",
  "otherIdentifiers": [
    {
      "type": "SystemIdentifier",
      "identifier": "example.edu:SI182-F16",
      "identifierType": "LisSourcedId"
    }
  ],
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
</code></pre>

The main Caliper documentation has other examples if you scroll to the example JSON after the properties table: [CourseOffering](https://www.imsglobal.org/spec/caliper/v1p2#CourseOffering), [CourseSection](https://www.imsglobal.org/spec/caliper/v1p2#CourseSection), [Person](https://www.imsglobal.org/spec/caliper/v1p2#Person), [Envelope with Mixed Payload Example](https://www.imsglobal.org/spec/caliper/v1p2#jsonldPayload)


### Robustness expectations

As an _analytics_ specification, Caliper is not generally well suited to other uses that require more robust guarantees around timeliness and completeness.  A few items of consideration are listed below.

- Caliper is _not_ specified as a messaging or transaction service
- There are no guarantees around delivery timing in the specification
- Events in Caliper are _not_ ordered and may come much later, or in batches, etc.
- Any integration parties may plan to use events as transaction but they will need to design their requirements together and not rely on Caliper certification implying others meet their extra expectations.
- Using Caliper for official grade or enrollment data exchange is not recommended. Use the other IMS specifications built to solve those integration problems.


### JSON-LD

[JSON-LD](https://www.w3.org/2018/jsonld-cg-reports/json-ld/) is a specification providing a JSON-based data serialization and messaging format, processing algorithms, and API for working with Linked Data. Implementations of Caliper do not need to utilize JSON-LD itself to emit or consume Caliper events as they can be treated as regular JSON objects. If your implementation utilizes some of the benefits of JSON-LD that is excellent, but it is important to realize most implementations will not.


## Caliper in the IMS ecosystem

As an analytics standard, Caliper is relevant to almost every other IMS specification in some way. These sections will cover some of ways Caliper interacts with other specifications.


### CASE - Competencies and Academic Standards Exchange

[[[CASE-10]]] is used to align learning content and activities with academic standards. It might be useful to pass the CASE standard a Caliper <code>Entity</code> is aligned with via a [LearningObjective](https://www.imsglobal.org/spec/caliper/v1p2#LearningObjective) <code>Entity</code> included with the <code>Object</code> in a Caliper <code>Event</code>.

Researchers and analytics who collect data aligned to learning objectives can use it to correlate between learning activities and academic standards.

Wherever CASE-aligned learning objectives are associated to [DigitalResources](https://www.imsglobal.org/spec/caliper/v1p2#DigitalResource) you may want to include them in the <code>learningObjectives</code> array on your resource.

If the Caliper endpoint is able to retrieve this information from another source then it may be better to not include the <code>LearningObjective</code> to help keep the Caliper Event's JSON smaller.

Here is an example of a CASE <code>LearningObjective</code> with a full object (<code>name</code>, <code>description</code>, and <code>otherIdentifiers</code> are _optional_)

<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/202001/courses/7/sections/1/assign/2",
  "type": "AssignableDigitalResource",
  "name": "Reading Assignment: Research techniques",
  "learningObjectives": [
    {
      "id": "urn:uuid:2f5e8130-46fa-11e7-b197-cd3432e719f9",
      "type": "LearningObjective",
      "name": "Research techniques",
      "description": "ELAGSE1RL1 Ask and answer questions about key details in a text.",
      "otherIdentifiers": [
          {
              "type": "SystemIdentifier",
              "identifier": "https://case.georgiastandards.org/ims/case/v1p0/CFItems/2f5e8130-46fa-11e7-b197-cd3432e719f9",
              "identifierType": "CaseItemUri"

          }
      ]
    }
  ]
}
</code></pre>

For brevity, it is also valid to just include the <code>id</code> in the <code>learningObjectives</code> array like this:

<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/202001/courses/7/sections/1/assign/2",
  "type": "AssignableDigitalResource",
  "name": "Reading Assignment: Research techniques",
  "learningObjectives": [
    "urn:uuid:2f5e8130-46fa-11e7-b197-cd3432e719f9",
    "urn:uuid:2f5eda0e-46fa-11e7-b90a-62096a00843f"
  ]
}
</code></pre>


### Learning Tools Interoperability


#### How does an LTI Tool know where to send Caliper events?

An LTI Platform can use the [LTI Caliper Connector](https://www.imsglobal.org/spec/lti-cac/v1p0) service details to indicate to an LTI Tool where it should send Caliper events and entities. The LTI Tool will use the standard LTI workflow for authentication in order to use this service.

This service also specifies that the <code>Caliper.sessionId</code> value should be sent on an LTI launch. This is what Caliper calls the "Federated Session ID" as described in the [How are sessions tracked across multiple LTI tools?](#tracking-sessions-across-multiple-lti-tools) section.


#### Tracking LTI tool usage and privacy issues with Tool Launch Profile & LTI Insights

For the institutions that heavily use LTI tools they often want to know how much a tool is used, and what information about the student and class is being sent to 3rd party vendors. There are 2 Caliper Profiles that help make this information available to faculty and administrators.

The [Tool Use](https://www.imsglobal.org/spec/caliper/v1p2#profile-tooluse) and [Tool Launch](https://www.imsglobal.org/spec/caliper/v1p2#profile-toollaunch) profiles are meant to help understand how LTI tools are used at an institution. Their use is highly recommended for all LTI tools.

The [LTI Insights](https://www.imsglobal.org/lti-insights) project is a great example of monitoring
LTI usage at an institution.

#### Creating a ToolLaunchEvent

The [ToolLaunchEvent](https://www.imsglobal.org/spec/caliper/v1p2#ToolLaunchEvent) is an event created
when a user "launches" an LTI tool from a Platform, usually an LMS. This event can be used help
schools know what tools are being used and how much. The <code>federatedSession</code> is
required and allows you to track a user's session across many launches and multiple tools.

A simple ToolLaunchEvent would look like this:

<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:a2e8b214-4d4a-4456-bb4c-099945749117",
  "type": "ToolLaunchEvent",
  "profile": "ToolLaunchProfile",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Launched",
  "object": {
    "id": "https://example.com/lti/tool",
    "type": "SoftwareApplication"
  },
  "eventTime": "2018-11-15T10:15:00.000Z",
  "federatedSession": {
    "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
    "type": "LtiSession"
   }
}
</code></pre>

In an <code>LtiSession</code> object you can capture the <code>messageParameters</code> from an LTI
launch message. This launch information is primarily needed for the LTI tool to operate and not
usually used for conveying learning activity so a sender of this event should generally only include
the information actually needed for their purposes. For example, if you're tracking what
privacy-related information is being sent to all your tool vendors, it's useful to send all the
parameters to evaluate, but if you're just interested in usage then most of the launch parameters
may be superfluous.

The <code>MessageParameters</code> look a bit different for different versions of LTI. Below are
examples for LTI 1.3, 1.1 and family, and also an example of using this same object for integrations
that aren't necessarily using LTI but can include data sent to a 3rd party tool.

##### MessageParameters Example LTI 1.3

LTI 1.3 uses JSON as its core message parameter mechanic, so it straight forward to include them in
the <code>MessageParameters</code> of an LTISession like this:

<pre><code class="json">
{
   "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
   "type": "LtiSession",
   "user": "https://example.edu/users/554433",
   "messageParameters": {
       "iss": "https://example.edu",
       "sub": "https://example.edu/users/554433",
       "aud": ["https://example.com/lti/tool"],
       "exp": 1510185728,
       "iat": 1510185228,
       "azp": "962fa4d8-bcbf-49a0-94b2-2de05ad274af",
       "nonce": "fc5fdc6d-5dd6-47f4-b2c9-5d1216e9b771",
       "name": "Ms Jane Marie Doe",
       "given_name": "Jane",
       "family_name": "Doe",
       "middle_name": "Marie",
       "picture": "https://example.edu/jane.jpg",
       "email": "jane@example.edu",
       "locale": "en-US",
       "https://purl.imsglobal.org/spec/lti/claim/deployment_id": "07940580-b309-415e-a37c-914d387c1150",
       "https://purl.imsglobal.org/spec/lti/claim/message_type": "LtiResourceLinkRequest",
       "https://purl.imsglobal.org/spec/lti/claim/version": "1.3.0",
       "https://purl.imsglobal.org/spec/lti/claim/roles": [
          "http://purl.imsglobal.org/vocab/lis/v2/institution/person#Student",
          "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
       ],
       "https://purl.imsglobal.org/spec/lti/claim/context": {
          "id": "https://example.edu/terms/201801/courses/7/sections/1",
          "label": "CPS 435-01",
          "title": "CPS 435 Learning Analytics, Section 01",
          "type": ["http://purl.imsglobal.org/vocab/lis/v2/course#CourseSection"]
       },
       "https://purl.imsglobal.org/spec/lti/claim/resource_link": {
          "id": "200d101f-2c14-434a-a0f3-57c2a42369fd",
          "description": "Assignment to introduce who you are",
          "title": "Introduction Assignment"
       },
       "https://purl.imsglobal.org/spec/lti/claim/tool_platform": {
          "guid": "https://example.edu",
          "name": "Example Tool Platform",
          "url": "https://example.edu",
          "version": "1.0"
       },
       "https://purl.imsglobal.org/spec/lti/claim/custom": {
          "xstart": "2017-04-21T01:00:00Z",
          "request_url": "https://tool.com/link/123"
       },
       "https://purl.imsglobal.org/spec/lti/claim/lis": {
          "person_sourcedid": "example.edu:71ee7e42-f6d2-414a-80db-b69ac2defd4",
          "course_offering_sourcedid": "example.edu:SI182-F16"
       }
    },
   "dateCreated": "2020-01-15T10:15:00.000Z",
   "startedAtTime": "2020-01-15T10:15:00.000Z"
 }
</code></pre>

##### MessageParameters Example for LTI 1.0, 1.1, 1.2

Previous versions of LTI used properties in a form POST, so you'll need to convert each key/value
pair for the <code>MessageParameters</code> like this:

<pre><code class="json">
{
   "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
   "type": "LtiSession",
   "user": "https://example.edu/users/554433",
   "messageParameters": {
        "lti_version": "LTI-1p0",
        "lti_message_type": "basic-lti-launch-request",
        "resource_link_id": "120988f929-274612",
        "user_id": "292832126",
        "roles": "Instructor",
        "lis_person_name_full": "Jane Q. Public",
        "lis_person_contact_email_primary": "user@school.edu",
        "lis_person_sourcedid": "school.edu:user",
        "context_id": "456434513",
        "context_title": "Design of Personal Environments",
        "context_label": "SI182",
        "tool_consumer_instance_guid": "lmsng.school.edu",
        "tool_consumer_instance_description": "University of School (LMSng)",
        "custom_xstart": "2017-04-21T01:00:00Z",
        "custom_request_url": "https://tool.com/link/123"
   },
   "dateCreated": "2020-01-15T10:15:00.000Z",
   "startedAtTime": "2020-01-15T10:15:00.000Z"
 }
</code></pre>

##### MessageParameters Example for an integrated non-LTI tool

Despite the name "LtiSession", these session objects can be used to model non-LTI integrations just
as well as LTI ones. The <code>messageParameters</code> object has no restrictions and can thus be
used to hold data from any kind of integration.

For example, LTI 1.3 builds on top of the popular OpenID Connect (OIDC) standard for verifying a user's
identity between integrated systems. If a platform was using a non-LTI OIDC integration the
<code>messageParameters</code> could look something like this:

<pre><code class="json">
{
   "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
   "type": "LtiSession",
   "user": "https://example.edu/users/554433",
   "messageParameters": {
       "iss": "https://example.edu",
       "sub": "https://example.edu/users/554433",
       "aud": ["https://example.com/lti/tool"],
       "exp": 1510185728,
       "iat": 1510185228,
       "azp": "962fa4d8-bcbf-49a0-94b2-2de05ad274af",
       "nonce": "fc5fdc6d-5dd6-47f4-b2c9-5d1216e9b771",
       "name": "Ms Jane Marie Doe",
       "given_name": "Jane",
       "family_name": "Doe",
       "middle_name": "Marie",
       "picture": "https://example.edu/jane.jpg",
       "email": "jane@example.edu",
       "locale": "en-US"
    },
   "dateCreated": "2020-01-15T10:15:00.000Z",
   "startedAtTime": "2020-01-15T10:15:00.000Z"
 }
</code></pre>

Perhaps a school would like to also track logins via SAML or Shibboleth via a Caliper event. The
assertions and messages could be converted from their XML values into a simple format that fits into a
<code>messageParameters</code> object. That could look something like this:

<pre><code class="json">
{
   "id": "urn:uuid:1c519ff7-3dfa-4764-be48-d2fb35a2925a",
   "type": "LtiSession",
   "user": "https://example.edu/users/554433",
   "messageParameters": {
       "login_type": "saml",
       "saml_version": "2.0",
       "response_id": "07940580-b309-415e-a37c-914d387c1150",
       "IssueInstant": "2020-01-15T10:15:00Z",
       "Destination": "http://sp.example.com/demo1/index.php?acs",
       "InResponseTo": "\_4fee3b04709234efa4234755273d56685",
       "Issuer": "http://idp.example.com/metadata.php",
       "signed": "true",
       "Status": "urn:oasis:names:tc:SAML:2.0:status:Success",
       "Subject_NameID": "\_ce3d2948b4cf20146dee0a0b3dd6f69b6cf86f62d7",
       "Audience": "http://sp.example.com/demo1/metadata.php",
       "AuthnContextClassRef": "urn:oasis:names:tc:SAML:2.0:ac:classes:Password",
       "mail": "test@example.com",
       "eduPersonAffiliation": ["users", "learners"]
   },
   "dateCreated": "2020-01-15T10:15:00.000Z",
   "startedAtTime": "2020-01-15T10:15:00.000Z"
 }
</code></pre>

Since the format and contents of the <code>messageParameters</code> for non-LTI tools isn't strictly
specified, the senders and receivers of these events should work closely together to make sure both
sides understand the meaning of the fields and what information is needed for the desired use case.


### LTI Resource Search

[LTI Resource Search](https://www.imsglobal.org/activity/lti-resource-search) is a standard that defines how to search digital repositories for a set of resources. It addresses searching learning object repositories (LORs), and other catalogs of learning resources, from learning tools using various attributes of resources and returning full metadata about the resources to the learning tools. Results can be launched either as URLs or LTI links.

If you wish to collect Caliper analytics events for users interacting with a Resource Search application, you can use the [SearchEvent](https://www.imsglobal.org/spec/caliper/v1p2#SearchEvent) that is within the [Search Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-search).

In Caliper terms, a search "generates" a <code>SearchResponse</code> object to be included in the event. You can read the details in the [SearchResponse documentation](https://www.imsglobal.org/spec/caliper/v1p2#SearchResponse).

The <code>searchProvider</code> is the SoftwareApplication providing the search interface and returning the results. The <code>searchTarget</code> is what is being searched such as a text book or LOR application. Both these fields are optional but may be useful depending on your use case. Generally the <code>object</code> of the Search Event should be the same as the <code>searchTarget</code>.

Since the <code>SearchResponse</code> will usually be a desired object to include, this event will usually be sent <em>after</em> the search results have been generated, not before.

The <code>id</code> of the <code>Query</code> should be the URL used for the search. The <code>id</code> of the <code>SearchResponse</code> can be any IRI, but depending on your usage, it may useful to also make that ID contain the search URL.

This is an example of what a Resource Search event might look like:

<pre><code class="json">
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:cb3878ed-8240-4c6d-9fee-77221810f5e4",
  "type": "SearchEvent",
  "profile": "SearchProfile",
  "eventTime": "2020-01-15T10:05:00.000Z",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Searched",
  "object": {
    "id": "https://example.edu/catalog",
    "type": "SoftwareApplication"
  },
  "generated": {
    "id": "https://example.edu/ims/rs/v1p0/resources?fields=url,name,description&filter=search~'cats'&limit=25",
    "type": "SearchResponse",
    "searchProvider": "https://example.edu",
    "searchTarget": "https://example.edu/catalog",
    "searchResultsItemCount": 3
    "query": {
      "id": "https://example.edu/ims/rs/v1p0/resources?fields=url,name,description&filter=search~'cats'&limit=25",
      "type": "Query",
      "creator": "https://example.edu/users/554433",
      "searchTarget": "https://example.edu/catalog",
      "searchTerms": "cats",
      "dateCreated": "2020-01-15T10:05:00.000Z"
    }
  }
}
</code></pre>


### OneRoster & LIS

Caliper Entities can contain a lot of contextual information beyond the interaction described in an Event. However, it isn't always good practice to include all that information because that can make your Events very large and repetitive. In many cases it's preferred to include as little contextual information as possible in an included Entity or Agent to keep the amount of data being sent to a minimum. In this case, since that contextual information is still likely needed for analysis, services like OneRoster and LIS can be used to fetch that information from SIS systems allowing you to get everything needed about a user, course, or section.

The identifiers included in your Caliper Events should be aligned to the identifiers in these SIS systems to allow this functionality. When planning an analytics project, you should make sure all the appropriate IDs are included for your needs.

For instructions on how to do that see the section [Including Identifiers from other systems](#including-identifiers-from-other-systems).

### OpenVideo

The [Media Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-media) can be used by platforms implementing [OpenVideo](https://www.imsglobal.org/activity/openvideo).


### QTI - Question and Test Interoperability

For a learner's interactions within a [QTI](https://www.imsglobal.org/question/index.html) assessment the [Assessment Profile](https://www.imsglobal.org/spec/caliper/v1p2#profile-assessment) should be used. This profile is useful for all assessments whether driven by QTI or not allowing researchers and tool creators to send events about assessment generically.


<section class="appendix informative" id="revisionhistory">
## Revision History

| Release Date  | Comments                |
|---------------|-------------------------|
| 21 October, 2020 | Base Document Release |
| 27 March, 2020 | Candidate Final Release |
</section>
`;