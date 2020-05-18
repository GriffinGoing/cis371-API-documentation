# CIS371: Journaling API Documentation

A Documentation assignment for a (soon to be not) hypothetical journaling API

## Resources to Manage

- **users** - Information about the people using the service. 
- **journalEntries** - The journal entries.
- **images** - Every image on the site with data about the image.
- **comments** - What other users have to say for each entry.
- **locations** - Where the entries were posted from.
- **permissions** - Who is able to view, modify, create, delete, etc. 

### users
Information about the people using the service. 

```
class user {
  int id;
  string name;
  list<entryId> journalEntries;
}
```

### journalEntries
The journal entries.

```
class journalEntry {
  int byUser;
  int entryId;
  int timeStamp;
  string entryText;
}
```

### images
Every image on the site with data about the image.

```
class image {
  int imageId;
  string about; 
}
```

### comments
What other users have to say for each entry.

```
class comments {
  int onPostId;
  list<comment> allPostComments;
}

class comment {
  string text;
  int fromUserId;
  int timeStamp;
}
```

### locations
Where the entries were posted from.

```
class location {
  int parentPostId;
  string location;
}
```

### permissions
Who is able to view, modify, create, delete, etc. 

```
class permission {
  list<int> viewableBy;
  list<int> modifiableBy;
  list<int> creatableBy;
  list<int> deletableBy;
}
```

## Endpoints

The behavior of and verbage/responses of endpoints.

### /user

- query user info
- update user info
- create new users
- delete user

#### Lookup info:
GET   /search/
GET   /user/1   Responses: 200 on Success, 404 (not found) otherwise

#### Replace info:
PUT   /user/1   Responses: 200, 404 (not found), 405 (not allowed)

#### New user:
POST    /user/new   Responses: 

#### Delete:
DELETE    /user/1   Responses: 
