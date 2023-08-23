# API : 

<img src="https://github.com/1Ahmedzedan/js_cheat_sheet/assets/116225212/17115824-605a-457e-bb08-6f6076ec176b" alt="Picture" style="display: block; margin: 0 auto" />

# AJAX(Asynchronous JavaScript And XML) : 
```java script
const request = new XMLHttpRequest() ;
request.open('mehtod' , 'url' , true) ;
request.send() ;
request.addEventListener('load' , ()=>{
      const [data] = JSON.parse(request.responseText) ;
      /*
          deal with response 
      */
});
```
## explain code :
`XMLHttpRequest()`
- The XMLHttpRequest object can be used to exchange data with a web server behind the scenes. This means that it is possible to update parts of a web page, without     reloading the whole page.

`request.open('mehtod' , 'url' , async)`
- method : the type of request : 'GET' or 'POST' .
- url : the server (file location) .
- async : true for asynchronous , false for synchronous (by default true (asynchronous)) .
`request.send()` 
- send() : Sends the request to the server (used for GET) .
- send(string) : Sends the request to the server (used for POST) .

`JSON.parse()`
- convert json string written in json format to java script object
> **Note**
> `JSON.stringify()` convert js object to json format

### some property to deal with response : 
- `request.responseText`
  - return response from server in a json format
- `request.readystate`
  -  returns the state an XMLHttpRequest client is in. An XHR client exists in one of the following states :
  
  Value |        State       | Description
  ------|:------------------:|-------------------------------------------------------------------:
  0     | UNSET              | Client has been created. `open()` not called yet.
  1     | OPENED             | `open()` has been called.
  2     | HEADERS_RECEIVED   | `send()` has been called, and headers and status are available.
  3     | LOADING            | Downloading; `responseText` holds partial data.
  4     | DONE               | The operation is complete.

>**Note**
>[read more]((https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState)https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState) about state property .
