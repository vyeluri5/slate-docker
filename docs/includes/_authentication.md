# Authentication

## Retrieve Access Token

```shell
curl --request POST \
  --url /account/api/auth/token/{merchantId} \
  --header 'Content-Type: application/json' \
  --data '{
	"clientId":"a440b2cb0d4cdeaeae57956f7c01cc7d",
	"clientSecret":"ef56c373-13cd-478d-b5ec-ec48e9f9884f"
}
```

> The above command returns JSON structured like this:

```json
{
    "merchantId": "7a0a190e08f804b1dda81fcbf6000c53",
    "token": "45993268f6d74fce8184a8b5bb875fac",
    "expiry": 43200
}
```

> Replace `merchantId`,`clientId`,`clientSecret` with your registered merchant account Id and API app credentials from your Merchant Portal.

Qubyk Marketplace uses clientId and clientSecret to generate authorization key. Login to your merchant account [click here](https://portal.qubyk.com/) under API section to register your Client App and access keys.

### HTTP Request

`POST /account/api/auth/token/{merchantId}`

### URL Parameters
Parameter | Required | Description
--------- | ------- | -----------
merchantId | Yes   | unique id created entire to Qubyk Marketplace

### Request Body (Json)
Parameter | Required | Description
--------- | ------- | -----------
clientId | Yes   | Your registered Client Id
clientSecret | Yes   | Your registered Client Secret


<aside class="notice">
    Each AccessToken allows up to 12 hours of access to our API's. Send a request to above resource with API App credentials to regenerate new token. 
</aside>
<aside class="warning">
    Regenerate client API App credentails (Client Id and Secret) from merchant portal in case your credentails are compromised.
</aside>
