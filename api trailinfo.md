# trailinfo object

<!-- This is a sample object for use in my imaginary application, AppRoach. AppRoach is all about getting the climber from their house, to the rocks! Part of the app should handle approach trail data.  -->

This object stores all the information related to trails. 

| Attribute | Data Type | Description |
| --- | --- | --- |
| id | string | unique identifier |
| name | string | name of the trail
| length | nullable integer | length of the trail |
| elevation | nullable integer | elevation gain of the trail |

The following are available for trailinfo:  
**GET** /trailinfo/{id}  
**GET** /trailinfo   
**POST** /trailinfo  
**PUT** /trailinfo/{id}  
**DELETE** /trailinfo/{id}

## Getting one specific trail info: **GET** /trailinfo/{id}

For users who already know which climb they wish to go to, this function selects a specific trail, and returns that trail's information.  
This is expected to be the most common use case for a dedicated climber, who has a particular climb in mind.  

*Note*: GETs trailinfo object by id. The user is expected to select a trail by name in the UI, but translation layer between **id** and **name** parameters are handled by the frontend application.

| Parameters | Data Type | Description | Conditional |
| ---: | --- | --- | -- |
| id  | string | unique identifier of the trail | required |

Request:  
``` 
curl https://example.apiserver.com/trailinfo/{trail_one}  
```  
Response: returns trailinfo object after successfully accessing trail data.
```
{
    "id": "trail_one",
    "name": "Example Trail Name",
    "length": "123456789",
    "elevation": "987654321"
}
```
## Getting info for all trails: **GET** /trailinfo

For users who have a general area in mind, but not one specific destination. This function returns all trailinfo for all trails.  
The expected use case is for a climber who does not have a particular destination in mind. This would be expected for a climber who is new to an area.

*Note*: GETs all trailinfo available in backend. Frontend application is expected to handle display UI and sorting methodology.

| Parameters | Data Type | Description | Conditional |
| ---: | --- | --- | -- |
| none   | n/a | n/a | n/a |

Request:  
``` 
curl https://example.apiserver.com/trailinfo  
```  
Response: returns all trailinfo after successfully accessing data. Data is returned sorted by **id**.
```
{
    "id": "trail_one",
    "name": "Example Trail Name",
    "length": "123456789",
    "elevation": "987654321"
},
{
    // more trails, etc.
}
```
## Creating a new trail: **POST** /trailinfo

Used to create new trails.  
Specific administrators will have app functionality unlocked to be allowed to define new trails. Not expected for a general user.

| Parameters | Data Type | Description | Conditional |
| ---: | --- | --- | -- |
| name  | string | name of the trail | required |
| length | integer | length of the trail | optional |
| elevation | integer | elevation gain of the trail | optional |

Request:  
``` 
curl https://example.apiserver.com/trailinfo/
    -d name="Example New Trail Name"
    -d length="1234"
``` 
Response: returns trailinfo object after successfully creating a new trail. 
```
{
    "id": "new_trail_id",
    "name": "Example New Trail Name",
    "length": "1234",
    "elevation": "null"
}
```
## Updating an existing trail: **PUT** /trailinfo/{id}

Used to update data in existing trails.  
Specific administrators will have app functionality unlocked to be allowed to define new trails. Not expected for a general user.

| Parameters | Data Type | Description | Conditional |
| ---: | --- | --- | -- |
| id | string | unique identifier of the trail | required |
| name  | string | name of the trail | optional |
| length | integer | length of the trail | optional |
| elevation | integer | elevation gain of the trail | optional |

Request:  
``` 
curl -X PUT https://example.apiserver.com/trailinfo/{new_trail_id}  
    -d elevation="4321"
```   
Response: returns trailinfo object after successfully updating a  trail. 
```
{
    "id": "new_trail_id",
    "name": "Example New Trail Name",
    "length": "1234",
    "elevation": "4321"
}
```
## Deleting an existing trail: **DELETE** /trailinfo/{id}

Used to delete an existing trail. Trails may close, and land access could change over time, and the app should not list trails that are no longer accessible.   
Specific administrators will have app functionality unlocked to be allowed to delete existing trails. Not expected for a general user.

| Parameters | Data Type | Description | Conditional |
| ---: | --- | --- | -- |
| id  | string | id of trail | required |

Request:  
``` 
curl -X DELETE https://example.apiserver.com/trailinfo/{new_trail_id}
```   
Response: returns an object with a deleted parameter set to true. 
```
{
    "id": "new_trail_id",
    "deleted": true
}
```