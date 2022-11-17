# CDC Frequently Asked Questions

*N.B. the CESSDA DATA Catalogue (CDC) gets its content by 'harvesting' metadata records from existing catalogues.*

Q: What are the basic technical requirements for an endpoint to be harvestable by the CDC?

A: An OAI-PMH compliant REST API that returns DDI 2.5 content in XML format. In practice, that means the endpoint can be implemented by Dataverse, Kuha2, jOAI etc.

Q: In order to in have harvested metadata records included in the CDC, what fields must be present?

A: The required fields are specified in DDI profiles, which specify the XPaths to use, as well as usage notes for the fields. These can be used for validation and are available at <https://cmv.cessda.eu/documentation/profiles.html>.

Q: Any there other requirements for a harvestable endpoint (CV’s, languages)?

A: None in principle. In practice, an endpoint holding a large number of records (typically thousands) may need to be cached, otherwise the harvesting process will time out if it takes too long to send the list of headers (summary of all metadata records available) or individual metadata records (which will result in these records being unavailable).

Q: How does the harvesting process of the CDC work?

A: The harvester is provided with a list of URLs of the endpoints, and the format of metadata that the endpoints use. The pipeline will convert the format of the harvested metadata to a standard JSON format for internal representation.

Q; What types of endpoints can be harvested?

A: Currently only metadata represented as DDI 2.5 Codebook is supported.

Q: Can more types of endpoints be harvested?

A: Yes, more handlers can be added, but they need to be developed.

Q: Can more endpoints of the same type (OAI-PMH DDI 1.2/DDI 2.5) be harvested?

A: Yes, it is relatively easy to add a new endpoint of the same type.
  
Q: Is there a general overview of the CDC available?

A: More information is available here: [The New CESSDA Data Catalogue](https://zenodo.org/record/2530106#.XJIiRSj7SUk)
