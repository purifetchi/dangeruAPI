# The danger/u/ API.

**What is it**

Avaiable under ``` https://boards.dangeru.us/api.php ``` provides an interface for applications to easily index a board or get replies from a thread.

**How do i use it**

The API requires 3 main queries. *type*, *board* and *ln*.
* *type* is the query that has the type of request you want to perform, currently **index** and **thread**
* *board* is the query that has the board you want to index
* *ln* is the length of the request

Wanting to get the replies from a certain thread requires one more query `thread`, which is the id of the thread you want to index.

Example usage of the API to get the last 5 threads on /u/

``` https://boards.dangeru.us/api.php?type=index&board=u&ln=5 ```

The output is in JSON which would look like this

``` { "board":[{"name":"/u/", "url":"https://boards.dangeru.us/u/"}], "threads":[{"id":1529,"title":"G/u/rl, asian, almost 18, weeb. I'm bored ask me everythin pls ","url":"https://boards.dangeru.us/u/thread.php?=1529"},{"id":1547,"title":"ay ni🅱️🅱️a ","url":"https://boards.dangeru.us/u/thread.php?=1547"},{"id":1532,"title":"Ask a retired assa anything ","url":"https://boards.dangeru.us/u/thread.php?=1532"},{"id":1419,"title":"Eh? You've never seen a pair of breasts before? ","url":"https://boards.dangeru.us/u/thread.php?=1419"},{"id":1538,"title":"stop it with the AMAs ","url":"https://boards.dangeru.us/u/thread.php?=1538"},{"id":1516,"title":"Three Word sfory thread ","url":"https://boards.dangeru.us/u/thread.php?=1516"}]} ```

The first field, **board** contains the information about the name and url of the board.
The threads field contains the id, title and the url of the thread.

Indexing a thread is similar too!

``` https://boards.dangeru.us/api.php?type=thread&board=u&ln=5&thread=1334 ```

The output:

``` { "meta":[ { "title":"just try to post a less than three ", "id":1334, "url":"https://boards.dangeru.us/u/thread.php?=1334"} ], "replies":[{ "post":"you wont "},{ "post":" "},{ "post":"nuuuuuuuuuuuuuu "},{ "post":">3 "},{ "post":"> "}]} ```

**Show me an example of usage in some programming language you faggot.**

Here is an example using python and the [requests](https://github.com/kennethreitz/requests) library

```python
import requests

fetch = requests.get("https://boards.dangeru.us/api.php?type=index&board=u&ln=5")
print (fetch.content)
```
Output:
`b'{ "board":[{"name":"/u/", "url":"https://boards.dangeru.us/u/"}], "threads":[{"id":1484,"title":"One word story thread\n","url":"https://boards.dangeru.us/u/thread.php?=1484"},{"id":1529,"title":"G/u/rl, asian, almost 18, weeb. I\'m bored ask me everythin pls\n","url":"https://boards.dangeru.us/u/thread.php?=1529"},{"id":1516,"title":"Three Word sfory thread\n","url":"https://boards.dangeru.us/u/thread.php?=1516"},{"id":1547,"title":"ay ni&#127345;&#65039;&#127345;&#65039;a\n","url":"https://boards.dangeru.us/u/thread.php?=1547"},{"id":1532,"title":"Ask a retired assa anything\n","url":"https://boards.dangeru.us/u/thread.php?=1532"},{"id":1419,"title":"Eh? You\'ve never seen a pair of breasts before?\n","url":"https://boards.dangeru.us/u/thread.php?=1419"}]}'`

You can also use the danger/u/ python library! It requires requests too sadly, but the library automatically makes your request into an array!

```python
import dangeru

fetch = dangeru.thread("u",5,"1000")
print(fetch["meta"][0]["title"])
```

Output: ```Rip me```

So, stop being passive and utilize some of our beautiful dangerous API!
