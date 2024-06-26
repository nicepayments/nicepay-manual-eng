## Access token

<br>

### Over-view
- Use when calling API with Bearer token HTTP authentication.
- The token is valid for 30 minutes.   
- Therefore, after the initial token is generated, the same token will be returned for 30 minutes, and if a new token is requested after 30 minutes, a newly generated token will be issued.  

<br>

### Access token API Call example

```shell
curl --location --request POST 'https://api.nicepay.co.kr/v1/access-token' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic UjFfNzc5ODhmMzMxYTFhNDExYjhlMjE1ZDA3ZTJkZGRmNWM6YmUwZDdlMDBiZjQzNGJhMWJiZWM3ZjgyNzY2MmFiMzA=' \
```

```shell
{
    "resultCode": "0000",
    "resultMsg": "정상 처리되었습니다.",
    "accessToken": "dc51c8b13620519b8503bef6ee18f11370e8b349",
    "tokenType": "Bearer",
    "expireAt": "2023-02-28T13:23:17.655+0900",
    "now": "2023-02-28T12:53:17.657+0900"
}
```

<br>

### Access token API request parameter

```bash
POST /v1/access-token
HTTP/1.1
Host: api.nicepay.co.kr
Authorization: Basic <credentials>  or Bearer <token>
Content-type: application/json;charset=utf-8
```

|   Parameter   |  type  | required  | byte | Description  |
|:-------------:|:------:|:---------:|:----:|:-------------|
| returnCharSet | String |           |  10  | Response encoding <br> utf-8 or euc-kr <br> Default:utf-8 |

<br>

### Access token API reseponse (Body)
```bash
Content-type: application/json
```
|  Parameter  |  type  | required  | byte | Description  |
|:-----------:|:------:|:---------:|:----:|:-------------|
| resultCode  | String |  O  |  4   | Response code<br>0000:success, other failures  |
|  resultMsg  | String |  O  | 100  | Result message  |
| accessToken | String |  O  |  40  | Access token  |
|  tokenType  | String |  O  |  10  | Authentication Scheme Type <br> 'Bearer' fixed  |
|  expiredAt  | String |  O  |      | Token expiration time<br>ISO 8601 format |
|     now     | String |  O  |      | Current time<br> ISO 8601 format |
| messageSource | String | |  | nicepay: Response message generated by nicepay  <br> external: Response message generated by 3rd partner|