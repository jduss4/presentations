# Part 3: Querying Datasets with SPARQL

## Available Datasets

- [dbpedia sparqler](http://dbpedia.org/sparql)
- [data.gov](http://catalog.data.gov/dataset) (filter by RDF)
- [OSCYS](http://earlywashingtondc.org/rdf/oscys.relationships.ttl) (large file)

For this workshop, I recommend using either dbpedia or OSCYS.  If you are using dbpedia, you may make queries through their interface.  If you are using OSCYS or a dataset of your choice, you will need to use the SPARQLer:  [SPARQLer](http://www.sparql.org/sparql.html)

## Example Queries

### Hello World with OSCYS


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

### DBPedia By Random Article

Go to a wikipedia random article: [random article](https://en.wikipedia.org/wiki/Special:Random)

Now navigate to the DBPedia SPARQLer: [dbpedia](http://dbpedia.org/sparql)

Take the last part of the URL after `/wiki/` and sub it into the following code:

```
SELECT *
WHERE {
 <http://dbpedia.org/resource/{your_article_here}> ?p ?o
}
LIMIT 200
```

Try to find a little more information about your topic by narrowing in on one predicate.  Pick something that appears in the first column of your results and sub it in here instead of subdivisionName:

```
SELECT *
WHERE {
 <http://dbpedia.org/resource/Charlotte,_North_Carolina> <http://dbpedia.org/property/subdivisionName> ?o
  
}
LIMIT 100
```

Go back to your first query and this time, we're going to get a longer list of things that are related through the same predicates

```
SELECT *
WHERE {
  <http://dbpedia.org/resource/{your_article_here}> ?p1 ?o1 .
  ?s2 ?p1 ?o2
}
LIMIT 200
```
__Notice the `.` after the triple, this indicates there is another line of the where clause!__

The above query means any predicates your subject has are being used to pull up a list of other subjects and objects that also use those predicates.  You can see how this could be useful to start meandering through a dataset, poking around to see what is there!

### Prefixes

In order to make your queries shorter, you can put prefixes at the top, like in our Hello World example above.  You can do the same for the DBPedia, though I have encountered problems using it when there are commas in the resource name.  [I might not be the only person who has noticed this problem](http://stackoverflow.com/questions/39338506/handling-commas-when-using-a-namespace-prefix-in-a-sparql-where-clause)

```
PREFIX db:<http://dbpedia.org/resource/>

SELECT *
WHERE {
  db:your_article_here ?p ?o
}
LIMIT 200
```
