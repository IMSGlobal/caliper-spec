# IMS Global Learning Consortium, Inc.

# Caliper Analytics&reg; Specification
The [Caliper Analytics® Specification](https://www.imsglobal.org/caliper/v1p1/caliper-spec-v1p1) 
provides a structured approach to describing, collecting and exchanging learning activity data at 
scale. Caliper also defines an application programming interface (the Sensor API™) for marshalling 
and transmitting event data from instrumented applications to target endpoints for storage, 
analysis and use.

## Files in the repository

| Name                              | Description                                                                                                                                                                                                                     |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `caliper-spec.md`                 | The main specification document.                                                                                                                                                                                                |
| `/guides/implementation-guide.md` | The implementation guide document.                                                                                                                                                                                              |
| `/guides/certification-guide.md`  | The Certification guide specifies the requirements and process for certification.                                                                                                                                               |
| `/ontology/`                      | Directory for machine-readable documents that define the concepts, relationships and constraints that together comprise the Caliper information model. The ontology is available in three flavors: JSON-LD, RDF/XML and Turtle. |
| `/profiles/`                      | Some Caliper Profiles are defined in their own documents instead of in the main specification document. Those are stored in this directory.                                                                                     |

## Caliper Central repository

[caliper-central](https://github.com/IMSGlobal/caliper-central)

Caliper Central has a listing of all peripheral Caliper repositories and is used as the primary place to log issues in github for Caliper development. 

## Branches
* __master__: stable, deployable branch that stores the official release history.  
* __develop__: unstable development branch.  Current work that targets a future release is 
merged to this branch.

## Tags
Following the 1.1.0 release *caliper-spec* releases will be tagged as follows:

#### Tags on master 
* `1.2-final`: denotes the release of version 1.2 in Final state

* `1.1-errata.01`: denotes the first errata release for version 1.1 

* `1.1-errata.02`: denotes the second errata release for version 1.1

#### Tags on develop (pre-release)
* `1.2-base.01`: denotes the first release of version 1.2 in Base Document state

* `1.2-candidate.01`: denotes the first release of version 1.2 in Candidate Final state

* `1.2-candidate.02`: denotes the second release of version 1.2 in Candidate Final state

_Note: the third `.nn` segment is incremented whenever the same type of release may occur 
multiple times for a given version of a document._

## Contributing
We welcome the posting of issues by non IMS Global Learning Consortium members (e.g., feature 
requests, bug reports, questions, etc.) but we *do not* accept contributions in the form of pull 
requests from non-members. See [CONTRIBUTING.md](./CONTRIBUTING.md) for more 
information.

## License
This project is licensed under the terms of the IMS Global Learning Consortium Specification Document 
License. See the [LICENSE](./LICENSE.md) file for details.

©2018 IMS Global Learning Consortium, Inc. All Rights Reserved.
Trademark Information - http://www.imsglobal.org/copyright.html
