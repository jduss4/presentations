# Hello World

## OSCYS

In the [SPARQLer](http://www.sparql.org/sparql.html)

```
SELECT *
FROM <http://earlywashingtondc.org/rdf/oscys.relationships.ttl>
WHERE {
  ?s ?p ?o
}
LIMIT 100
```

The above will return results for "any subject any predicate and any object"

Now make your results look a little nicer by setting prefixes:

```
PREFIX oscys:<http://earlywashingtondc.org/rdf/oscys.relationships#>
PREFIX owl:<http://earlywashingtondc.org/rdf/oscys.objectproperties.owl#>

SELECT *
FROM <http://earlywashingtondc.org/rdf/oscys.relationships.ttl>
WHERE {
  ?s ?p ?o
}
LIMIT 100
```

## DBPedia

In the [dbpedia sparqler](http://dbpedia.org/sparql):

```
SELECT *
WHERE {
  ?s ?p ?o
}
LIMIT 100
```
