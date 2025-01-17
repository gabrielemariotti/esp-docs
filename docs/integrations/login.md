# Login

The next step is to authenticate with the service you are integrating (SPID/CIE) then you have to build an address formed by different parameters.

> **GET environment_name/login_file.php**

#### Parameters

Name | Description
------------- | -------------
 **domain_uri** | The ESP domain uri
 **environment_name** | The environment path
 **login_file** | The login file used for the authentication (like cielogin-spidlogin)
 **final_url** | It's the redirect url called at the end of the authentication process (It should be comunicated during the assessment phase)
 **level** | It's the authentication level (L1-L2-L3)
 **attributes** | It's the attribute level (Base-Full)
 **authnKey** | It's the authn key that has been given at the [getkey](./getkey.md) endpoint


## Result

The address that is constructed must then be copied and pasted into the address bar of a browser. The page that opens can be
- login screen with SPID
- login screen with CIE

## Login Succeded

After a succeded login the user will be redirected to the final url parameter. 
The parameters that will be returned with querystring should be:

- a session id and user key parameter, if the configuration has redirect type set to `TOKEN`. Now you have to call the [token](./token.md) API, if you want the JSON Web Token

- a jwt token parameter, if the configuration has redirect type set to `JWT`. Now you have the JWT with the user info. You can see an example of this JWT at the [token](./token.md) section.
