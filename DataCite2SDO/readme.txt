This directory contains XML transform modules to create schema.org JSON-LD to insert in web pages for Datasets.

 XMLToSchemaOrgDataset-template.xslt is a template file that can be used as a starting point to create JSON-LD from an XML metdata format. 
 
 DataCiteToSchemaOrgDataset.xslt is a transform to create schema.org JSON-LD from dataCite XML. The module will work with DataCite v2, v3 and v4.  Funding references are places in an 'isPartOf' key, pending community convergence on how to represent acknowledgment for funding support for creation of a dataset. The transform duplicates JSON-LD produced from the DataCite service (e.g. https://data.datacite.org/application/vnd.schemaorg.ld+json/10.1594/ieda/100577), results can be compared with the files in the examples directory.
 
 Differences with DataCite generated schema.org markup:
 
 the transform includes spatialCoverage content if present
 the transform puts keywords in as an array of strings, the subjectScheme attribute is not transferred to the JSON-LD
 Transform does not include a 'schemaVersion' element; guidance on that property suggests the schema would be the content schema for the resoruce documented by the metadata, not the metadata. 
 The provider organization is the same as the publisher (not DataCite as in the DataCite versions.)
 The transform includes some other additionalTypes.
 The transform generates a distribution object for the dataset landing page; if http alternate identifiers are included, these are also represented as distributions. 
 Non http alternate identifiers are included in an identifiers key. 
 
 
 SM Richard
 20180115