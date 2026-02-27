## 1. Client → Request → Server → Response

## 2. Common Http Methods
| Method | Purpose             | Example       |
| ------ | ------------------- | ------------- |
| GET    | Fetch data          | Get user list |
| POST   | Send new data       | Create user   |
| PUT    | Update full data    | Replace user  |
| PATCH  | Update partial data | Update email  |
| DELETE | Remove data         | Delete user   |

## 3. Commonly Used Status Codes
    200 – OK                               # 400 series -> client side errors
    201 – Created                          # 500 series -> server side errors
    204 – No Content                       # 300 series -> redirection errors
    400 – Bad Request                      # 200 series -> sucess
    401 – Unauthorized                     # 100 series -> information
    403 – Forbidden
    404 – Not Found
    422 – Validation Error
    500 – Internal Server Error
    503 – Service Unavailable

## 4. Status Code to Rest API Mapping
| Operation        | Status Code |
| ---------------- | ----------- |
| GET success      | 200         |
| POST success     | 201         |
| PUT success      | 200 / 204   |
| DELETE success   | 204         |
| Validation error | 422         |
| Auth failure     | 401 / 403   |



## 5. Http Response Component
    1. Status Code
    2. Headers
    3. Body (data)

## 4. Python Request Library
        pip install requests

## 5. Accessing HTTP Data using requests
| **What you want to access**         | **Object**                 | **How to access (Code)**                        | **Return Type**       | **Notes / Best Practice**             |
| ----------------------------------- | -------------------------- | ----------------------------------------------- | --------------------- | ------------------------------------- |
| **Request headers (all)**           | `response.request.headers` | `response.request.headers`                      | `dict`-like           | Contains **default + custom** headers |
| **Request header (specific key)**   | `response.request.headers` | `response.request.headers.get("Authorization")` | `str / None`          | Always use `.get()`                   |
| **Response headers (all)**          | `response.headers`         | `response.headers`                              | `CaseInsensitiveDict` | Keys are case-insensitive             |
| **Response header (specific key)**  | `response.headers`         | `response.headers.get("Content-Type")`          | `str / None`          | Safer than `[]`                       |
| **HTTP status code**                | `response.status_code`     | `response.status_code`                          | `int`                 | Example: `200`, `404`                 |
| **Status message**                  | `response.reason`          | `response.reason`                               | `str`                 | Example: `"OK"`                       |
| **Payload / response body (text)**  | `response.text`            | `response.text`                                 | `str`                 | Raw body as string                    |
| **Payload / response body (JSON)**  | `response.json()`          | `response.json()`                               | `dict / list`         | Only if response is JSON              |
| **Payload / response body (bytes)** | `response.content`         | `response.content`                              | `bytes`               | Used for files                        |
| **Request payload (sent body)**     | `response.request.body`    | `response.request.body`                         | `str / bytes / None`  | Shows sent data                       |
| **Check if response is success**    | `response.ok`              | `response.ok`                                   | `bool`                | `True` if `< 400`                     |

    ⚠️ Important Notes (Must Remember)
        1. custom / request header send to server = Your headers dict + Requests default headers 
        2. response.headers ≠ response.request.headers
        3. Headers are metadata, not payload
        4. .json() parses body → fails if response isn’t JSON
        5. Use .get() for headers to avoid KeyError
        6. Status code always comes from response


# 6. Http Methods Constructor
##  6.1  ✅ Common Constructor Fields (All HTTP Methods)
* These parameters are accepted by ALL methods:
* get, post, put, patch, delete, head, options

| Parameter         | Type          | Purpose                | Used With        |
| ----------------- | ------------- | ---------------------- | ---------------- |
| `url`             | str           | Target endpoint        | ALL              |
| `headers`         | dict          | HTTP headers           | ALL              |
| `params`          | dict          | URL query parameters   | ALL (mainly GET) |
| `auth`            | tuple / Auth  | Authentication         | ALL              |
| `timeout`         | float / tuple | Request timeout        | ALL              |
| `cookies`         | dict          | Cookies                | ALL              |
| `allow_redirects` | bool          | Follow redirects       | ALL              |
| `verify`          | bool          | SSL certificate verify | ALL              |
| `proxies`         | dict          | Proxy settings         | ALL              |
| `stream`          | bool          | Stream response body   | ALL              |
| `cert`            | str / tuple   | Client-side cert       | ALL              |
| `hooks`           | dict          | Event hooks            | ALL              |

## 6.2 ⚠️ Method-Specific / Meaningful Fields
* These parameters are accepted by all, 
* but are only meaningful for certain HTTP methods

| Parameter | Type               | Purpose               | GET | POST | PUT | PATCH | DELETE | HEAD | OPTIONS |
| --------- | ------------------ | --------------------- | :-: | :--: | :-: | :---: | :----: | :--: | :-----: |
| `params`  | dict / list[tuple] | URL query string      |  ✅  |  ⚠️  |  ⚠️ |   ⚠️  |    ✅   |   ✅  |    ⚠️   |
| `data`    | dict / str / bytes | Form-encoded body     |  ❌  |   ✅  |  ✅  |   ✅   |   ⚠️   |   ❌  |    ❌    |
| `json`    | dict / list        | JSON request body     |  ❌  |   ✅  |  ✅  |   ✅   |   ⚠️   |   ❌  |    ❌    |
| `files`   | dict               | Multipart file upload |  ❌  |   ✅  |  ⚠️ |   ❌   |    ❌   |   ❌  |    ❌    |
Legend:
* ✅ = Common & valid
* ⚠️ = Technically allowed but uncommon / server-dependent
* ❌ = Ignored or not applicable