# JSONServer + auth

MockWebAPI (JSON Server) with WebAPI authentication in Node.js.

## Install

```bash
$ npm install
$ npm run api:auth
```

## Login API

```
POST http://localhost:3000/users/login
```

### Request ContentType

```
Content-Type: application/json
```

### Request Body

```
{
  "email": "hoge@email.com",
  "password":"hoge"
}
```

### Response Body (200 OK)

```
{
   "access_token": "XXXXXXXXXXXXXXXX"
}
```

## Auth Required API

```
GET     http://localhost:3000/users
GET     http://localhost:3000/users/1
POST    http://localhost:3000/users
PUT     http://localhost:3000/users/1
DELETE  http://localhost:3000/users/1
```

## Auth Request Header (required access_token)

```
Authorization: Bearer XXXXXX
```

### Response Body (401 Unauthorized)

```
{
  "status": 401,
  "message": "Error access_token is revoked"
}
```
