# OAuth2

```
  NB: Deep Linking API does not form part of the general TASS API framework.
  As such, it does not require the Encrypted Tokenisation outlined in the API Introduction
```

**flowchart outlining the authentication process using OAuth2.0 and PKCE security**
![image](https://user-images.githubusercontent.com/46773099/165877518-8832a71c-a900-441a-a7df-216eb4f1fe85.png)

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

**Scopes**

  * student_events
  * school_calendar
  * parent_notifications
  * acknowledge_parent_notification:write
  * parent_deeplink
  * students
  * student_ediary
  * calendar_categories
  * school_campuses
  * school_yeargroups
  * public_calendar


**TASS API Gateway Setup**

- Application ID
- Application Name
- Login Title
- Authorisation Title
- Redirect URI

**Postman - Authorization - Configuration Options Setup**

- Type: OAuth 2.0
- Header Prefix: Bearer
- Callback URL: same as "Redirect URI" from TASS Setup
- Client ID: same as "Application ID" from TASS Setup
- Scope: include all in the "Scopes" list, student_events, school_calendar, ...


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
  Authorisation Type: OAuth 2.0 "authorization code flow"
  Add Authorization Data to: Request Headers
  Header Prefix: Bearer
  Grant Type: Authorization Code (with PKCE)

- Example of an Authorisation request:
  Client ID: (TASS OAuth Application ID) (eg.tasslogintest)
  Client Secret: none
  Code Challenge Method: SHA-256
  Scope: See “OAuth 2 Scope” section of the spec.
  State: (user defined) ( not required , but recommended )  (Possible “testchangestate” for testing)

