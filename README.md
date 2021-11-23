# Homework-14-Web-Development

#### HTTP Requests and Responses

Answer the following questions about the HTTP request and response process.

1. What type of architecture does the HTTP request and response process occur in?

 - _Client-Server Architecture_

2. What are the different parts of an HTTP request? 

- _Request Line, Header, and Body_

3. Which part of an HTTP request is optional?

- _The body is optional._

4. What are the three parts of an HTTP response?

- _Status Line, Header, and Response body.

5. Which number class of status codes represents errors?

- _400's represents errors_

6. What are the two most common request methods that a security professional will encounter?

- _GET and POST are the two most common request methods._

7. Which type of HTTP request method is used for sending data?

- _Post method is used for sending data._

8. Which part of an HTTP request contains the data being sent to the server?

- _Request Body contains the data being sent to the server._

9. In which part of an HTTP response does the browser receive the web code to generate and style a web page?

- _Response Body: the broswer receives the web code to generate and style a web page._

#### Using curl

Answer the following questions about `curl`:

10. What are the advantages of using `curl` over the browser?

- _Able to test HTTP Reqests which can be automated._
- _Able to support various protocols without a present UI._

11. Which `curl` option is used to change the request method?

 - _`curl` -X_

12. Which `curl` option is used to set request headers?


- _`curl` -H_

13. Which `curl` option is used to view the response header?

- _`curl` --head_

14. Which request method might an attacker use to figure out which HTTP requests an HTTP server will accept?

- _Options method would be used to figure out which HTTP requests an HTTP server will accept._

#### Sessions and Cookies

Recall that HTTP servers need to be able to recognize clients from one another. They do this through sessions and cookies.

Answer the following questions about sessions and cookies:

15. Which response header sends a cookie to the client?

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```
- _Set-Cookie: cart=Bob sends cookie to the client._

16. Which request header will continue the client's session?

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```
- _Get /cart HTTP/1.1 will continue the clients's session._

#### Example HTTP Requests and Responses

Look through the following example HTTP request and response and answer the following questions:

**HTTP Request**

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What is the request method?

- _Post_

18. Which header expresses the client's preference for an encrypted response?

- _Upgrade-Insecure-Requests:1_

19. Does the request have a user session associated with it?

- _No, there are no cookie tracking, therefore the request does not have a user session associated with it._

20. What kind of data is being sent from this request body?

- _The Username=Barbara and Password=password is being sent from this request body._

