# Authentication

> To authorize, use this code:

```ruby
require 'xpo'

api = xpo::APIClient.authorize!('XPO_AUTH_KEY')
```

```python
import xpoApi

api = xpoApi.authorize('XPO_AUTH_KEY')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: XPO_AUTH_KEY"
```

```javascript
const xpoApi = require('xpo');

let api = xpoApi.authorize('XPO_AUTH_KEY');
```

> Make sure to replace `XPO_AUTH_KEY` with your API key.

The XPO API is JSON based. In order to make an authenticated call to the API, you must include your access token with the call. OAuth2 uses a BEARER token that is passed along in an Authorization header.

## Registering Appliction

In order to use the XPO API, you must be a current XPO partner. To request access to the API please contact your XPO represenative.

Your XPO representative, will provide you with two keys:

* `APPLICATION_ID`
* `APPLICATION_SECRET`

## Authorization Code with Refresh Token
