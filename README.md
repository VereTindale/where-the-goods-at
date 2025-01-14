# Urban Foraging 

## Final Project

Find the free food

## The Tech


* React
* Redux
* Express
* Knex
* Bootstrap
* JWT Auth

## User Stories

### MVP

As a non-registered user:
  * I want to see a google map container with login and register buttons in the nav.
  * I want to be able to filter through the items to forage and show them as pins on the google map and list them below.
  * I want to click on a pin and be shown information about the item to forage.

As a user:
  * I want to be able to register as a new user.
  * I want to be able to log in to my own account and see my profile.
  * I want to be able to add a new item.
  * I want to be able to update and delete my own item.
  * I want to be able to add an item and set it to public or private.
  * I want to be able to see a google map container which has the option of showing my private collection and my private collection plus everyone else’s entries. (filter)
  * I want to be able to search by keyword and see a google map container which shows them as pins and lists.

### Stretch

  * Pop up sign up or register form 10 seconds after landing on website
  * Add a rating and comment on other peoples items
  * Filter by seasonal availability
  * Filter by quantity (eg heaps of lemons)
  * Share with another user/friend
  * User points system
  * Email confirmation for sign up


  ---

## Views (Client Side)
  | name | purpose |
  | --- | --- |
  | Login | View for user to enter their login credentials |
  | Register | View for user to sign up for the App |
  | UserProfile | View to display map with users personal items with the ability to add/delete/update items |
  | CreateItem | View for user to add new item to their profile/map. This is a modal |
  | Map | View to display map listed items with this ability to filter (filter types: region, type, recently added, entered word) |
  | ItemLocationList | Displays filtered items in a list below the map saying location, img and other item info. |
  | PopUp | displays a pop up box after 10 seconds prompting the user to sign in/register if not logged in |


## Reducers (Client Side)

  | name | purpose |
  | --- | --- |
  | auth | Store information regarding user logins, auth status and auth errors |
  | publicItems | Store all items from db with public property set to true |
  | privateItems | Store all specific users items, after they have signed in |

 ## Actions

 ### Items
 | type | data | purpose |
 | --- | --- | --- |
 | PUBLIC | public item data | retreive the items from the server |
 | PRIVATE | private item data | retrieve the items from the server |



## API (Client - Server)

| Method | Endpoint | Protected | Usage | Response |
| --- | --- | --- | --- | --- |
| Post | /api/auth/login | Yes | Log In a User | The Users JWT Token |
| Post | /api/auth/register | Yes | Register a User | The Users JWT Token |
| Get | /api/v1/items | No | Get all publicly available items from db | An Array of items |
| Get | /api/v1/items/user | Yes | Get all private items for specific user from db | An Array of items |
| Post | /api/v1/items/add | Yes | Add a new item to db | The item that has been save in db read format |
| Patch | /api/v1/items/update | Yes | Edit an existing item in db | Item has been updated in db |
| Del | /api/v1/items/delete | Yes | Remove an item that belongs to this user | Item has been removed from db |

| Method | Endpoint | 
| --- | --- |
| Get | /api/v1/items | 

Response
`{ locationData: [ { 
          name: 'test', 
          description: 'test', 
          lat: 11.111111, 
          long: 22.2222222 }, 
          {...},
          ... ]}`


IGNORE STUFF UNDERNEATH
## DB (Server Side)
  There should be three tables for MVP

### Users
  | Column Name | Data Type |
  | --- | --- |
  | id | Integer |
  | user_name | String |
  | first_name | String |
  | last_name | String |
  | hash | text |

### Meetings
  | Column Name | Data Type |
  | --- | --- |
  | id | Integer |
  | meeting_name | String |
  | time | Timestamp |
  | attendees | integer |
  | cost | Decimal |

### Attendees (Join Table M2M)

  Many Users attend Many Meetings

 | Column Name | Data Type |
 | --- | --- |
 | user_id | Integer |
 | meeting_id | Integer |

 ---

## Setup

Run the following commands in your terminal:

```sh
npm install
npx knex migrate:latest
npx knex seed:run
mv .env.example .env
```

To run in development:
```sh
npm run dev
```

To run in production:
```sh
npm start
```


## Heroku!!!

### Creating your app

Create your app with `heroku create [name]`

You can check that this was successful by running `heroku apps` to view a list of your apps


### Adding postgres

Add postgresql (hobby dev) to your app at `https://dashboard.heroku.com/apps/[APP NAME HERE]/resources`

Check that pg has been added by running `heroku addons` to ensure the postgresql db is on your app


### Deploying!

I have created several npm scripts that will be useful for deploying your app to heroku easily.

To push your local master branch to your heroku app:
```sh
npm run h:deploy
```

Run heroku migrations:
```sh
npm run h:migrate
```

Run heroku seeds:
```sh
npm run h:seed
```

If ever you need to rollback, you can also:
```sh
npm run h:rollback
```


### Ta-Da!
Your app should be deployed!
