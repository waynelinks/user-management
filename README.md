# User Management
## Manage Users and Loyalty them.

- knexfile.ts 
```ts
 connection: {
    host: 'localhost',
    port: 5433,
    user: 'postgres',
    password: 'docker',
    database: 'postgres',
},

```


## Dashboard Routes
|Method|Path|Description|
|---|---|---|
|**GET**|```/users```|get the users list ordered by id|
|**POST**|```/users```|create a new user|
|**PUT**|```/user<id>```|update an user by id|
|**DELETE**|```/user<id>```|delete an user by id|

 - ### GET
    - Header Authorization
      ```Authorization: Bearer <token>```

      **token must be valid. See:**
      <a href="/">How to get a token</a>
      
      
    - Query Params
    
      |Param|Description|Required|Example|
      |---|---|---|---|
      |**page**|Defines the page|false|```/users?page=2```|
      
    - Response Example
       
       200 - Success
       ```json
       {
         "data": 
         [
           {
             "name": "Carlos Kauãn Moreira de Sousa",
             "phone": "5585992476020",
             "bought": 500,
             "notes": "Estudando back-end",
             "created_at": "2020-11-16T19:22:56.065Z",
             "id": 3
           },
           {
             "name": "Carlos Kauãn",
             "phone": "5585992476020",
             "bought": 500,
             "notes": "Estudando back-end",
             "created_at": "2020-11-16T19:22:56.065Z",
             "id": 2
           },

         ],
         "total": 1
       }
       ```
  

 - ### POST
     |Field|Description|Type|
     |---|---|---|
     |**name**|user name|string|
     |**phone**|user phone|string|
     |**bought**|how much user bought|number|
     |**notes**|notes about user|string|

     - Header Authorization

       ```Authorization: Bearer <token>```

       **token must be valid. See:**
       <a href="/">How to get a token</a>
     - Request Example

        ```json
          {
            "name": "Carlos",
            "phone": "5585992476020",
            "bought": 650,
            "notes": "Estudando"
          }

        ```
      - Response Example

         201 - Success
         ```json
          {
             "id": 34,
             "name": "Carlos",
             "phone": "5585992476020",
             "bought": 650,
             "notes": "Estudando",
             "created_at": "2020-11-16T18:23:54.381Z"
          }
         ```
         
         **See:** <a href="/">Error Docs</a>
         
- ### PUT
 
    - Header Authorization
      ```Authorization: Bearer <token>```

      **token must be valid. See:**
      <a href="/">How to get a token</a>
      
    - Request Example

      ```json
        {
          "name": "José Silva",
          "bought": 1000
        }
      ```

    - Response Example

       201 - Success: Returns the updated user.
       ```json
        {
          "id": 36,
          "name": "José Silva",
          "phone": "5585992476020",
          "bought": 1000,
          "notes": "Estudando back-end",
          "created_at": "2020-11-16T19:22:56.065Z"
        }
       ```

       **See:** <a href="/">Error Docs</a>

## Admin Routes
|Method|Path|Description|
|---|---|---|
|**POST**|```/sign```|register a new admin|
|**GET**|```/login```|login into admin account|

  - ### GET
     - Header Authorization
     
       ```Authorization: Basic <basic64credentials>```

        - Encoded: ```Authorization: Basic Y2FybG9za2F1YW5AZ21haWwuY29tOmNhcmxvczEyMw==```

        - Decoded: ```Authorization: Basic carloskauan@gmail.com:carlos123 ```
     
     - Response Example
     
        201 - Success
        ```json
         {
            "id": "4802f5a1-7e53-4c4c-8f60-e1c7ec4c161b",
            "name": "Carlos Kauãn",
            "email": "carloskauan@gmail.com",
            "token": "<token>"
          }
        ```
        
        **See:** <a href="/">Error Docs</a>
        
  - ### POST
      |Field|Description|type|
      |---|---|---|
      |**name**|admin name|string|
      |**email**|admin email|string|
      |**password**|admin password|string|
      
      - Header Authorization
      
        ```Authorization: Bearer <token>```
        
        **token must be a valid superuser. See:**
        <a href="/">How to get a admin token</a>
      - Request Example
      
         ```json
          {
            "name": "Carlos Kauãn",
            "email": "carloskauan@gmail.com",
            "password": "carlos123"
          }

         ```
       - Response Example
       
          201 - Success
          ```json
            {
              "id": "0554ec30-db86-4109-ae7d-0a3169e6a831",
              "name": "Carlos Kauãn",
              "email": "carloskauan@gmail.com",
              "token": "<token>"
            }
          ```
          **See:** <a href="/">Error Docs</a>
