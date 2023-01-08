# theindegenous-tech-Dummy_codebase
The Indegenous Library
Entire Full stack app.

Instruction for configuring the application for Development and testing:
clone the repo:
git clone https://github.com/theindegenous-tech/TheIndegenousLibrary.git

Setting up the database:
Install postgreSQL

Launch the postgreSQL shell using:

sudo -u postgres psql

this will login to the postgreSQL shell as user 'postgres'

Create the library database using:
CREATE DATABASE library;

create the admin role:
CREATE USER admin WITH PASSWORD 'admin';

The following commands sets up the database :
ALTER ROLE admin SET client_encoding TO 'utf8';

ALTER ROLE admin SET default_transaction_isolation TO 'read committed';

ALTER ROLE admin SET timezone TO 'UTC';

Grant permissions to admin:
 GRANT ALL PRIVILEGES ON DATABASE library TO admin;

Running the backend server:
The name of the django project is backend created using:

django-admin startproject <project_name>

Launch the virtual environment the below example is using pipenv however any virtual environment package can be used:
pipenv shell

It is recommended to use a virtual environment to set up the backend application in order to avoid any dependancy issue with other applications

Install all required dependencies from the requirements.txt file provided using:
pip install -r requirements.txt

From root, change directory to backend:
cd backend

Prepare the models for migrations using:

python manage.py makemigrations

Migrate the changes to the postgreSQL database using:
python manage.py migrate

Create the django superuser for manipulating the data via GUI using:
python manage.py createsuperuser

Follow the instructions and create a super user to access django-admin.

run the backend server using:
python manage.py runserver

This will run the server on port 8000

django-admin can be accessed via localhost:8000/admin

Login via the superuser credentials created in step 4

Running the frontend server:
from base directory, change directory to frontend. Then:

Install the required node modules using:
npm install

Start the app using npm start. This will host the app on port 3000.

access the website at localhost:3000

If all steps were followed and no errors were encountered, the app should be configured for development and testing.

Steps for starting the Backend server for the first time:
comment out lines in backend/the_indegenous_backend/api/views : 9->17 and 65->89
Follow steps 1 to 5 as usual. Reason: The code for the trie tree involves getting all the books and creating the datastructure for searching the books. This seems to run before the migrations of the models to the database thus interfering with the migration process. Upon completing the migration it should be uncommented to resume normal functionality.
