### CURL

Silent mode, only output response data.
```
[root@webh ~]# curl -s https://api.github.com/
{
  ...
  ...
  "keys_url": "https://api.github.com/user/keys",
  "notifications_url": "https://api.github.com/notifications",
  "organization_repositories_url": "https://api.github.com/orgs/{org}/repos{?type,page,per_page,sort}",
  "organization_url": "https://api.github.com/orgs/{org}",
  ...
  ...
}
```
To print http headers with response data.
```
[root@webh ~]# curl -i https://api.github.com/
HTTP/1.1 200 OK
Server: GitHub.com
Date: Sat, 01 Apr 2017 13:01:49 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 2165
Status: 200 OK
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 58
...
...
```
To print all request, response http headers and response data. **>** header data sent by curl, **<** header data received by curl, * additional information provided by curl.
```
[root@webh ~]# curl -v https://api.github.com/
*   Trying 192.30.253.117...
* Connected to api.github.com (192.30.253.117) port 443 (#0)
* Cipher selection: ALL:!EXPORT:!EXPORT40:!EXPORT56:!aNULL:!LOW:!RC4:@STRENGTH
* successfully set certificate verify locations:
*   CAfile: /etc/pki/tls/certs/ca-bundle.crt
  CApath: none
...
...
> GET / HTTP/1.1
> Host: api.github.com
> User-Agent: curl/7.50.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Server: GitHub.com
< Date: Sat, 01 Apr 2017 13:02:30 GMT
< Content-Type: application/json; charset=utf-8
< Content-Length: 2165
< Status: 200 OK
...
...
{
  "current_user_url": "https://api.github.com/user",
  "current_user_authorizations_html_url": "https://github.com/settings/connections/applications{/client_id}",
  "authorizations_url": "https://api.github.com/authorizations",
  "code_search_url": "https://api.github.com/search/code?q={query}{&page,per_page,sort,order}",
...
...

```
Print http headers only.
```
[root@webh ~]# curl -I https://api.github.com/
HTTP/1.1 200 OK
Server: GitHub.com
Date: Sat, 01 Apr 2017 13:11:16 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 2165
Status: 200 OK
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 56
X-RateLimit-Reset: 1491055110
...
...
```
Save output to a file with -o option. (to save only response data we used silent mode)
```
[root@webh ~]# curl -so github-api.json https://api.github.com/
```