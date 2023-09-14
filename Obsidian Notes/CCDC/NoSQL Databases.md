
- Provision still needs work.
- Made up of denoramlized data.
- Do not have cross-table relationships
- Where traditional databases supported data access across tables with a single query, NoSQL options require additional tools or functions to make calls to multiple tables at once.
- Types:
		- Key Value
		- Column Based
		- Document Based

#### Amazon DynamoDB:
- Less focus on building and architecting the underlying system, and more ability to focus on performance
- Directly manage the level of performace you want to achieve through adjustments to the read and write capacity units
- The table in DynamoDB is a collection of zero or more items that can be queried through their keys. The items themseleves are made up of attributes which are the values associated with the keys that are set up for the table. The only required attribute for all items is the primary key or the partition key.
- When creating the table, you immediately need to specify the partition key that you are going to use. 
- You can choose the attribute type that is used by the table.
- You also have the ability to update your items by modifying any of the attributes or adding additionla fields or attributes.
- When reading the item, you have the option to do a strongly or an eventually consistent read. The type of read you request is going to impact your performance.
- Strongly consistent reads are heavier and your throughput needs to be higher in order to handle the same number of operations as when working with eventually consistent reads.
- While the table size does not have a certain limit, the individual items do. The max item size for DynamoDB is 400 kilobytes.
- The min key length for partition and sort keys are 1 byte. The max key length for partition key is 2048 bytes and the max key length for a sort key is 1024 bytes.
- AWS has an IDE called AWS Cloud9 that will allow you to run commands to list, add, etc. to your table.
		- the command to list all of your tables is `aws dynamodb list-tables`
		- the command to add an item, you will run `aws dynamodb put-item --table-name [tablename] --item file://[file name]`
		- in order to query a table in the database, you have to provide something called a key condition expression which is what is used to allow us to search the table for items that have certain partition and sort key values that match our input.
		- if i wanted to query the table named Music, for an artist name that is stored inside a variable in a file, the command would be `aws dynamodb query --table-name Music --key-condition-expression "Artist :[variable name]" --expression-attribute-values file:// [filename]`
		-  if i wanted to query the table named Music for an artist name and a song title (primary key and sort key) that are stored in variables in a file the command would be `aws dynamodb query --table-name Music --key-condition-expression "Artist = :[variable name] AND SongTitle = :v2" --expression-attribute-values file:// [filename]`
		- if you want to delete an item, you have to specify the partition key and the sort key. the command would be `aws dynamodb delete-item --table-name [tablename] --key file:// [filename]` to delete an item which values are stored in a file
		- 