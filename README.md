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

Cacheable: 1 hour, as the user object links to their journalEntries

```
class user {
  int id;
  string name;
  list<entryId> journalEntries;
}
```

### journalEntries
The journal entries.

Cacheable: One Day, as entries don't frequently change once posted.

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

Cacheable: One Week, as images will not likely change, but may in some cases.

```
class image {
  int imageId;
  string about; 
}
```

### comments
What other users have to say for each entry.

Cacheable: 10 minutes at most, assuming new comments are frequently posted. 

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

Cacheable: Yes, and immutable, as locations should rarely (if ever) change. 

```
class location {
  int parentPostId;
  string location;
}
```

### permissions
Who is able to view, modify, create, delete, etc. 

Cacheable: Hell no, always pull from the API. 

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

### /journalEntries
- query journal entries
- update entries
- create new entry
- delete entry

### /images
- query image(s)
- update an images text
- create new image
- delete image

### /comments
- query comments
- update a comment (edit)
- add (create) new comment
- delete comment

### /locations
- query location(s)
- update a location
- add a new location
- delete location (the circumstances surrounding such an action concern me...)
