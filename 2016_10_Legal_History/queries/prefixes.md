# Prefixes

In order to make your queries shorter, you can put prefixes at the top, like in our Hello World example above.  You can do the same for the DBPedia, though I have encountered problems using it when there are commas in the resource name.  [I might not be the only person who has noticed this problem](http://stackoverflow.com/questions/39338506/handling-commas-when-using-a-namespace-prefix-in-a-sparql-where-clause)

In the [dbpedia sparqler](http://dbpedia.org/sparql):

```
PREFIX db:<http://dbpedia.org/resource/>

SELECT *
WHERE {
  db:your_article_here ?p ?o
}
LIMIT 200
```
