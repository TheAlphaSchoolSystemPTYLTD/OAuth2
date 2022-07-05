# OAuth2

```
  Knowledge of this code flow is important to understand how to correctly authorise an OAuth 2 connection.
  Details are found here: https://oauth.net/2/pkce/
```

**flowchart outlining the authentication process using OAuth2.0 and PKCE security**
![image](https://user-images.githubusercontent.com/46773099/165877623-d82203d1-46e5-40f3-8faa-5e195a6045b3.png)

**Methods**

  * getStudentEvents
  * getSchoolCalendar
  * getParentNotifications
  * setAcknowledgeParentNotification
  * getParentDeepLinkURL
  * getStudents
  * getStudentEDiary
  * getCalendarCategories
  * GetSchoolCampuses
  * getSchoolYearGroups
  * GetPublicCalendar

**TASS API Gateway Setup**

- Application ID
- Application Name
- Login Title
- Authorisation Title
- Redirect URI

**URLs required to authenticate and authorise the OAuth 2 connection**

- Core URLs required for base functionality:
  - Authorize: https://{site's domain}/tassweb/api/parent/oauth/authorize/index.cfm
  - Token: https://{site's domain}/tassweb/api/parent/oauth/token/index.cfm

- Utility URLs (Using a combination of these URLs desirable to provide standard OAuth behaviour):
  - Introspect: https://{site's domain}/tassweb/api/parent/oauth/introspect/index.cfm
  - Logout: https://{site's domain}/tassweb/api/parent/oauth/logout/index.cfm
  - Revoke: https://{site's domain}/tassweb/api/parent/oauth/revoke/index.cfm
  - Userinfo: https://{site's domain}/tassweb/api/parent/oauth/userinfo/index.cfm

- Core URLs required for base functionality:
  - Callback (optional): https://{site's domain}/tassweb/api/parent/oauth/callback/index.cfm
  - Verify (optional): https://{site's domain}/tassweb/api/parent/oauth/verify/index.cfm

- Additional information regarding implementation:
  - Authorisation Type: OAuth 2.0 "authorization code flow"
  - Add Authorization Data to: Request Headers
  - Header Prefix: Bearer
  - Grant Type: Authorization Code (with PKCE)

- Example of an Authorisation request:
  - Client ID: (TASS OAuth Application ID) (eg.tasslogintest)
  - Client Secret: none
  - Code Challenge Method: SHA-256
  - Scope: See “OAuth 2 Scope” section of the spec.
  - State: (user defined) ( not required , but recommended )  (Possible “testchangestate” for testing)

**Postman - Authorization - Configuration Options Setup**

- Type: OAuth 2.0
- Header Prefix: Bearer
- Callback URL: same as "Redirect URI" from TASS Setup
- Client ID: same as "Application ID" from TASS Setup
- Scope: include all in the "Scopes" list, student_events, school_calendar, ...

**Scopes**
```
  Knowledge of the “scope” is required to determine what data is returned to the API based on “permission based” data points.  

  OAuth2 “scope” would need to be passed as a list of the endpoints you would like the parent / app to have access to. Using this list we will present the parent with a brief description of the information the app would have access to and once they have authenticated and authorised the app to have access, only the included scopes would be available as endpoint calls when using the access_token provided.

  These are user defined and outlined below.

  Details are found here: https://oauth.net/2/scope/
```
  * student_events
    - Method: getStudentEvents
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: Student Events
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/mobile-app/blob/master/getStudentToursAndExcursions.md
      - Note: Keys renamed to “Events” instead of “Tours”.

  * school_calendar
    - Method: getSchoolCalendar
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: N/A
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/mobile-app/blob/master/getSchoolCalendar.md

  * parent_notifications
    - Method: getParentNotifications
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: Parent Notifications
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/mobile-app/blob/master/getNotifications.md

  * acknowledge_parent_notification:write
    - Method: setAcknowledgeParentNotification
    - Return Type: Structure
    - Parent Facing Description: N/A
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/mobile-app/blob/master/setAcknowledgeNotification.md

  * parent_deeplink
    - Method: getParentDeepLinkURL
    - Return Type: Structure
    - Parent Facing Description: Parent Lounge Access
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/mobile-app/blob/master/getDeepLinkURL.md 

  * students
    - Method: getStudents
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: Student General Details
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/mobile-app/blob/master/getStudents.md

  * student_ediary
    - Method: getStudentEDiary
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: Student eDiary
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/mobile-app/blob/master/getStudentEDiary.md

  * calendar_categories
    - Method: getCalendarCategories
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: N/A
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/school-calendar-and-notices/blob/master/getCategories.md

  * school_campuses
    - Method: GetSchoolCampuses
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: N/A
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/school-calendar-and-notices/blob/master/getCampuses.md

  * school_yeargroups
    - Method: getSchoolYearGroups
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: N/A
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/school-calendar-and-notices/blob/master/getYearGroups.md

  * public_calendar
    - Method: GetPublicCalendar
    - Return Type: Structure with an Array of Structures
    - Parent Facing Description: N/A
    - Reference: https://github.com/TheAlphaSchoolSystemPTYLTD/public-calendar-and-notices/blob/master/getPublicCalendar.md


