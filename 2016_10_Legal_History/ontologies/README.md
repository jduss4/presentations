# Part 2: Ontology Workshop

For this part of the workshop, we'll be brainstorming how to create an ontology that will help us ask questions of the data.

You are welcome to use your own project for this brainstorming session, but if you would like to use OSCYS, I'll be handing out sample documents from a specific case.

- [Moses Graham v. Richard B. Alexander (caseid.0181)](http://earlywashingtondc.org/cases/oscys.caseid.0181)
- [The OSCYS ontology](http://earlywashingtondc.org/rdf/oscys.objectproperties.owl)
- The worksheet I'm passing out `OntologyWorksheet.pdf`

## Considerations for Ontology Creation

Here are some general things to consider when you start thinking about creating an ontology:

- Are there any existing ontologies that fit your data and questions or that could be extended to fit?
- Could these questions be answered with another technology better?
- What kind of research questions can you imagine asking of your dataset?

OSCYS focuses on the person to person relationships so that we can gather information like:

- which individuals were petitioners and against whom?
- list all the family relationships of a given person
- how many ways did person A and person B know one another?
- how many women were plaintiffs?

However, we could have created our ontology differently so that we could ask other types of questions through RDF:

- which cases took place in specific locations?
- which judges oversaw cases with a type of outcome?
- find which people appear in which documents throughout a case's duration

## Examples for Brainstorming an Ontology

You will notice that since we were concerned with describing relationships, our ontology has object properties like this (pseudo-code):

```
property: petitionerAgainst
    domain: person
    inverseOf: defendantAgainst
    subPropertyOf: legalRelationship
```

This way, we can not only find information about people petitioningAgainst other people, but we can draw further conclusions about their relationship from the ontology's definition.

However, if you wanted to describe cases and documents, more, you might prefer something more along these lines:

```
property: outcome
    domain: case
    # any other relevant information about what "outcome" means
# example:  case A > outcome > dismissed
```

or perhaps

```
property: hasJudge
    domain: case
    subPropertyOf: courtRole
# example: case A > hasJudge > William Cranch
```
