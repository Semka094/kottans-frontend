# kottans-frontend

## Stage 0. Self-Study
<details>
<summary>Git & Version Control</summary> 


**Git - version control tool.**

Version control is like a save point in the game.

3 most popular version control tools:

- Git (distributed version control system)
- Subversion
- Mercurial

There are 2 different categories:
- _Centralized model_ (one computer hosts the project and every interaction must go through this computer)
- _Distributed model_ (no central repository of info, each dev has a complete copy on their computer)

3 main commands:
```$ git init```
```$ git clone```
```$ git status```


```ls``` - used to list files and directories

```mkdir``` - used to create a new directory

```cd``` - used to change directories

```rm``` - used to remove files and directories

```$ git log``` - is used to display all of the commits of a repository

```$ git log --oneline``` _(все те саме що і при git log тільки візуально покаже вкорочену версію)_

-----------------

## Branches
```$ git tag``` _(створити тег, можна і на древній коміт)_

🔥 ```$ git branch``` _(показати усі вітки і яка зараз вітка активна, for example → *master)_

```$ git branch name_of_new_branch```  _(створити нову вітку)_

```$ git checkout name_of_the_branch``` _(переключитися на іншу вітку)_

🔥  ``$ git checkout -b name_of_the_branch`` _(створить нову вітку і перейде в неї = git checkout)_

```$ git branch -d name_of_the_branch``` _(видалити вітку: можна зробити лише тоді коли ти на іншій вітці, і якщо там немає змін які не закомічені в іншу гілку)_

```$ git branch -D name_of_the_branch``` _(дозволить видалити бренч навіть якщо там є зміни які ніде не були закомічені)_

Running ```git checkout``` command will:
- remove all files and directories from the Working Directory that Git is tracking;
- go into the repository and pull out all of the files and directories of the commit that the branch points to;

## Merges
```
$ git merge <other-branch>
```

There are two types of merges:

- **Fast-forward merge** – the branch being merged in must be ahead of the checked out branch. The checked out branch's pointer will just be moved forward to point to the same commit as the other branch.

- **Regular merge:**
    - two divergent branches are combined
    - a merge commit is created
  
```$ git log --oneline --decorate --graph --all``` _(покаже усі бренчі і відвітвлення)_

```$ git branch name_of_a_new_branch SHA``` _(створить вітку від певного коміту)_

🔥 ``$ git commit -a -m "short desr"`` _(одночаcно додає в stage index ``-add``, комітить і добавляє коментар ``-message``)_

```$ git commit --amend``` _(дозволяє змінити/виправити тайтл останнього коміту або оновити останній комміт (замість створення нового))_

```$ git revert <SHA-of-commit-to-revert>``` _(для скасування попередньо зробленого коміту)_

```$ git reset <reference-to-commit>```


``` $ git reset``` can be used to:

- move the HEAD and current branch pointer to the referenced commit
- erase commits
- move committed changes to the staging index
- unstage committed changes


**Git Reset's Flags**
```
$ git reset
```


`````--mixed ````` _(by default і поверне його у Working Directory. Можна робити зміни, але SHA вже буде іншим навіть якщо контент не зміниться)_

`````--soft````` _(поверне на Staging Index i SHA буде іншим)_

`````--hard````` _(видалить коміт ! )_
## Relative Commit References

``X~n`` means: The nth ancestor of X.

``X^`` means: The parent of X. This is equivalent to X~1.

If ``X`` has more than one parent, one needs to distinguish between them when using the ``^`` notation.
So X^1 would be the first parent, X^2 would be the second parent, and so on. X^ is equivalent to X^1 (and also equivalent to X~1).


## Backup Branch 💡

Remember that using the ``git reset`` command will _erase commits from the current branch_. 

> Note: So if you want to follow along with all the resetting stuff that's coming up, you'll need to create a branch on the current commit that you can use as a backup.


    $ git branch backup
 </details>

<details>
<summary>Linux CLI, and HTTP</summary>

### Linux
``chmod`` - change premission mode

``cat`` - concatenate

``cd`` - change directory

``mkdir`` - make directory

``rmdir`` - remove empty directory

``rm -r <name_of_directory>`` - remove directory even if it has some file

``mv`` - move or rename

``pwd`` - print current working directory

``*``  - all files

``finger`` - show user info

``find`` - find files

``df`` - disk free - to check how much space in the system

``ps``- process status

``ps aux`` - show all processes

``grep`` - to find patterns in data

``kill -9 <name_of_the_process>`` - kill immediately 

### HTTP
HTTP Request Verbs
- GET (fetch)
- POST (create)
- PUT (update)
- DELETE

#### HTTP Requests
- **request** line (what is being requested)
- **headers** (additional info about message, request, communication format)
- **body** (optional): (the content of the request)

#### HTTP Responses
- **status line** (includes a status code for example, code 200)
- **headers** (additional info about the response, for ex, content type or information about the server)
- **body** (optional): the content of the response. For ex, HTML content of a requested web page)

#### Status Codes
``1xx``: Informational Messages

``2xx``: Successful (``200 OK``)

``3xx``: Redirection (``303 See Other``)

``4xx``: Client Error (``404 Not Found``)

``5xx:`` Server Error (``500 Internal Server Error``)

