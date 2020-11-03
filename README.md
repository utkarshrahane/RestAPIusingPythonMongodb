# RestAPIusingPythonMongodb
This is a RESTful API for MongoDB (No-SQL). As this is a basic API, it has 4 basic functionalities of CRUD operations on the database: Create, Read, Update and Delete. The user will be able to perform the operations using the API and make changes to the database. Also to isolate the MongoDB server, we will dockerize the entire application in a container using Docker. For testing the API we would use Postman.

## Getting Started

### Setting Up Prerequisties
1. To install pip in your system, download [get-pip.py](https://bootstrap.pypa.io/get-pip.py) and run locate the current working directory to the file location. Execute this command on your terminal:
```
python get-pip.py
```
2. Now set up the environment by installing pymongo and flask server using pip on your terminal by executing:
```
pip install pymongo
pip install Flask
```
3. Navigate [here](https://www.docker.com/get-started) and download the latest version of Docker for your desktop.
4. Once downloaded, install docker on your system, to verify the installation you can execute this command on terminal:
```
docker -v
```
5. Install postman on your system by navigating to this [link](https://www.postman.com/downloads/).
6. You can use a tool like MongoDB Compass for understanding the schema and your database. You can navigate here to download [MongoDB Compass](https://www.mongodb.com/products/compass). Once donloaded, you can start MongoDB on your terminal and set the same port connection in MongoDB Compass for accessing local database.

### Installation
#### Using Git (Recommended)
1. Clone the project from github.
```
git clone https://github.com/utkarshrahane/RestAPIusingPythonMongodb.git
```
#### By downloading project manually
1. Download the repository.
2. Unzip the repository to the directory.




## Execution
* Make sure you open a seperate terminal or command prompt for your MongoDB and host it locally using:
```
mongod
```
### Host API locally without Docker
1. Change the working directory to the project folder path on the terminal using:
```
cd project-directory-path
```
Now deploy the flask server using the below stated command on the terminal.
```
python Rest_API_mongo.py
```
2. Open Postman. Select New request and select the type of request you want to test.
    | Plugin | README |
    | ------ | ------ |
    | HTTP GET | This method is used to read any resource. |
    | HTTP POST | This method is used to write any resource. |
    | HTTP PUT | This method is used to update any resource. |
    | HTTP DELETE | This method is used to delete any resource. |
    
3. Now, paste the URL for the request on which the flask server has been hosted, which in this case would be:
For Reading:
```
    http://localhost:5001/read
```
4. Select ```Body>raw>json``` from the window.
5. Now, based on the structure and name of database into consideration the format has to be edited.
```  
{
    "database": "products",
    "collection": "ecom_data" 
}
```
NOTE: Here, the name of my database is "products" and the collection(analogous to table in RDBMS) I am referring to is "ecom_data".
 6. Click Send, this will now fecth all the entries in the mentioned collection.
 
 ```read_get.jpg```


Similarly, the route and input for other operations is stated below.  
For Writing:```http://localhost:5001/write```
```
{
    "database": "products",
    "collection": "ecom_data",
    "Document": {
        "name": "Wildcraft Bagpack",
        "brand_name": "Wildcraft",
        "regular_price_value": 11,
        "offer_price_value": 10,
        "currency": "GBP",
        "classification_l1": "bagpack",
        "classification_l2": "trekking",
        "classification_l3": "",
        "classification_l4": "",
        "image_url": "https://www.flipkart.com/wildcraft-flip-ruck-1-rucksack-45-l/p/itmf6dhgbtvjqsdu?"
    }
}
```
```write.jpg```

For Updating:```http://localhost:5001/update```
```
{
    "database": "products",
    "collection": "ecom_data",
    "Filter": {
        "name": "Wildcraft Bagpack"
    },
    "DataToBeUpdated": {
        "offer_price_value": 11
    }
}
```
```update.jpg```

For Deleting:```http://localhost:5001/delete```
```
{
    "database": "products",
    "collection": "ecom_data",
    "Filter": {
        "name": "Wildcraft Bagpack"
    }
}
```
```delete.jpg```

### Deploying and hosting application with Docker
1. Now, to host the entire application we will use two containers and to link them to each other, we have to use the ```docker-compose``` file along with ```Dockerfile``` that has been defined within the repository.
2. To build the containers and run them, use:
```
    docker-compose run --build
    docker-compose run
```
3.Once done, execute:
```
docker-compose up
```
