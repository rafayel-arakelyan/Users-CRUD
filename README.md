# UsersCrud

###You need to create a simple USERS Crud app.
You should use routing and implement 3 main pages.

###1. Users list
Here you will see brief information of all users `name` and `email` in list format.
On each user item there should be a button to remove that particular user.
On each user item there should be a `see more` button which will navigate to `Update User` page
There should be `Add user` button at the bottom of the list, it should navigate to `Add user` page.

###2. Add User
Here you will have a form to create a user.

form fields are as follows:
  name: required field
  email: required field, should be valid email
  street: required field
  city: required field
  phones: this should use FormArray and should have `+` button near to input to add more phone numbers, at least one phone number is required, also phone   number should be valid and match following pattern: '+' sign following by 8-12 numbers
  Make sure you have error messages for invalid fields.

###3. Update user
Here you will have a form which will be populated from selected user.
Then you can change values and hit save.
all the validations are same as in `Add user` page



#Backend API

<br>
<br>

## User Schema

Below represented the interface of user <br>
First goes key, then value type, then validations

 - name: string (required)
 - email: string (required, unique, validEmail)
 - address:
   - street: string (required)        
   - city: string (required)
 - phones: string[] (at least one item required, pattern: `+` following with 8-12 numbers)
  
<br>
<br>

##### `Get all users`
GET - http://52.14.58.85:4000/api/users

Description: Fetches all users. However user model is not complete for this endpoint, only few properties are present like `name` and `email`. 

Example Response Model
```
[
  {
    _id: 'cq9wqjwv9q77'
    name: 'Rafayel Arakelyan',
    email: 'rafayel@mail.ru',
  },
  
  {
    _id: 'p1d8c66faas'
    name: 'Robert Soxoyan',
    email: 'robert@mail.ru',
  }
]
```

##### `Get user by ID`
GET - http://52.14.58.85:4000/api/users/[id]

Description: Fetches specific user. User model is more detailed when you fetch specific user, you receive `address` and `phones` in addition to `name` and `email`. 

Example Response Model
```
{
  _id: 'cq9wqjwv9q77',
  name: 'Rafayel Arakelyan',
  email: 'rafayel@mail.ru',
  address: {
    street: 'Tumanyan',
    city: 'Yerevan',
  },
  phones: ['+37477111111', '+37477222222']
}
```
  
##### `Create user`
POST - http://52.14.58.85:4000/api/users

Description: Creates a new user with given payload and return it in response. There are few validations for payload on backend side, see User schema above.

Example Payload Model
```
{
  name: 'Arman Ayvazyan',
  email: 'arman@mail.ru',
  address: {
    street: 'Isahakyan',
    city: 'Gyumri',
  },
  phones: ['+37477555555', '+37477666666']
}
```

Example Response Model
```
{
  _id: 'a90qwq9fjj9qw'
  name: 'Arman Ayvazyan',
  email: 'arman@mail.ru',
  address: {
    street: 'Isahakyan',
    city: 'Gyumri',
  },
  phones: ['+37477555555', '+37477666666']
}
```

##### `Update user by ID`
PATCH - http://52.14.58.85:4000/api/users/[id]

Description: Updates existing user by ID. Payload can be the complete or partial user model. There are few validations for payload on backend side, see User schema above.

Example Payload Model
```
{
  name: 'Arman Sahakyan',
  phones: ['+37443000000']
}
```

Example Response Model
```
{
  _id: 'a90qwq9fjj9qw'
  name: 'Arman Sahakyan',
  email: 'arman@mail.ru',
  address: {
    street: 'Isahakyan',
    city: 'Gyumri',
  },
  phones: ['+37443000000']
}
```
  
##### `Delete user by ID`
DELETE - http://52.14.58.85:4000/api/users/[id]

Description: Deletes user by ID. There is no response.


<br>
<br>




