# MongoDB-tutorial

MongoDB is NoSQL database. Everything in MongoDB is managed in the form of documents. The data type specified for a field in one document need not be same for other documents.

To learn about MongoDB use below links:

https://beginnersbook.com/2017/09/mongodb-tutorial/

M1001 course available in MongoDB university
https://university.mongodb.com/courses/M001/about

Installation of MongoDB
-----------------------
Go to mongodb site and install msi file. update path environment variable with mongodb bin folder.

The executable files for mongodb server is "mongod" -> this will start the server at port 2701. We can start the server using mongod command or we can use servers from MongoDB Atlas which is a cloud management for MongoDB. From Atlas, we can connect to Mongo shell (Command line for MongoDB) and Mongo Compass (UI interface for MongoDB).

To execute commands, open another command prompt type use "mongo" executable. This is a way of accessing Mongo shell.

MongoDB commands:
----------------
1. to create database use "use" command as shown below

        use <database-name>
        eg: use hockey

  it first checks whether hockey database is avaialble or not. If it is available it switches to hockey database or it will create hockey database and switch to it.
 
2. to know current using database use "db" command

        db
        It gives current using database name as output

3. to delete database use below command

        db.dropDatabase();


4. for NoSQL database, the data stores as a collection. so to create collection use below command

        eg: db.players.insert( 
            {
              "id": 1,
	            "name": "Ram"
            }
            );
  
  here db indicates current database which is hockey and players is a collection. if it is already available it uses that collection to insert or else it will create a         collection called "players"
  
  insert function is to insert the documents into mentioned collection. we can insert bulk information as well.
  
5. to view collections use below command

        show collections;

        eg: show collections;
            players
            system.indexes
   
6. to view specific collection information use below command

        eg: db.players.find();
        
    this will display all the documents information present in players collection. to view the information in pretty print use below command
	
        eg: db.players.find().pretty();
 
7. to view the first document present in collection, use below command

        eg: db.players.findOne();

8. To remove document from collection use below command

        eg: db.players.remove( 
		          {"_id": "unique object id" }
	          )
    
9. To update document information in a collection use below command

        eg: db.players.update (
            {"_id": "unique object id to identity the document"},
		        {
		          // document info 
		          "id": 1
		          "name: "Rahul"
		        }
           )
	 
10. to remove collection from database use below command

        eg: db.players.drop();

   now view collections information in hockey db with below command
   
   show collections;
   
   system.indexes
   
   now players collection is dropped from hockey database
   
11. to find documents with specific search criteria we can mention body in find function as shown below

        eg: db.players.find(
              "id": 1
            )
	
	this gives documents whose id is 1
	
  To specify or condition, we can use $or as shown below

      eg:	db.players.find(
	        	$or: [
	          		"position": "Left wing",
		        	"position": "Right wing"
	        	]
	        )
	
	this will give documents whose position is either left wing or right wing
	
eg: to specify greater than or less than or not equal or greater than equal or less than equal conditions we can use below dollar operator

          db.players.find(
	          "age": {$gt:30} -> this indicates age greater than 30
          )	 
	 
	      $gt - greater than
	      $gte - greater than or equal
	      $lt - less than
	      $lte - less than or equal
	      $ne - not equal
	 
eg: to view only specific information in the document, not all the information we can use below

    db.players.find(
	   "position": "Left wing", -> this is search criteria
	   "name":1,_id:0 -> this indicates what to display as output, we want only name and _id:0 indicates it will not display _id parameter in the output
	)
	
eg: to limit the output count, we can use limit function

      db.players.find(
        "position": "Left wing" -> search criteria
      ).limit(3);

  this will limit the output to only first 3 entries
  
eg: to skip the entries in output, we can use skip function

        db.players.find(
          "position": "Left wing" -> search criteria
        ).skip(2);
   
   this will skip first two entries
