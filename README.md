# LEL Ontology – Airline Example

This repository contains an ontology-based representation of the **Extended Language Lexicon (LEL)** applied to an **airline domain**.

The project was developed using **Protégé** and includes:

- the **LEL metamodel**
- a **domain ontology**
- **LEL individuals**
- automatically generated **HTML ontology documentation**

The ontology is intended to support research on **semantic validation of domain vocabularies in Requirements Engineering**.

---

```markdown
## Repository Structure

```text
/
  catalog-v001.xml
  airline-lel.owl
  airline-lel.owl.properties
  metamodel/
    lel-metamodel.ttl
  individuals/
    airline-lel-individuals.ttl
  owl/
    index.html
    classes.html
    objectproperties.html
    dataproperties.html
    individuals.html


### Main Files

| File | Description |
|-----|-------------|
| `airline-lel.owl` | Main ontology project opened by Protégé |
| `lel-metamodel.ttl` | Core LEL metamodel (TBox) |
| `airline-lel-individuals.ttl` | LEL instances (ABox) |
| `catalog-v001.xml` | IRI resolution configuration |
| `airline-lel.owl.properties` | Protégé project configuration |
| `owl/` | HTML documentation generated from the ontology |

---

# Opening the Project in Protégé

## Step 1

Open **Protégé**.

Select:
File → Open
Protégé will automatically load the imports using the file:

---

## Step 2

After loading the ontology you should see:

### Classes
LELSymbol
Notion
Impact
SubjectType
ObjectType
VerbType
StateType

### Object Properties
hasNotion
hasImpact
hasType
referencesSymbol


### Data Properties
symbolName
text


---

# Ontology Layers

The ontology is structured in three layers.

### 1. LEL Metamodel

Defines the conceptual structure of the LEL:

- symbols
- notions
- impacts
- symbol types

File:
metamodel/lel-metamodel.ttl


---

### 2. Domain Ontology

Specializes the metamodel for the **airline domain**.

Examples of LEL symbols:

- Passenger
- Flight
- Reservation
- Boarding
- Ticket

---

### 3. Individuals

Each LEL symbol is represented by three main individuals:

Example:
Vuelo_LEL
Vuelo_Notion
Vuelo_Impact


Relationships:
Vuelo_LEL
hasNotion → Vuelo_Notion
hasImpact → Vuelo_Impact
hasType → objectType

Text descriptions are stored using:

---

# Ontology Documentation

The folder:

contains HTML documentation automatically generated from the ontology.

Open:
owl/index.html 


to explore:

- classes
- properties
- individuals
- relationships

in a browser.

---

# Example SPARQL Query

In Protégé open:
SPARQL Query tab


Run:

```sparql
PREFIX lel: <http://ontologies.mgis.unlp.org/lel-metamodel#>
PREFIX : <http://ontologies.mgis.unlp.org/airline-lel#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT ?symbol ?type ?notionText ?impactText
WHERE {

?symbol rdf:type lel:LELSymbol ;
lel:hasType ?typeInd ;
lel:hasNotion ?notion ;
lel:hasImpact ?impact .

?typeInd rdf:type ?type .

?notion lel:text ?notionText .
?impact lel:text ?impactText .

}
ORDER BY ?type ?symbol

Research Context

This ontology is part of research on:

Semantic enrichment of the Extended Language Lexicon (LEL) using Description Logics

The objective is to support:

validation of domain vocabulary

detection of semantic inconsistencies

ontology-based support for requirements engineering.

Author

Marc Marinho de Alcântara
Universidad Nacional de La Plata (UNLP)

