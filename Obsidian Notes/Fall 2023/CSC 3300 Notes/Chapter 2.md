
### Attribute Types

- The set of allowed values for each attribute is called the domain of the attribute 
- Attribute values are (normally) required to be atomic, that is, indivisible 
- The special value, *null*, is a member of every domain
	- It causes complications in the definition of many operations 


### Relation Schema and Instance

- A1, A2, A3, ... , An are attributes 
- R = (A1, A2, A3, ... , An) is an relation schema 
	- Example: Instructor = (ID, Name, Dept_Name, Salary)

- The current values (relation instance) of a relation are specified by a table
	- The element t, of r is a tuple and is represented by a row in a table

- Order of tuples are irrelevant 
	- they may be stored in any arbitrary order 


### Database

- A database consists of multiple relations
- Information about an enterprise is broken up into parts:
- For a university those parts might include:
	- Instructors
	- Students
	- Advisors 
	- Classes
	- Buildings 


- Bad Design
	- Storing everything in one record
	- Univ (Instructor_ID, Name, Dept_name, Salary, Student_ID, Building)
		- This results in repetition of information (like two students having the same instructor)
		- The need for null values (a student with no advisor)

- Normalization Theory (Chapter 7)
	- How to design "good" relational schemes 


### Keys

- Let K be a proper subset of R
	- K is a Superkey of R if values for K are sufficient to identify a unique tuple of each possible relation r(R)
	- Superkey K is a Candidate Key if K is minimal
	- One of the candidate Keys is selected to be the primary key - which one?

- Foreign Key constraint 
	- Value in one relation must appear in the other
	- Referencing relation
	- Referenced relation 

- Schema Diagram for University Database 
	- ![[Screenshot 2023-08-28 at 2.53.26 PM.png]]

### Relational Query Language 

- Procedural (imperative) vs Non-Procedural (declarative)
	- Imperative - C, Python, Java
	- Declarative - SQL, R, Ruby, Haskell

- "Pure" Languages 
	- Relational Algebra 
	- Tuple Relational Calculus
	- Domain Relational Calculus 

- Relational Operators
	- Select 
	- Project
	- Join

#### Selection of Tuples

- ![[Screenshot 2023-08-28 at 3.06.43 PM.png]]

	- The select statement says to get everything where A=B and D > 5 in the relation r
#### Selection of Attributes 

- ![[Screenshot 2023-08-28 at 3.07.54 PM.png]]


#### Joining Two Relations - Cartesian Product 

- ![[Screenshot 2023-08-28 at 3.13.56 PM.png]]


#### Joining Two Relations - Natural Join

- 