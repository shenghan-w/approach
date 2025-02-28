# AppRoach API

<!-- This is a sample for AppRoach's API. This sample focuses on the Trail Topography feature of the app.-->

## Trail Topography API

These are the objects for the Trail Topography API.
- trailinfo

<!-- More object tbd. -->

---

## Error Handling

AppRoach uses conventional HTTP response codes to indicate the success or failure of an API request.

| Code | Meaning | Description |
| ---: | --- | --- |
| 200 | OK | Everything worked as expected |
| 201 | Created | The resource was successfully created |
| 400 | Bad Request | Invalid request |
| 404 | Not Found | The requested resource was not found |
| 500, 502, 503, 504 | Server Errors | An internal server error |