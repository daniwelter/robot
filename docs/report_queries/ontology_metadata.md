# Ontology Metadata

Problem: The ontology header is missing required metadata. Currently, the OBO Foundry expects: a [license](http://dublincore.org/documents/dcmi-terms/#terms-license), a [description](http://dublincore.org/documents/dcmi-terms/#elements-description), and a [title](http://dublincore.org/documents/dcmi-terms/#elements-title).

Solution: Add the missing metadata. See links for appropriate annotation properties.

```sparql
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>

SELECT DISTINCT ?entity ?property ?value
WHERE {
 VALUES ?property {
   dcterms:license
 	dc:description
 	dc:title
 }
 ?entity a owl:Ontology .
 OPTIONAL { ?entity ?property ?value }
 FILTER (!bound(?value))
}
```
