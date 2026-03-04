# LEL Ontology – Ejemplo del Dominio de Aerolínea

Este repositorio contiene una representación basada en ontologías del **Léxico Extendido del Lenguaje (LEL)** aplicada a un **dominio de aerolínea**.

El proyecto fue desarrollado utilizando **Protégé** e incluye:

- el **LEL metamodel**
- una **Ontologia de dominio**
- **LEL indivíduos**
- generado automaticamente **Documentación HTML de la ontologia **

La ontología está destinada a apoyar investigaciones sobre **validación semántica de vocabularios de dominio en Ingeniería de Requisitos**.

---

# Repository Structure
```text
.
├── catalog-v001.xml
├── airline-lel.owl.properties
│
├── doc
│ ├── DL-axioms
│ │	└── Meta-modelo do LEL em Description Logic (DL).docx
│ └── Lel-glossary
│   └── Léxico Extendido del Lenguaje (LEL) – Línea Aérea.docx
│
│
├── domain
│ └── airline-lel.owl.ttl
│
├── individuals
│ └── airline-lel-individuals.ttl
│
├── metamodel
│ └── lel-metamodel.ttl
│
├── owl
│	├── index.html
│	├── classes.html
│	├── objectproperties.html
│	├── dataproperties.html
│	└── individuals.html
│
│
└── queries
  └── sparql.txt
````

### Main Files

| Archivo | Descripción |
|-----|-------------|
| `airline-lel.owl` | Proyecto principal de la ontología abierto en Protégé |
| `lel-metamodel.ttl` | Metamodelo central del LEL (TBox)  |
| `airline-lel-individuals.ttl` | Instancias del LEL (ABox) |
| `catalog-v001.xml` | Configuración de resolución de IRI |
| `airline-lel.owl.properties` | Configuración del proyecto en Protégé |
| `owl/` | Documentación HTML generada a partir de la ontología |
| `doc/` | Documentos con el LEL, entrada base para estructurar la ABox. DL proporciona la base teórica lógica para el razonamiento |

---

# Opening the Project in Protégé

## Step 1

Open **Protégé**.

Select:
File → Open 
Protégé cargará automáticamente las importaciones utilizando el archivo:

---

## Step 2

Después de cargar la ontología, deberían aparecer:

### Classes
````
LELSymbol
Notion
Impact
SubjectType
ObjectType
VerbType
StateType
````
### Object Properties
````
hasNotion
hasImpact
hasType
referencesSymbol
````

### Data Properties
````
symbolName
text
````
## Step 3

En Protégé, revisar en la sección **Classes** si aparecen clases del dominio de aerolínea como:
- Aeronave  
- Pasajero  
- Vuelo 
Si no aparecen:

1. Verificar en **Active Ontology** si el metamodelo está cargado.
2. Si no está, cargar manualmente: /metamodel/lel-metamodel.ttl

en **Direct Imports**.

Una vez cargado, todos los elementos de la **ABox** estarán disponibles en Protégé.

---

## Step 4

Cargar los individuos:
/individuals/airline-lel-individuals.ttl 


en **Direct Imports**.

Luego verificar en la pestaña **Individuals** si aparece una lista de elementos del LEL.

Si no aparece nada, intentar recargar la ontología:
File → Reload

---

# Capas de la Ontología

La ontología está estructurada en tres capas.

---

## 1. Metamodelo del LEL

Define la estructura conceptual del LEL:

- símbolos  
- nociones  
- impactos  
- tipos de símbolos  

Archivo:
metamodel/lel-metamodel.ttl


---


---

## 2. Ontología de Dominio

Especializa el metamodelo para el **dominio de aerolínea**.

Ejemplos de símbolos del LEL:

- Passenger  
- Flight  
- Reservation  
- Boarding  
- Ticket  

---

## 3. Individuos

Cada símbolo del LEL está representado por tres individuos principales.

Ejemplo:
````
Vuelo_LEL
Vuelo_Notion
Vuelo_Impact


Relationships:
Vuelo_LEL
hasNotion → Vuelo_Notion
hasImpact → Vuelo_Impact
hasType → objectType
````
Las descripciones textuales se almacenan utilizando propiedades de datos.

---

# Documentación de la Ontología

La carpeta:

contiene documentación HTML generada automáticamente a partir de la ontología.


Abrir:
owl/index.html 

para explorar:
````
- classes
- properties
- individuals
- relationships
````
en un navegador.

---

# Ejemplo SPARQL Query

En el Protégé abra:
SPARQL Query tab


Pege y execute:

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
```` 

Contexto de Investigación

Esta ontología forma parte de una investigación sobre:

Enriquecimiento semántico del Léxico Extendido del Lenguaje (LEL) mediante Lógicas de Descripción.

El objetivo es apoyar:

validación del vocabulario del dominio

detección de inconsistencias semánticas

soporte basado en ontologías para la ingeniería de requisitos.

Autor

Marc Marinho de Alcântara  
Universidad Nacional de La Plata (UNLP)
Magister en Ingeniería de Software - Fac. Ciencias Informáticas


