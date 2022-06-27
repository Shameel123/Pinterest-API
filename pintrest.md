# Register an App

First step is to get your app registered.
Go to:

`https://developers.pinterest.com/`

Click on `My Apps` at top right and follow the instructions to get your app registered.
Note: It takes couple of days for the app to get approved.

Once the app is created, go to the `Manage App` option and configure `Redirect URIs`.

**This is an important step, the code is returned at the Redirect URI that you mention here.**

# Getting the Code

Hit to following URL in the browser:
`https://www.pinterest.com/oauth/?client_id=<app-id>&redirect_uri=https://www.shameeluddin.com/&response_type=code&scope=boards:read,pins:read,boards:write,pins:write`

## Parameters:

### Client_ID

Enter your App ID.

### Ridrect_URI

This must containt the EXACT SAME URI that you have configured in your app on Pinterest.

### Scope

Please give your required scope in the scope key above.

For Example, if your fail to mention boards:write scope then you will be unable to create the board in your account.

### Access The Code

The code is returned on the `Redirect URI` so you must have access to the website.
For example, the code is going to be returned like this:
`https://www.shameeluddin.com/?code=38403d8b19dc0a37b0c59be1aca3481774bea8022`

# Obtaining Access Token

First execute this command `echo -n $client_id:$client_secret | base64` to get base64 result.

Enter this in Authorization Header Below.

**Make Sure To Enter Correct Code Extracted Earlier**

Simple CURL command is this:

```
curl -X POST https://api.pinterest.com/v5/oauth/token
--header 'Authorization: Basic {base64 encoded string made of client_id:client_secret}'
--header 'Content-Type: application/x-www-form-urlencoded'
--data-urlencode 'grant_type=authorization_code'
--data-urlencode 'code={YOUR_CODE}'
--data-urlencode 'redirect_uri=http://localhost/'
```

Note: This can also be very easily obtained via. `Postman`.

# API Links

Now that everything is obtained, use `OAuth2.0` in Postman.
Enter `Access Token`
Hit the APIs to perform CRUD operation on Board or Pin

## Boards

https://developers.pinterest.com/docs/api/v5/#tag/boards

## Pins

https://developers.pinterest.com/docs/api/v5/#tag/pins

## Media

https://developers.pinterest.com/docs/api/v5/#tag/media

## Catalogs

https://developers.pinterest.com/docs/api/v5/#tag/catalogs

## Ad Account

https://developers.pinterest.com/docs/api/v5/#tag/ad_accounts
