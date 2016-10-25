# The Random Article DBPedia Challenge!

## Step 1: Basic Query

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

## Step 2: Limiting Results with Predicates

Try to find a little more information about your topic by narrowing in on one predicate.  Pick something that appears in the first column of your results and sub it in here instead of subdivisionName predicate:

```
SELECT *
WHERE {
 <http://dbpedia.org/resource/{your_article_here}> <http://dbpedia.org/property/subdivisionName> ?o
  
}
LIMIT 100
```

## Step 3: Exploring with Predicates

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
