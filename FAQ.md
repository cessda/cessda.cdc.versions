# CDC Frequently Asked Questions

### N.B. the CESSDA DATA Catalogue (CDC) gets its content by 'harvesting' metadata records from existing catalogues.

Q: What are the basic technical requirements for an endpoint to be harvestable by the CDC?

A: An OAI-PMH compliant REST API that returns DDI 1.2 or DDI 2.5 content in XML format.
In practice, that means the endpoint can be implemented by NESSTAR, Dataverse, Kuha2, jOAI etc.

Q: Any there other requirements for a harvestable endpoint (CV’s, languages)?

A: None in principle. In practice, an endpoint holding a large number of records (typically thousands) may need to be cached, otherwise the harvesting process will time out if it takes too long to send the list of headers (summary of all metadata records available).


Q: In order to in have harvested metadata records included in the CDC, what fields must be present?

A: In the following, the format is `CDC User Interface label`, followed by `<DDI 2.5 field name>`.
Note that `<IDNo>` may or may not be in the form of a persistent identifier, hence it is used for Study Number and may be used for Study Persistent Identifier. The language of the metadata file should be stated using `<codeBook>@xml:lang`, otherwise it defaults to English.
 
**Must be present**: `Study number <IDNo>, Abstract <abstract>, Study title <titl>, publisher <distrbtr>, Study Url <URI>`
 
*Should be present*: `Topic <topcClas>, Keyword <keyword>, Time dimension <timeMeth>, Country <nation>, Analysis unit <anlyUnit>, Year of publication <distDate>, Study Persistent Identifier <IDNo>, Creator <AuthEnty>, Language of data file(s) <fileDscr><fileTxt>@xml:lang>, Data collection method <collMode>, Data collection period: start date <stdyDscr><stdyInfo><sumDscr><collDate>@date @event="start">, Data collection period: end date <stdyDscr><stdyInfo><sumDscr><collDate>@date @event="end">, Terms of data access <restrctn>`
 
 
Q: How does the metadata harvester part of the CDC work?

A: The harvester is provided with a list of URLs of the endpoints, and the handler type to use for each.
A handler is an adaptor that converts the format of the harvested metadata to CMM standard in JSON format.


Q; What types of endpoints can be harvested?

A: There are 2 handlers/adaptor types at present: for DDI 1.2 content in XML format; for DDI 2.5 content in XML format. 

Q: Can more types of endpoints be harvested?

A: Yes, more handlers can be added, but they need to be developed (which takes a few day of effort). 

Q: Can more endpoints of the same type (OAI-PMH DDI 1.2/DDI 2.5) be harvested?

A: Yes, it is relatively easy to add a new endpoint of the same type.
  
Q: Is there a general overview of the CDC available?

A: More information is available here: [The New CESSDA Data Catalogue](https://zenodo.org/record/2530106#.XJIiRSj7SUk)
 