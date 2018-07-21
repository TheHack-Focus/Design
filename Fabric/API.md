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

## Message Queue

### Message Card

Message card is a JSON schema for messages in the application. An example of message card is presented below.

    {
        "timeStamp: "2018-07-20T23:21:39.1153429-07:00",
        "publisher": {
            "userId": "e2773914-8767-40fa-9f75-f63bb2885974",
            "userName": "John Appleseed"
        },
        "text": "Xcode sucks",
        "media": {
            "type": "Images",
            "images": [
                "https://example.com/image1.png",
                "https://example.com/image2.png"
            ],
            "videos": [
                "https://example.com/image1.mp4",
                "https://example.com/image2.mp4"
            ],
            "linkCards": [
                {
                    "title": "Twitter",
                    "preview": "现在的程序员怎么不测试的……",
                    "url": "https://twitter.com/tualatrix/status/1020541670587109377"
                }
            ]
        },
        "location": {
            "lat": 37.733795,
            "lon": -122.446747,
            "description": "The City and County of San Francisco"
        }
    }

There are some constraints in cards:

- **Either** Text or Media Node (`media`) could be `null`. Do not assume `media` is always present.
- Typically, only one type of media node will be presented.
- Media Type (`type`) should be one of `Images`, `Videos` or `LinkCards`.
- **Location** must present. Otherwise the card will be ignored.
