# [DB]E-R Model

## Main concepts
- Entities
  - entity types 
  - entity sets
- Attributes
  - simple
  - composite
  - mutivalued
- Relations
  - relationship types
  - relationship sets

## Entities 和 Attributes

### Type of Attributes 
- Simple
- Composite
- Multi-valued

### Entity Type 和 Key Attribute

Entity Type : Entities with the same basic attributes are grouped or typed into an entity type.
- An entity type may have more than one key
- ER diagrams : 
  - An entity type is displayed in a rectangular box

Key Attribute : An attribute of an entity type for which each entity must have a unique value is called a key attribute of the entity type.
- A key attribute may be composite.
- Each key is <ins>underlined</ins>
- ER diagrams : 
  - Attributes are displayed in ovals
  - Multivalued attributes displayed in double ovals

### Entity Set

Definition : Entity set is the **current state** of the entities of that type that are stored in the database

### Weak Entity Types

Definition : 
- An entity that does not have a key attribute
- A weak entity must participate in an identifying relationship type with an owner or identifying entity type

## Relationship

### Relationship Type 和 Relationship Set

Relationship Type : Is the schema description of a relationship
- A relationship type can have attributes

Relationship Set : The **current state** of a relationship type

ER diagrams : 
  - Diamond-shaped box is used to display a relationship type
  - Connected to the participating entity types via straight lines

Constrains :
  - Cardinality Ratio 
    - One-to-one (1:1)
    - One-to-many (1:N) or Many-to-one (N:1)
    - Many-tomany (M:N)
  - Existence Dependency Constraint 
    - zero
    - one or more 
  
ER diagrams : 
- Cardinality ratio : Shown by placing appropriate numbers on the relationship edges.
- Participation constraint : Total shown by double line, partial by single line.
  


### Recursive Relationship Type

Definition : An relationship type whose with the same participating entity type in **distinct roles**

- ER diagrams : 
  - Need to display role names to distinguish participations.




