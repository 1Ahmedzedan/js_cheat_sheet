# API : 

<img src="https://github.com/1Ahmedzedan/js_cheat_sheet/assets/116225212/17115824-605a-457e-bb08-6f6076ec176b" alt="Picture" style="display: block; margin: 0 auto" />

# AJAX(Asynchronous JavaScript And XML) : 
```java script
const request = new XMLHttpRequest() ;
request.open('GET' , 'url') ;
request.send() ;
request.addEventListener('load' , ()=>{
      const [data] = JSON.parse(request.responseText) ;
      /*
          deal with response 
      */
});
```
## explain code :
- const request = new XMLHttpRequest() ;
  - The XMLHttpRequest object can be used to exchange data with a web server behind the scenes. This means that it is possible to update parts of a web page, without     reloading the whole page.
