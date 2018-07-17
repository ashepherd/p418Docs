# ESIP Summer 2018 Authoring Session

## Audience Poll

1. How many are familiar with JSON? JSON-LD?
2. How many have heard about schema.org? familiar with it? tried it?
3. How many manually create/edit metadata? have it dynamically generated?

## JSON-LD Primer

[What is JSON-LD](https://www.youtube.com/watch?v=vioCbTo3C-4)

[JSON-LD Specification](https://json-ld.org/spec/latest/json-ld/#basic-concepts)

[JSON-LD Playground](https://json-ld.org/playground/)

[JSON-LD Developer Libraries](https://json-ld.org/) (navigate down to the Developers section)

## Step 1: Create some JSON

1. Go to the [JSON-LD Playground](https://json-ld.org/playground/)
2. Create a *JSON* record to describe a dataset with properties for its name, it's url, amd it's author(s).

Sample:
<pre>
{
  "name": "BML Mooring pCO2",
  "url": "https://example.org/dataset/3537",
  "author": {
     "name": "Dr Tessa Hill",
     "role": "Principal Investigator"
  }
}
</pre>

3. Set the view in the playground to 'Expanded' (at the bottom).

### Question: Why is 'Expanded' view of our JSON blank? ###

## Step 2: Turn that JSON into JSON-LD

[The Context](https://json-ld.org/spec/latest/json-ld/#the-context) - "@context"

1. Add a "@context" to your JSON to make it JSON-LD

<pre>
{
  <strong>"@context": "http://schema.org",</strong>
  "@type": "Dataset",
  "name": "BML Mooring pCO2",
  "url": "https://example.org/dataset/3537",
  "author": {
     "name": "Dr Tessa Hill",
     "role": "Principal Investigator"
  }
}
</pre>

2. Switch the playground view to 'Table'

### Question: Why is the 'role' attribute not using schema.org? ###

## Step 3: Give a type to your JSON-LD

[Typing](https://json-ld.org/spec/latest/json-ld/#specifying-the-type) - "@type"

1. Add a "@type" to our Dataset.

<pre>
{
  "@context": "http://schema.org",
  <strong>"@type": "Dataset",</strong>
  "name": "BML Mooring pCO2",
  "url": "https://example.org/dataset/3537",
  "author": {
     "name": "Dr Tessa Hill",
     "role": "Principal Investigator"
  }
}
</pre>

2. Notice in the 'Table' view that 'Dataset' is linked and the "@type" has been replaced with '[http://www.w3.org/1999/02/22-rdf-syntax-ns#type](http://www.w3.org/1999/02/22-rdf-syntax-ns#type)' - the URL for identifying classes in RDF.

### Question: In 'Table' view, why are the subjects listed as '_:b0'and '_:b1'? ###

## Step 4: Identifying the 'first class citizens' in your data

[Identifying "Things"](https://json-ld.org/spec/latest/json-ld/#node-identifiers) - "@id"

1. Add a "@id" to our Dataset.

<pre>
{
  "@context": "http://schema.org",
  "@type": "Dataset",
  <strong>"@id": "https://example.org/dataset/3537",</strong>
  "name": "BML Mooring pCO2",
  "url": "https://example.org/dataset/3537",
  "author": {
     <strong>"@id": "https://example.org/author/1234",</strong>
     "name": "Dr Tessa Hill",
     "role": "Principal Investigator"
  }
}
</pre>

2. Notice in the 'Table' view that the 'http://schema.org/author' predicate now has a linked Object that matches the subjects of our author statements.

### Question: What if my author is defined at a URL with its own JSON-LD? ###

You do not *need* to present all the fields for all your types that have representations that can be found by resolving their '@id'.

<pre>
{
  "@context": "http://schema.org",
  "@type": "Dataset",
  <strong>"@id": "https://example.org/dataset/3537",</strong>
  "name": "BML Mooring pCO2",
  "url": "https://example.org/dataset/3537",
  "author": {
     <strong>"@id": "https://example.org/author/1234"</strong>
  }
}
</pre>



