# Regular expressions

## 1. Online tools
* https://regex101.com/
* https://regexr.com/

## 2. Regular expression "not starting with":
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
  **socket**
  **sockets**
  **Socket**
  **Sockets**

## 3. Regular expression "word not ending with":
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
  **DB::**aaa
  **DB::**classa 
