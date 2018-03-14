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

### Resources

Uses OAuth 2:
https://security.stackexchange.com/questions/108662/why-is-bearer-required-before-the-token-in-authorization-header-in-a-http-re

JSON Web Tokens (Basics/JWT)
By signing we can just validate this token is sent by a particular identity server.
https://medium.com/@piraveenaparalogarajah/json-web-tokens-jwt-basics-6515b13077e8

Preflight requests with CORS
https://github.com/angular/angular/issues/7445
http://restlet.com/company/blog/2015/12/15/understanding-and-using-cors/
https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

```
npm install cors
```

todo:
//const middlewares = jsonServer.defaults()
//server.use(middlewares)
//then remove options calls
