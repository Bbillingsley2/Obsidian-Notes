


DBMS - Database Management Systems

- Contains information about a particular enterprise 
	- collection of interrelated data
	- set of programs to access the data
	- an environment that is convenient and efficient to use

- University Database Example
	- Going to be revisited for most of the semester 
	- Application program examples
		- add new students, instructors, an courses
		- register students for courses and generate class rosters
		- assign grades to students
		- compute student grade point averages (GPAs)
		- generate transcripts for alumni

- Drawbacks of Using File System to Store Data 
	- Data redundancy and inconsistency 
		- multiple file formats
		- duplication of information across multiple files

	- Difficulty in Accessing Data
		- need to write a new computer program to accomplish each new task

	- Data isolation
		- multiple files and formats 

	- Security 
		- hard to provide a user to access to some, but not all, data 

	- Integrity Problems 
		- integrity constraints become buried in program code rather than stated explicitly 
		- hard to add new constraints or change existing ones

	- Atomicity of updates
		- failures may leave the database in an inconsistent state with partial updates carried out 
		- example: the transfer of funds from one account should either be complete or not happen at all 

	- Concurrent Access by Multiple Users
		- concurrent access is needed for performance 
		- uncontrolled concurrent access can lead to inconsistencies 
			- (two people reading a balance and each withdrawing money at the same time)

	- Database Management Systems offer solutions to all of these problems 


	- Levels of Abstraction 
		- Physical Level
			- describes how a record (e.g. a student) is stored on the file system
		- Logical Level
			- describes how data is stored in the database and the relationships among the different data points 
		- View Level 
			- application programs hide details of data types 

	- Instances and Schemas 
		- similar to types and variables in programming languages

		- Schema - the logical structure of the database 
			- ex: the database consists of information about a set of customers and accounts and the relationships between them
			- analogous to the type of information of a variable in a program

			- Physical schema - database design at the physical level
			- Logical schema - database design at the logical level

		- instance - the actual content of the database at a particular point in time 
			- analogous to the value of a variable 

		- physical data independence 
			- the ability to modify the physical schema without changing the logical schema 


	- Data Models 
		- a collection of tools for describing 
			- data
			- data relationships
			- data semantics
			- data constraints

		- relational model
		- entity - relationship model (used in database design)
		- object based model (object-oriented and object-relational)
		- semi-structured model (XML)
		- older models (network and hierarchical)

	- Data Manipulation Language (DML)
		- language for accessing and manipulating the data organized by the appropriate data model
			- also known as 'Query Language'

		- two typical classes or languages 
			- procedural - user specifies what data is required and how to get to the data 
			- declarative - user specifies what data is required without specifying how to get to the data 

		- SQL is the most widely used query language 


	- Data Definition Language (DDL)
		- Specification notation used for defining  the structure of the database 
			- ![[Screenshot 2023-08-23 at 3.02.40 PM.png]]
		- The DDL compiler generates a set of tables stored in a data dictionary 

		- Data Dictionary contains metadata (data about data)
			- database schema 
			- integrity constraints 
				- primary key (ID that uniquely identifies information)
				- Referential integrity (references constraints in DML)
					- ex: dept_name value in any instructor tuple must appear in a department relation
				- authorization 