---

Tags : #cors #web #development #concept
Back Links :
Date : {{26-03-2022}} 20:34

---

# CORS

## What is it
CORS is a mechanism that allows browsers to request data from 3rd party URLs (or origins).
Browser implements **SAME-ORIGIN Policy** as part of its security module. This will makes browser to freely requests resource in the server from its own url, but will block anything if its not the same url by giving CORS error.
This can happen because when requesting resource to server, browser will add *origin* parameter in the *header* with the value of url name of the requesting end.
- If the *origin* is same with the server, then it is ok.
- If the *origin* is different with the server, known as called *CROSS-ORIGIN Request*, the server will add *Access-Control-Allow-Origin* parameter in the *header* with the value of **list of allowed url**.
	- Then the browser will **match** the value in the *origin* and from Access-Control-Allow-Origin, for the browser to show the result. If it's **mismatch**, show CORS error.
	- The value of *Access-Control-Allow-Origin* can also be a wildcard ( * ) which allow all url to make request to the server.


## Common Solution
Setup the server to include cors header in the response, with the name of the allowed urls and the allowed methods.


## Advanced
Some methods such as **PUT, PATCH, DELETE** or any request with non-standard headers, need to be **Preflighted**, which means the browser will first check with the server if the method is allowed.
**Preflighte** works by sending **OPTIONS** request, and the server will responds with the list of allowed urls in *Access-Control-Allow-Origin* param and the list of allowed methods in *Access-Control-Allow-Method* param.
The server can also include *Access-Control-Max-Age* param in the response's header with the value of a number that represents **duration**, so the browser can **cache** the **Preflight** for the duration.

