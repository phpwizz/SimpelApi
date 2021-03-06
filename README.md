# SimpleApi

Simplest api ever created with CRUD and token authentication

![](https://raw.githubusercontent.com/phpwizz/SimpleApi/master/logo.png)


![](https://img.shields.io/badge/version-v1.0-blue.svg) ![](https://img.shields.io/badge/size-16,8%20kB-blue.svg) ![](https://img.shields.io/badge/python-2.7-green.svg) ![](https://img.shields.io/badge/status-active-brightgreen.svg) ![](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)

## Documentation

[SimpleApi](#simpleapi)
  * [Documentation](#documentation)
  * [Features](#features)
  * [Getting Started](#getting-started)
    + [Prerequisites](#prerequisites)
    + [Installing](#installing)
  * [Running the tests](#running-the-tests)
      - [Generating authentication token](#generating-authentication-token)
      - [HTTP Request Method GET](#http-request-method-get)
      - [HTTP Request Method POST](#http-request-method-post)
      - [HTTP Request Method PUT](#http-request-method-put)
      - [HTTP Request Method DELETE](#http-request-method-delete)
  * [Deployment](#deployment)
  * [Built With](#built-with)
  * [Contributing](#contributing)
  * [Versioning](#versioning)
  * [Authors](#authors)
  * [License](#license)
  * [Acknowledgments](#acknowledgments)


## Features

* CRUD operations
* User authentication
* Tokens
* Limitation for api requests (default:300 requests per minute)

##### Features that comming in next version [v.1.0.1]

 * Upload files on server with Flask-Upload extension implemented


## Getting Started

SimpleApi is Flask application developed for fast development of simple APIs,this package uses SQLite3 as default database and SQLAlchemy to comunitcate with database.



### Prerequisites

For running this package you will need few other packages

```
pip install Redis
pip install Flask
pip install SQLAlchemy
pip install Flask-HTTPAuth
```
- Redis package is for limation on requests
- Flask package is micro-framework itself
- SQLAlchemy package is for communication with SQLite3 database
- Flask-HTTPAuth package is for authentication users and restricting routes with login required

### Installing

SimpleApi is easy to setup you just need to clone or download directory and run it as shown bellow


```
git clone https://github.com/phpwizz/SimpleApi.git
cd /dir/SimpleApi/
python views.py
```
And that is it ! Now you have your own api on [localhost:8080/api/v1/](http://localhost:8080/api/v1/ "localhost:8080/api/v1/")

## Running the tests

#### Generating authentication token

To generate token in SimpleApi you will first need to be logged in , for that you will first need to create account in 

http://localhost:8080/user/auth/token


Output:
```json

{

   "token" : "eyJhbGciOiJIUzI1NiI eyJhbGciOiJIUzI1NiIsImV4cCI6MTUzMTMxNzYxMSwiaWF0IjoxNTMxMzE3MDExfQ.eyJpZCI6MX0.N6KGiEivg3aZCWlkUPjNLNfphUmZx5ssXW56KoPakK0"

}



```

This token has expiration date of 600 minutes by default but that can be extended on more if is needed.

####  HTTP Request Method GET

Open any REST api client this tutorial will cover use of  [Advanced REST client](https://chrome.google.com/webstore/detail/advanced-rest-client/hgmloofddffdnphfgcellkdfbfbjeloo "Advanced REST ")


* Open a client application

* For methode chose GET

This will show JSON format for all users
```
For url put :  http://localhost:8080/api/v1/users
```
Output:
```json

{
  "Users": [
    {
      "id": 1, 
      "name": "Alex", 
      "picture": "https://thumbs.dreamstime.com/b/profile-icon-male-avatar-portrait-casual-person-silhouette-face-flat-design-vector-47075236.jpg", 
      "user_about": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.  ", 
      "username": "alex123"
    }, 
    {
      "id": 2, 
      "name": "Mark", 
      "picture": null, 
      "user_about": null, 
      "username": "marY2"
    }
  ]
}
```
####  HTTP Request Method POST

* Open a client application

* For methode chose POST

POST method in this package is used for creating new database entries  ex.register new user or creating a new post

Creating new user
```
For url put :  http://localhost:8080/api/v1/user/register/new
```
Set headers to Content-Type and application/json

Input:

```json
{
  "username": "test12",
  "password": "test2"
}
```
Output:
```json
{
"Created": "test12"
}
```
Application will respond with success message!

If you are familier with curl command you can do it this way
```
 curl -i -X POST -H 'Content-Type: application/json' -d '{"username":"1","password":"1"}' http://localhost:8080/api/v1/user/register/new

```

####  HTTP Request Method PUT
Info : For this step you need to have already registered user

* Open a client application

* For methode chose PUT

PUT method in this package is used for updatung already existent database entries  ex.change user name , change content for post

Updating user username
```
For url put :  http://localhost:8080/api/v1/user/id/1/edit/username
```
Set headers to Content-Type and application/json

Input:

```json
{
  "username": "changedusername"
}
```
Output:
```json
{
"username": "changedusername"
}
```
Application will respond with new value added for username!


####  HTTP Request Method DELETE


* Open a client application

* For methode chose DELETE

DELETE method in this package is used for removing  ex.users or posts

Removing user with specific id

* For url put :  http://localhost:8080/api/v1/user/id/1/delete

Set headers to Content-Type and application/json

Output:
```json
{
"Deleted": "Success"
}
```
Application will respond with success message!

Info: Same process can be applied for managing with posts!


## Deployment

[Tutorial for deploying any flask application on heroku](https://medium.com/the-andela-way/deploying-a-python-flask-app-to-heroku-41250bda27d0 "Tutorial for deploying any flask application on heroku")

## Built With

* [Flask](http://flask.pocoo.org/) - The micro-framework used
* [SQLAlchemy](http://docs.sqlalchemy.org/en/latest/) - Database communicator
* [Redis](https://redis.io//) - Used to set limitations on requests

## Contributing

Everyone is welcome to contribute to this project.

## Versioning

- Version : v1.0

## Authors

* **phpwizz** - [phpwizz](https://github.com/phpwizz)

On this link will be set all future [contributors](https://github.com/your/project/contributors).
The best contributers will be added as co-authors

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Flask official documantion
* Udacity course for APIs
* Logo icon: <div>Icons made by <a href="http://www.freepik.com" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/" title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a></div>

![](https://camo.githubusercontent.com/ba40cf893a8f6dcdc5d1db437564f634f3ca0b4a/68747470733a2f2f63646e2e7261776769742e636f6d2f61726374696369636573747564696f2f6e6f72642f646576656c6f702f7372632f6173736574732f62616e6e65722d666f6f7465722d6d6f756e7461696e732e737667)
