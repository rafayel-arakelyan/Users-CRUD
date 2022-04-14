# UsersCrud

#### You need to create a simple USERS Crud app. 
#### Use Angular material for design.
#### You should use routing and implement 3 main pages.


### 1. Users list page
Here you should show brief information of all users (`name` and `email`) in list format. <br>
On each user item there should be a `delete` button to remove that particular user. <br>
On each user item there should be an `edit` button which will navigate to `Update User` page for that particular user. <br>
There should be `Add user` button at the bottom of the list, it should navigate to `Add user` page.<br>
There should be `Drop users` button to delete all users by one click.

### 2. Add User page
In this page you will have a form to create a user.

form fields are as follows:
  - name: required field
  - email: required field, should be valid email
  - street: required field
  - city: required field
  - phones: this should use FormArray and should have `+` button under the input field to add more fields dynamically. At least one phone number is required, also phone number should be valid and match following pattern: '+' sign following by 8-12 numbers.
  
Make sure you have error messages for invalid fields.<br>

There should be `create` button which will submit the form and create a user.
After successfully creating a user you should be automatically navigated to `Users list` page.

### 3. Update user page
In this page you will have a form to update user. The form should be populated with selected user's data automatically.<br>
Then you can change values.<br>
all the validations are same as in `Add user` page.<br>

There should be `update` button which will submit the form and update the user.
After successfully updating a user you should be automatically navigated to `Users list` page.

#### You are free to implemnt additional features: (asking for confirmation before deleting user, multi selection in users list to perform bulk actions and so on).

<br><br><br>

# Backend API

## User Schema

Below represented the interface and validations of user model in backend <br>
format is `key: type (validations)`

 - name: string (required)
 - email: string (required, unique, validEmail)
 - address:
   - street: string (required)        
   - city: string (required)
 - phones: string[] (at least one item required, pattern: `+` following with 8-12 numbers)
  
<br>
<br>

## CRUD Endpoints

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




