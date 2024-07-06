## Mock data generation

This is small project for generating artificial / mock data, conforming to the specified DB schema.
It can be useful to either generate pseudo-realistic data in the database, or prepare large amounts of mock data for stress testing.


The package allows for generating mock data for specified database schema.

## Configuration file schema:

```  
{
  "connection": "postgresql+psycopg2://admin:test@172.17.0.1:5432/ChmielDB",
  "tables": {
        "Projects":{
        "id": "PK serial",
        "project_name": "first_name",
        "project_owner": "FK Users.id"
      },
      "Users": {
        "id": "PK serial",
        "first_name": "first_name",
        "last_name": "last_name",
        "email": "email UNIQUE",
        "password": "password",
        "role": "OPTION IN (USER, ADMIN)",
        "address": "address",
        "birth_date": "timestamp",
        "phone_number": "phone"
      },
      "IntermediaryTable: Projects_Users": {
        "project_id": "FK Projects.id",
        "user_id": "FK Users.id"
      },
  },
  "objects_count": {
    "Users": 25,
    "Projects": 10,
    "Projects_Users": 250,
  }
```


### Allowed column keywords:




#### Disclaimer:
The program only checks for uniqueness and integrity withing itself, there can still be error if there's already existing data in the database.
