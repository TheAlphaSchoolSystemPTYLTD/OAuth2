**getSchoolYearGroups**
----
  Returns the School Year Groups in JSON format.

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `codeonly [bool]`
   
   **Optional:**
 
   none

   **Conditional:**

   none

* **Success Response:**
    
    `codeonly:true`

    ```javascript
    {
	    "yeargroups": [
	        -5,
	        -4,
	        -3,
	        -2,
	        -1,
	        0,
	        1,
	        2,
	        3,
	        4,
	        5,
	        6,
	        7,
	        8,
	        9,
	        10,
	        11,
	        12
	    ],
	    "__invalid": {},
	    "__status": "success",
	    "__tassversion": "01.058.03.000"
	}
	```

  `codeonly:false`

    ```javascript
	{
	    "yeargroups": [
	        {
	            "code": -5,
	            "desc": "DD"
	        },
	        {
	            "code": -4,
	            "desc": "CC"
	        },
	        {
	            "code": -3,
	            "desc": "BB"
	        },
	        {
	            "code": -2,
	            "desc": "PK"
	        },
	        {
	            "code": -1,
	            "desc": "K"
	        },
	        {
	            "code": 0,
	            "desc": "P"
	        },
	        {
	            "code": 1,
	            "desc": 1
	        },
	        {
	            "code": 2,
	            "desc": 2
	        },
	        {
	            "code": 3,
	            "desc": 3
	        }
	        ....
	    ],
	    "__invalid": {},
	    "__status": "success",
	    "__tassversion": "01.058.03.000"
	}
	```
 
* **Error Response:**

    Required `[field_name]` not supplied
    ```javascript
     "error_description": "'codeonly' IS REQUIRED"
    ```
    
    Bool `[field_name]` not a valid boolean
    ```javascript
     "error_description": "'codeonly' MUST BE 'true' or 'false'"
    ```
    
* **Sample Parameters:**

  ```javascript
    { "codeonly" : true }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getSchoolYearGroups&appcode=DEMOCAL&company=10&v=2&token=nb3QZurfruc1oEsFRAHeUFij5yf8M7mzO1vPmh7giNc%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
      <input type="hidden" name="method" value="getSchoolYearGroups">
      <input type="hidden" name="appcode" value="DEMOCAL">
      <input type="hidden" name="company" value="10">
      <input type="hidden" name="v" value="2">
      <textarea name="token">nb3QZurfruc1oEsFRAHeUFij5yf8M7mzO1vPmh7giNc=</textarea>
    </form>
  ```