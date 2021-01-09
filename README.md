## Udacity Full Stack Web Developer Nanodegree Capstone Project 

## UdaciMarket Management System
### Temporary Location at https://udacimarket-grocery-system.herokuapp.com/
#
### Setting up the Application


#### Python 3.7

Follow instructions to install Python 3.7 for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)


#### Run setup.sh

A bash script, `setup.sh`, is an initial setup script located in the root of the project. The script assumes that Python 3.7 is installed and defaulted on your machine, and you are starting out fresh from cloning the project. This script will take care of creating the virtual environment, installing application dependencies, generating a `.env`, configuration file which will not be checked into the repository, and creating and setting up both the database and test database for the application. Before opening the browser and running the application at http://localhost:8181, please make sure that the database password is included in the .env file just created.

The following is a little deeper discussion of what the `setup.sh` is doing:


* #### Virtual Enviornment

Running the app in an virtual environment is highly recommended. This keeps the dependencies for the project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)


* #### PIP Dependencies

Once the virtual environment is setup and running, we can install application dependencies by naviging to the root of the project and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages within the `requirements.txt` file.


* #### Key Dependencies

- [Flask](http://flask.pocoo.org/) is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we"ll use handle the lightweight sqlite database. You"ll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we"ll use to handle cross origin requests from our frontend server. 

- [Flask-Swagger-UI](https://github.com/swagger-api/swagger-ui) is a collection of HTML, JavaScript, and CSS assets that dynamically generate beautiful documentation from a Swagger-compliant API.

- [Flask-Migrate](https://flask-migrate.readthedocs.io/en/latest/) is used for SQLAlchemy database migrations for Flask applications using Alembic.

- [Flask-Authlib-Client](https://docs.authlib.org/en/latest/client/flask.html) is a Flask extension that adds support for separate authorization/resource servers. It extends authlib's flask integration.

- [Python-Jose-Cryptodome](https://pypi.org/project/python-jose-cryptodome/) is a JOSE, which is a framework intened to provide a method to securely transfer claims between parties, implementation in Python using pycryptodome instead pycrypto.


* #### Database Setup
With Postgres running, restore a database using the grocery.sql file provided. From the backend folder in terminal run:

```bash
psql grocery_market < grocery.psql
```


* #### Configuration File Setup
A `.env` file for defining the following configuation parameters is required to be able to successfully build the project, and the file needs to be resided in the root of the project. This file will be ignored by GIT. 

The following parameters are required for the `.env` file.

- AUTH0_DOMAIN
- ALGORITHMS
- CLIENT_ID
- CLIENT_SECRET
- API_AUDIENCE
- ACCESS_TOKEN_URL
- AUTHORIZE_URL
- CALLBACK_URL
- SQLALCHEMY_TRACK_MODIFICATIONS=False
- POSTGRES.HOST=127.0.0.1
- POSTGRES.PORT=5432
- POSTGRES.USER=postgres
- POSTGRES.PASSWD=
- POSTGRES.DB=grocery_market
- POSTGRES.DB_TEST=grocery_market_test
- SECRET_KEY=
- JWT_PAYLOAD=jwt_payload
- PROFILE_KEY=profile
- TOKENA_KEY=id_key
- TOKENB_KEY=access_key
- SWAGGER_URL=/swagger
- API_URL=/static/swagger.json
- ITEMS_PER_PAGE=15
- TEST_TOKEN


### Running the application

First ensure you are working using your created virtual environment; then to run the application, execute the following command at the root of the project:

```bash
python app.py
```


### Endpoints

Endpoints information is documented via Swagger UI and can be accessed by appending `/swagger` to the host address, for example, http://localhost:8181/swagger.


### Error Handling

Errors are returned in their coressponding webpages:

The error codes currently used are:

* 400 – Bad Request
* 401 - Unauthorized
* 403 - Forbidden
* 404 – Not Found
* 405 - Method Not Allowed
* 422 – Unprocessable
* 500 – Something's Not Right
* AuthError - Authentication and/or Authorization Error


### Testing

To run the tests, run:
```
dropdb grocery_market_test
createdb grocery_market_test
psql grocery_market_test < grocery.sql
python test_api.py
```


* #### Postman Routing Tests

Both the Postman routing tests and their results can be found in two json files located in the root directory of the project; they are `udacity-fsnd-udacimarket.postman_collection.json` and `udacity-fsnd-udacimarket.postman_test_run.json`, respectively.

Helpful Notes for Postman testing:
> Please make sure you have the latest versions of Node.js and Postman installed on your machine. The Postman version is 7.36.1, and the Node.js version is 14.15.4 during development of this application and have proven to be working well.

> If you receive a Parser Error because of the header size. You could include the `NODE_OPTIONS` parameter in your machine's environment and enter the value `--max-http-header-size=32768`, or set the variable as the following in command prompt `NODE_OPTIONS=--max-http-header-size=32768`. 32,768, in bytes, (32kb) is the header size allowed for each request and/or response in Postman.


* #### Application Testers

Following is the Auth0 login information for several dummy accounts for testing:
```
(Role: MarketManager - Full permissions)
username: apptest2099@gmail.com
password: ..011iAmlegend235,,

(Role: MarketEmployee - Partial permissions)
username: apptest1024@yandex.com
password: ..011iAmlegend235,,

(Role: MarketCustomer - No permission)
username: apptest0512@yahoo.com
password: ..011iAmlegend235,,
```