**HTTP Response**

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```

21. What is the response status code?

- _200 OK: Successful response_

22. What web server is handling this HTTP response?

- _Apache webserver_

23. Does this response have a user session associated to it?

- _Yes it does, SessionID=5_

24. What kind of content is likely to be in the [page content] response body?

- _The content type is text/HTML, therefore the page content likely an HTML file_

25. If your class covered security headers, what security request headers have been included?

- _Strict-Transport-Security header_

#### Monoliths and Microservices

Answer the following questions about monoliths and microservices:

26. What are the individual components of microservices called?

- _Microservices, Containers, Service Mesh, Service Discover, and API gateway._

27. What is a service that writes to a database and communicates to other services?

- _API gateway_

28. What type of underlying technology allows for microservices to become scalable and have redundancy?

- _Containers allows for microservices to become scalable and have redundancy._ 

#### Deploying and Testing a Container Set

Answer the following questions about multi-container deployment:

29. What tool can be used to deploy multiple containers at once?

- _Docker Compose_

30. What kind of file format is required for us to deploy a container set?

- _YAML format: .yml_

#### Databases

31. Which type of SQL query would we use to see all of the information within a table called `customers`?

- _SELECT * FROM customers

32. Which type of SQL query would we use to enter new data into a table? (You don't need a full query, just the first part of the statement.)

- _INSERT INTO table_name_

33. Why would we never run `DELETE FROM <table-name>;` by itself?

- _If you run `DELETE FROM <table-name>` by itself, it would delete all records._

---


### Bonus Challenge Instructions: The Cookie Jar

First, using Docker Compose, navigate to the Day 1 WordPress activity directory and bring up the container set:

- `/home/sysadmin/Documents/docker_files`

Using `curl`, you will do the following for the Ryan user:

  - Log into WordPress and save the user's cookies to a cookie jar.

  - Test a WordPress page by using a cookie from the cookie jar.

  - Pipe the output from the cookie with `grep` to check for authenticated page access.

  - Attempt to access a privileged WordPress admin page.

#### Step 1: Set Up

Create two new users: Amanda and Ryan.   

1. Navigate to `localhost:8080/wp-admin/`

2. On the left-hand toolbar, hover over **Users** and click **Add New**.

3. Enter the following information to create the new user named Amanda.

    - Username: `Amanda`
    - Email: `amanda@email.com`

![Amanda username](https://user-images.githubusercontent.com/88859779/143035402-79c1cf58-7d64-4fa0-8c3a-08d614e36237.png)

4. Skip down to password:

    - Password: `password`
    - Confirm Password: Check the box to confirm use of weak password.
    - Role: `Administrator`

![Amanda password](https://user-images.githubusercontent.com/88859779/143035462-16425563-e2fa-48ba-bce6-9db5df062d44.png)

5. Create another user named Ryan.

    - Username: `Ryan`
    - Email: `ryan@email.com`

![Ryan username](https://user-images.githubusercontent.com/88859779/143035512-c985ff0f-9f5e-4857-9709-e10a34a0a2dd.png)

6. Skip down to password:

    - Password: `123456`
    - Confirm Password: Check the box to confirm use of weak password.
    - Role: `Editor`

![Ryan password](https://user-images.githubusercontent.com/88859779/143035548-13a344d4-99b5-4aef-bcfc-c85d3679e488.png)

7. Log out and log in with the following credentials:

    - Username: `Amanda`
    - Password: `password`

#### Step 2: Baselining

For these "baselining" steps, you'll want to log into two different types of accounts to see how the WordPress site looks at the `localhost:8080/wp-admin/users.php` page.  We want to see how the Users page looks from the perspective of an administrator, vs. a regular user.

1. Using your browser, log into your WordPress site as your sysadmin account and navigate to `localhost:8080/wp-admin/users.php`, where we previously created the user Ryan. Examine this page briefly. Log out.

![Administrator users php](https://user-images.githubusercontent.com/88859779/143035852-14dce5af-2bfb-4a0c-8d88-5c4c9086a39a.png)

2. Using your browser, log into your Ryan account and attempt to navigate to `localhost:8080/wp-admin/index.php`. Note the wording on your Dashboard.

![Ryan index php](https://user-images.githubusercontent.com/88859779/143037359-96b8c595-06b0-423d-a7f5-f892a431cb24.png)

3. Attempt to navigate to `localhost:8080/wp-admin/users.php`. Note what you see now.

![User users php](https://user-images.githubusercontent.com/88859779/143036074-fde66cf7-e025-4f3a-9a9e-531f7ab94912.png)

Log out in the browser.

#### Step 3: Using Forms and a Cookie Jar

Navigate to `~/Documents` in a terminal to save your cookies.

1. Construct a `curl` request that enters two forms: `"log={username}"` and `"pwd={password}"` and goes to `http://localhost:8080/wp-login.php`. Enter Ryan's credentials where there are placeholders.

    - **Question:** Did you see any obvious confirmation of a login? (Y/N) **YES. Connected to localhost (127.0.0.1) port 8080.**

![curl login to Ryan](https://user-images.githubusercontent.com/88859779/143038056-3a49db4b-8819-425a-87da-9d4f8c896861.png)

2. Construct the same `curl` request, but this time add the option and path to save your cookie: `--cookie-jar ./ryancookies.txt`. This option tells `curl` to save the cookies to the `ryancookies.txt` text file.

![--cookie-jar option](https://user-images.githubusercontent.com/88859779/143038154-1bfa1b4b-de15-42c2-82f1-ac2b5ff42f76.png)

3. Read the contents of the `ryancookies.txt` file.

   - **Question:** How many items exist in this file? **There are 3 items that exist in this file.**

![cat ryancookies txt](https://user-images.githubusercontent.com/88859779/143038243-bb196839-13e6-4151-9ce1-cf82a3322e6b.png)

Note that each one of these is a cookie that was granted to Ryan after logging in.

#### Step 4: Log in Using Cookies

1. Craft a new `curl` command that now uses the `--cookie` option, followed by the path to your cookies file. For the URL, use `http://localhost:8080/wp-admin/index.php`.

   - **Question:** Is it obvious that we can access the Dashboard? (Y/N) **Yes**

![--cookie option](https://user-images.githubusercontent.com/88859779/143038406-13b29739-119e-4949-b8de-638e33683f33.png)

2. Press the up arrow on your keyboard to run the same command, but this time, pipe `| grep Dashboard` to the end of your command to return all instances of the word `Dashboard` on the page.

    - **Question:**  Look through the output where `Dashboard` is highlighted. Does any of the wording on this page seem familiar? (Y/N) If so, you should be successfully logged in to your Editor's dashboard. **YES, the wording on this page is familiar.**

![Dashboard](https://user-images.githubusercontent.com/88859779/143038636-3feabd97-98a3-419d-b93b-8ea86eb492ef.png)

#### Step 5: Test the Users.php Page

1. Finally, write a `curl` command using the same `--cookie ryancookies.txt` option, but attempt to access `http://localhost:8080/wp-admin/users.php`.

    - **Question:** What happens this time? **Able to access**

![Ryan users php](https://user-images.githubusercontent.com/88859779/143038941-89cad698-3b81-428d-ac96-e5e2efdba457.png)

---

