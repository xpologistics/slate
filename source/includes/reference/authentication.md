# Authentication

The XPO [API](https://en.wikipedia.org/wiki/Application_programming_interface) is a [REST API](https://en.wikipedia.org/wiki/Representational_state_transfer) that returns a [JSON](https://www.json.org/) value.  In order to make an authenticated call to the API, you must include your [access token](https://en.wikipedia.org/wiki/Access_token) with the call.

## Registering Appliction

To use the XPO API, XPO partners must request access credentials through through their XPO representative, who will grant the credentials including:

* `CLIENT_ID`
* `CLIENT_SECRET`

Once you have these special values that are created just for you, and should be appropriately guarded, you are able to use curl from the command line to get an access token.  This should work on any operating system, however you may need to install curl if it is not already installed.

There are ways to call REST APIs from any computer language.  You do not have to use curl.  But to test your access to the API, curl is one very easy way.  Another way would be to use Postman.

Here, we show you how to call our API using simple curl commands.  Once you know how to connect with curl, you can then translate the call into your chosen programming language.

## Call the Authentication Server (Token Server) to get ACCESS_TOKEN

- In this example request, replace CLIENT_ID and CLIENT_SECRET with your own keys that you received from XPO.

> Request

```shell
curl "https://login.authxpo.com/connect/token"
  -d -s "grant_type=client_credentials&client_id=CLIENT_ID&client_secret=CLIENT_SECRET&scope=connect-orders"
```

> Response

```json
{
  "access_token":"ACCESS_TOKEN",
  "expires_in":3600,
  "token_type":"Bearer"
}
```

- The ACCESS_TOKEN value will be a long string of characters.  We are using ACCESS_TOKEN as a stand-in for your real value.

## Call the API itself with your ACCESS_TOKEN.

- Here is an example API call that you can try out.  Don't forget to replace ACCESS_TOKEN with the actual value you got in the last call.

> Request

```shell
curl -s -X GET \
  https://connect.xpo.com/36/timesTen \
  -H 'Authorization: Bearer ACCESS_TOKEN' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
	clientId: "xpo-auth-client", Name: "Wow", allowOfflineAccess: "1", applicationTypeId: 2, "accessTokenLifetime": 400
}'
```

> Response

```
{
  "title":"XPO Connect API",
  "timesTen":360
}
```

## Double check the security (Optional)

- Notice that if you change the ACCESS_TOKEN value at all, or leave it off, the call will not work.
