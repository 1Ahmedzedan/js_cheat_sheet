# API :

<img src="https://github.com/1Ahmedzedan/js_cheat_sheet/assets/116225212/82b0e6a8-46a3-48d3-be7b-3b79e641df48" alt="Picture" style="display: block; margin: 0 auto" />

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
## code explain :
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

> `JSON.stringify()` convert js object to json format

### some property to deal with response : 
- `request.responseText`
  - return response from server in a json format
- `request.readystate`
  -  returns the state an XMLHttpRequest client is in. An XHR client exists in one of the following states :
  
  Value |        State       |Description
  ------|:------------------:|-------------------------------------------------------------------:
  0     | UNSET              |Client has been created. `open()` not called yet.
  1     | OPENED             |`open()` has been called.
  2     | HEADERS_RECEIVED   |`send()` has been called, and headers and status are available.
  3     | LOADING            |Downloading; `responseText` holds partial data.
  4     | DONE               |The operation is complete.

>[read more](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState) about `readstate` property .

- `request.status`

 Value  | Status
  ------|-------------------:|
  200   | Ok                 |
  404   | Not Found          |

  >[read more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) about `status code` .
---

# Fetch and Promise :
``` java script
fetch('url' , options)
.then(response=>response.json()) // call when promise resolved 
.then(data=>{                    // call when promise resolved
      // deal with data 
})
.catch(error=>{                // call when promise rejected 
      // deal with error 
})
.finally(()=>{                // call any time when promise (rejected or resolved )
      // deal with finally callback function  
}); 
```
## code explain :

`fetch(url , options)`

- url : the server (file location) .
- options : select (HTTP request method type , headers , send body of request)
  - ex :
  ```
      let options = {
      method: 'POST',
      headers: {
          'Content-Type': 
              'application/json;charset=utf-8'
      },
      body: JSON.stringify(user)
      }
  ```
- return response from server
>[read more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) about `HTTP request method` .

`then()`

- call when promise resolved.

 `catch()`

 - call when promise rejected (exist any error).

`finally()`

- call in any case promise (resolved or rejected).

## throw error manually : 
- **Code 1** : 
``` java script
fetch('url' , options)
.then(response=>{
      if(!respone.ok) throw new Error("error massege") ; // throw error manually by throw new ebject Error to catch
      return response.json() ; 
}) 
.then(data=>{                 
      // deal with data 
})
.catch(error=>{                
      // deal with error 
})
.finally(()=>{               
      // deal with finally callback function  
}); 
```

- **Code 2** : 
``` java script
getJSON('url' , "error message")
.then(data=>{                 
      // deal with data 
})
.catch(error=>{                
      // deal with error 
})
.finally(()=>{               
      // deal with finally callback function  
}); 
```

`getJSON('url' , "error message")`

- url : the server (file location) .
- return response.json() .
---
## Promises with Async / await : 
- `Async` key word Before Function Mean This Function Return A Promise .
- `Async` And `Await` Help In Creating Asynchronous Promise Behavior Cleanner Style .
- `Await` Works Only Inside Async Function .
- `Await` Make JS Wait For The Promise Result .  
- `Await` Is More Elegant Syntex Of Getting Promise Result
- **Code** :
``` java script
async function getJson(){
      let res = await fetch('url') ;
      let data = await res.json() ;
      return data ; 
}
```
## try and catch syntax : 
``` java script
async function getJson(){
      try{
            let res = await fetch('url') ;
            if(!res.ok) throw new Error('failed') ; 
            let data = await res.json() ;
            return data ; 
      }
      catch(error){
            // deal with error
      }
      finally{
            console.log('finish') ;
            // call in any case promise (resolve or rejected)
      }
}
```
**IMPORTANT!!**
> [read more](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) about `Promise` .
----