### HTTP Connections
A connection must be established between the client and server before they can communicate with each other.

**Persistent Connections**

HTTP/1.1 introduced persistent connections, long-lived connections that stay open until the client closes them. Persistent connections are the default in HTTP/1.1
To achieve this, HTTP/1.1 keeps TCP connections open, even after a transaction is complete. The existing connection will be reused for future references. This is known as a persistent connection.

**Parallel Connections**

In addition to persistent connections, browsers/clients also employ a technique, called parallel connections, to minimize network delays. The age-old concept of parallel connections involves creating a pool of connections (generally capped at six connections). If there are six assets that the client needs to download from a website, the client makes six parallel connections to download those assets, resulting in a faster turnaround.

### HTTP Authentication

The server must know who a user is in order to provide that functionality.
There are a few different ways a server can collect this information, and most websites use a hybrid of these approaches:

**Request headers**: From, Referer, and User-Agent

**Client-IP**: the IP address of the client.

**Fat URLs**: storing the state of the current user by modifying the URL and redirecting to a different URL on each click; each click essentially accumulates state.

**Cookies**: the most popular and non-intrusive approach.

#### Basic Authentication

In Basic Authentication, the server initially denies the client's request with a WWW-Authenticate response header and a 401 Unauthorized  code. On seeing this header, the browser displays a login dialog, prompting for a username and password.

- **Tackling the 401 Unauthorised Response**

The 401 error occurs when a client request was not successfully completed. The request failed because important authentication credentials were not present in the request.

- **Authorisation Header**

Another commonly used method for sending client identity information to the server is through the Authorisation header.

- **Authentication Using Cookies**

Cookies allow the server to attach arbitrary information for outgoing responses via the Set-Cookie response header. A cookie is set with one or more name=value pairs separated by a semicolon (;), as in Set-Cookie: session-id=12345ABC; username=semka.

#### Digest Authentication

**From Client**: Digest Authentication does not transfer a password to the server.

**At Server**: The algorithm used to build the hash is used by the server to decode the password and username.

### HTTP Caching

Types of Caching:

1. **Public cashe**: stores the server response for multiple users.

2. **Private cashe**: limited to a single user. The resource would be stored in the user's browser.

Keeping the content fresh and up-to-date is one of the primary responsibilities of the cache. To keep the cached copy consistent with the server, HTTP provides some simple mechanisms, namely _Document Expiration_ and _Server Revalidation_.

#### Document Expiration

HTTP allows an origin-server to attach an expiration date to each document using the Cache-Control and Expires response headers. This helps the client and other cache servers know how long a document is valid and fresh.

``Expires`` is an older HTTP/1.0 response header that specifies the value as an absolute date.

``Cache-Control: max-age=<s>`` header where ``max-age`` is a relative age, specified in seconds, from the time the response was created. 
Thus if a document should expire after one day, the expiration header should be ``Cache-Control: max-age=86400``.

#### Server Revalidation

Once a cached document expires, the cache must revalidate with the server to check if the document has changed.
Just because a cached copy has expired doesn't mean that the server actually has newer content.

## HTTPS

The HTTPS protocol provides a secure connection on the web.
HTTPS's secure component involves inserting a layer of encryption/decryption between HTTP and TCP. This is the Secure Sockets Layer (SSL) or the improved Transport Layer Security (TLS).

HTTPS uses the SSL or TLS to encrypt the entire communication between the client and the server. This makes sure that the client is connected only to the right server. Also, it verifies that the data is transferred only to the intended server.


</details>

<details>
<summary>Git Collaboration</summary>

CI _(Continuous Integration)_ - is the practice of automating the integration of code changes from multiple contributors into a single software project.
It’s a primary DevOps best practice, allowing developers to frequently merge code changes into a central repository where builds and tests then run.

CD - _(Continious Delivery)_ - CD focuses an organization on building a streamlined, automated software release process.
</details>


<details>
  <summary>Intro to HTML and CSS</summary>

New info for me was that there is _Quirks mode_ for websites that do not follow W3C і IETF standards.

Inline tags cannot contain block tags.

**Wrong**: ``<span><div></div></span>``

**Good**: ``<div><span></span></div>``

semantic HTML element - an element that implies (натякає/передбачає) some meaning to the content. Also, it may help in SEO rankings.

For example: ``<h1>``, ``<nav>``,``<head>``, ``<footer>``

**There are 3 types of selectors**:
- Element (h1, p etc)
- Class ( .class_name)
- ID selector (#nameID)

**Combining selectors:**

**Element with Class selector**

```
p.blue {
  font-color: blue;
}
```

Blue color will apply to those paragraph that has ``classname=”big”`` only

**Child selector**

```
article > p {
  font-color: blue;
}
```

Blue color will apply to p element that is a direct child of article element

**Descending selector**

```
article p {
  font-color: blue;
}
```

Blue color will apply to all p elements in the article element at any level. 
Whether it is a child or not.


There are _relative_ and _absolute_ positioning.

### Media Queries

If we want to style our website based on the size of the screen, we should use, for example:

``@media (min-width: 768px) {...} and (max-width: 991) {...}``

``@media (orientation: portrait) {...}``

``@media screen {...}``

</details>
