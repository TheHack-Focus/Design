# API Specification

Rev. 1.0

All entities encoded in requests and responses should be formatted in JSON unless explicitly specified.

## Account Management

### Register

- Endpoint: `/Account/Register`
- Method: POST

#### Required Parameters

- Email: `email`
- User name: `username`
- Password: `password`
- SecureElementPublicKey: `secureElementPublicKey`, reserved for further use.

#### Return

- HTTP 200 (OK) will be returned upon successful requests.
- Otherwise, the API returns HTTP 400 (Bad request) with an error message payload.

### Login

- Endpoint: `/Account/Login`
- Method: POST

#### Required Parameters

- Login Handle: `loginHandle`
- Password: `password`
- SecureElementPublicKey: `secureElementPublicKey`, reserved for further use.

#### Return

- HTTP 200 (OK) will be returned upon successful requests. An authentication token as well as refresh token, will be returned in body content. You can ignore it since everything is assumed in the hackathon.
