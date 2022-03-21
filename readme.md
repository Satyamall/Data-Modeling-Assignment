
# 1. What are valid ways to represent this one-to-many relationship in MongoDB?

 - One-To-Many (1:N) The 1:N relationship describes a relationship where one side can have more than one relationship while the reverse relationship can only be single sided. An example is a Blog where a blog might have many Comments but a Comment is only related to a single Blog.

 # 2. What are valid ways on modelling many-to-many relationship with MongoDB?

  - A many-to-many relationship occurs when multiple records in a table are associated with multiple records in another table. For example, a many-to-many relationship exists between customers and products: customers can purchase various products, and products can be purchased by many customers.

# 3. What are valid ways to represent a one-to-one relationship with the document model in MongoDB?

 - This page describes a data model that uses embedded documents to describe a one-to-one relationship between connected data. Embedding connected data in a single document can reduce the number of read operations required to obtain data. In general, you should structure your schema so your application receives all of its required information in a single read operation.

# 4. create an ERD / CRD diagram for a blog application

 - ![download](https://user-images.githubusercontent.com/80479635/159255586-93a95a82-eb36-4a76-9380-f8a292000545.png)

# 5. create and design schema for each collection

 - Blog Collection
 ```js
 {
_id : ...
Title : ...
PostTime : ... 
nLikes : ...
NumComments : ...,
Author : { 
      UserId : ...,
      ProfilePic : ..., 
      Name : ....
}
...
}
 ```

Comment Collection
```js
{
 _id : ...,
 BlogId : ... // Reference to blogs
 PostTime : ... ,
 Text : ... 
  Author : { 
      UserId : ...,
      ProfilePic : ..., 
      Name : ....
}
,
nLikes : ...
}
```

Likes Collection
```js
{
 _id : ...,
 ReferenceId : ... // Reference to blogs or comments
 LikeTime : ... ,
  Author : { 
      UserId : ...,
      ProfilePic : ..., 
      Name : ....
}
```

# 6. Write a requirement document for designing a system like LinkedIn.

 - Define the Purpose With an Outline (Or Use an SRS Template) Your first step is to create an outline for your software requirements specification. ...
 - Define your Product's Purpose. ...
 - Describe What You Will Build. ...
 - Detail Your Specific Requirements. ...
 - Deliver for Approval.

# 7. Estimate daily read and writes, users, data transfer, list down all assumptions you have made

- ![download (1)](https://user-images.githubusercontent.com/80479635/159255626-69892f01-4582-4f78-bb14-5f445e83a3d8.png)

# 8. Write down some queries ( no need to write actual queries, but the kind of information that users, and admins would like to see ). for example: - list 10 post by user_id with pagination descending order of date
```js
const per_page=10;
const page = req.query.page || 1;
const skip = page < 0 ? 0 : (page - 1)*per_page;
db.users.find({},{user_id: 1}).sort({date: -1}).limit(10).skip(skip);
```
