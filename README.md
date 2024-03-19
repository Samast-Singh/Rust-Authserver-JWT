# Rust-Authserver-JWT
A JWT(JSON Web Token) authentication and authorization server that uses rust with warp.

It has 2 files that performs the functions:-
1. The `auth.rs` file makes authorization and authentication of a JWT.
2. The `error.rs` file shows and handles the error that occurs due to the wrong username or password.

## Run
The steps used to run the full program are:-

### Login
```bash
curl http://localhost:8000/login -d '{"email": "user@userland.com", "pw": "1234"}' -H 'Content-Type: application/json'

{"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIxIiwicm9sZSI6IlVzZXIiLCJleHAiOjE2MDMxMzQwODl9.dWnt5vfcGdwypEQUr3bLMrZYfdyxj3v6-io6VREWHXebMUCKBddf9xGcz4vHrCXruzx42zrS3Kygiqw3xV8W-A"}
```

### User Endpoint
```bash
curl http://localhost:8000/user -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIxIiwicm9sZSI6IlVzZXIiLCJleHAiOjE2MDMxMzQwODl9.dWnt5vfcGdwypEQUr3bLMrZYfdyxj3v6-io6VREWHXebMUCKBddf9xGcz4vHrCXruzx42zrS3Kygiqw3xV8W-A' -H 'Content-Type: application/json'

Hello User 1

curl http://localhost:8000/admin -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIxIiwicm9sZSI6IlVzZXIiLCJleHAiOjE2MDMxMzQwODl9.dWnt5vfcGdwypEQUr3bLMrZYfdyxj3v6-io6VREWHXebMUCKBddf9xGcz4vHrCXruzx42zrS3Kygiqw3xV8W-A' -H 'Content-Type: application/json'

{"message":"no permission","status":"401 Unauthorized"}
```

### Admin Endpoint
```bash
curl http://localhost:8000/login -d '{"email": "admin@adminaty.com", "pw": "4321"}' -H 'Content-Type: application/json'

{"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIyIiwicm9sZSI6IkFkbWluIiwiZXhwIjoxNjAzMTM0MjA1fQ.uYglVKRvb3h0bDC0Uz8FwGTu4v__Rl3toVI9fMI4_IT8keKde_SZRFQ4ii_PKzI4wjmDsZlnpULe6Tg0vWfEnw"}

curl http://localhost:8000/admin -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIyIiwicm9sZSI6IkFkbWluIiwiZXhwIjoxNjAzMTM0MjA1fQ.uYglVKRvb3h0bDC0Uz8FwGTu4v__Rl3toVI9fMI4_IT8keKde_SZRFQ4ii_PKzI4wjmDsZlnpULe6Tg0vWfEnw' -H 'Content-Type: application/json'

Hello Admin 2

curl http://localhost:8000/user -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIyIiwicm9sZSI6IkFkbWluIiwiZXhwIjoxNjAzMTM0MjA1fQ.uYglVKRvb3h0bDC0Uz8FwGTu4v__Rl3toVI9fMI4_IT8keKde_SZRFQ4ii_PKzI4wjmDsZlnpULe6Tg0vWfEnw' -H 'Content-Type: application/json'

Hello User 2
```
