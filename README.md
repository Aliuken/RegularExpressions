# Regular expressions

## 1. Online tools
* https://regex101.com/
* https://regexr.com/

## 2. Regex for "not starting with":
https://stackoverflow.com/questions/46162605/regex-match-string-not-starting-with

### 2.1. Example not starting with "ado" or "ADO":

* Regex:
  ```regex
  /(?<!(ado|ADO))db/g
  ```

* Input:
  ```txt
  adodb
  ADOdb
  rdbms
  ```

* Matches:
  * r**db**ms

### 2.2. Example not starting with "web" ignore case

* Regex:
  ```regex
  /(?<!web)sockets?/gi
  ```

* Input:
  ```txt
  websocket
  websockets
  socket
  sockets
  WebSocket
  WebSockets
  Websocket
  Websockets
  Socket
  Sockets
  ```

* Matches:
  * **socket**
  * **sockets**
  * **Socket**
  * **Sockets**

## 3. Regex for "word not ending with":
https://stackoverflow.com/questions/6830796/regex-to-match-anything-but-two-words

### 3.1. Example word not ending with "class" or "":

* Regex:
  ```regex
  /DB::(?!class\W|$)/g
  ```

* Input:
  ```txt
  DB::class
  DB::class
  DB::class,
  DB::class)
  DB::class(
  DB::
  DB::aaa
  DB::classa
  ```

* Matches:
  * **DB::**aaa
  * **DB::**classa 

## 4. Regex for "spaces without line breaks" and "everything without spaces and line breaks":
https://stackoverflow.com/questions/3469080/match-whitespace-but-not-newlines

### 4.1. Example sqlplus or sqlplus64 with possible intermediate words and an sql file name

* Regex:
  ```regex
  /(^|\s|\(|\/|`)sqlplus(64)?([^\S\r\n]+\S+)*[^\S\r\n]+(\S+\.sql)/g
  ```
  
  where:
  * `[^\S\r\n]+` means "spaces without line breaks"
  * `\S+` means "everything without spaces and line breaks"
  * there are four groups:
    ```regex
    - group 1: (^|\s|\(|\/|`)
    - group 2: (64)
    - group 3: ([^\S\r\n]+\S+)
    - group 4: (\S+\.sql)
    ```

* Input:
  ```txt
  sqlplus aa
  a bbb.sql
  
  sqlplus aaa bb
  b.sql
  
  sqlplus aaa bbb.sql
  
  sqlplus64 aaa bbb.sql
  ```

* Matches:
  * **sqlplus aaa bbb.sql** with:
    * group 1: "\n"
    * group 3: " aaa"
    * group 4: "bbb.sql"

  * **sqlplus64 aaa bbb.sql** with:
    * group 1: "\n"
    * group 2: "64"
    * group 3: " aaa"
    * group 4: "bbb.sql"

## 5. Regex for "everything without slash" and "everything":

### 5.1. Example URL with 2 path params and ending in whatever

* Regex:
  ```regex
  ^/path/var1/([^/]+)/var2/([^/]+)/(.*)
  ```
  
  where:
  * `([^/]+)` means "everything without slash"
  * `(.*)` means "everything"
  * there are three groups:
    ```regex
    - group 1: ([^/]+)
    - group 2: ([^/]+)
    - group 3: (.*)
    ```

* Input:
  ```txt
  /path/var0/value0/var1/value1/end
  /path/var1/value1/var2/value2/end
  ```

* Matches:
  * **/path/var1/value1/var2/value2/end** with:
    * group 1: "value1"
    * group 2: "value2"
    * group 3: "end"
