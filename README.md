# CollegeConnect
An app that connects high schoolers applying to college with college students

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
An app for high school students to connect with undergraduate college students and learn about the universities through real student experiences. 

HS = high school student(s)
C = college student(s)

### App Evaluation
- **Category:** Social, education
- **Mobile:** Mobile experience allows for instant messaging, push notifications, and potentially location sharing. 
- **Story:** Encourages high school students to be more proactive in their college search by reaching out to older college students who have been in their shoes before. Encourages real dialogue between real students that contrasts official, biased university-curated marketing. 
- **Market:** High school students (juniors, seniors) who care about making good college choices, college students who want to help others and talk openly about their experiences
- **Habit:** High school juniors and seniors especially will be using this every week or so during application season, and so college students will do the same. 
- **Scope:** 

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* User can sign up with a HS or C account
* User can log in/log out
* User can view their own profile
* HS can search for college by name
    * HS can see basic info about the college (*CollegeAI API*)
    * HS can see list of C at that college
* HS can start conversation with C from C's profile
* Users can have live chats

**Optional Nice-to-have Stories**

* C can share pinned location with HS to meet up on campus (*GoogleMaps SDK*)
* HS can view photo albums for that college, i.e. dorms, food, campus / C can add to photo albums
* * User can receive push notifications (contact adding and DMs)
* Users can call each other
* HS can leave a public review for C

### 2. Screen Archetypes

* Sign-up
   * User can create a new HS/C account and put in info about themselves

* Log-in
   * User can log into existing account (*persistence?*)
   
* Search (for HS)
   * HS can search for college by name

* College details
    * Users can view info about a specific college and which students from the college are on the app

* All conversations
    * Users can view all their ongoing conversations

* Conversation
    * User can view previous chat messages between another user with live updates

* Profile
    * Users can view their own or another's profile

* Start conversation
    * HS is prompted to start a conversation with C

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Search (*HS*) / College info (*C*)
* Conversations
* Profile

**Flow Navigation** (Screen to Screen)

* Search tab
   * goes to college details activity
   * clicking on a college user card goes to their profile
   * clicking on "Start conversation" opens start conversation activity
* All conversations tab
    * clicking on a conversation opens specific conversation activity with another user
    
 ## Wireframes
[Add picture of your hand sketched wireframes in this section]
<img src="https://github.com/janelle-cheung/CollegeConnect/blob/master/Wireframe.pdf" width=600>

## Schema 
### Models
User
| Property                     | Type         | Description |
| --------                     | --------     | -------- |
| objectId                     | String       | unique user id |
| type                         | String       | "high school" or "college" |
| name                         | String       | user's name |
| profileImage                 | File         | user's profile image |
| password                     | String       | user's password |
| email                        | String       | user's email |
| from                         | String       | user's hometown |
| college                      | String       | user's current college |
| high school                  | String       | user's (current or past) high school |
| about                        | String       | user's bio |
| grade                        | String       | user's grade (freshman, sophomore, etc) |
| academicInterests            | List<String> | user's academic interests |
| extracurricularsInterests    | List<String> | user's extracurricular interests |
| collegeUnitId                | String       | user's current college's unit id in CollegeAPI |
   
Message
| Property              | Type                  | Description |
| --------              | --------              | -------- |
| objectId              | String                | unique message id |
| body                  | String                | body of the message |
| conversation          | ConversationPointer   | pointer to Conversation that the message is in |
| sender                | UserPointer           | pointer to User that sent the message |
   
Conversation
| Property              | Type                  | Description |
| --------              | --------              | -------- |
| objectId              | String                | unique conversation id |
| highSchoolStudent     | UserPointer           | pointer to high school student in conversation |
| collegeStudent        | UserPointer           | pointer to college student in conversation |
| meetLocation          | LatLng                | coordinates of a location to meet up, set by collegeStudent |
   
CollegeMedia
| Property              | Type                  | Description |
| --------              | --------              | -------- |
| objectId              | String                | unique college media id | 
| file                  | File                  | file containing uploaded media (photo/video) |
| caption               | String                | caption of the media (optional) |  
| user                  | UserPointer           | pointer to user who uploaded the media | 
| albumName             | String                | name of the album the media is in (dorms, food, etc.) |
| collegeUnitId         | String                | unit id in CollegeAPI of the college that the media was uploaded for |  

### Networking
- [Add list of network requests by screen ]
- [Create basic snippets for each Parse network request]
- [OPTIONAL: List endpoints if using existing API such as Yelp]
