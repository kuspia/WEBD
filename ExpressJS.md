# ExpressJS

a very popular framework of nodejs for making server (remmember we did the same for http)

![image](https://user-images.githubusercontent.com/63403330/182040062-fb8d2596-0d9b-4fa4-8d63-8cc0d478c629.png)

and tht's wht we see when a browser try making a request on ```localhost:4000/``` since clearly though browser is requesting but server is not repsonding on that url.

![image](https://user-images.githubusercontent.com/63403330/182040145-f24b4d45-5546-4737-8e38-bdb653451871.png)

_see you know_ C R U D _opeartion in db_ right?

![image](https://user-images.githubusercontent.com/63403330/182040475-d140a851-7191-4368-96ad-38961104e384.png)

so here in terms of express we have _POST GET PUT DELETE_

now u should understand that a browser when makes a request can be of four types as shown above so basically 

```app.get(), app.post(), app.put(), app.delete()``` handles those types of request 

> remember in case of http we have to check it from if(req.method === "get") like this to know what kind of request it is 

we will look into get and post carefully and rest u can learn by the time 

#### app.get() and app.post() ?

so what happens when a browser request a server on particular URL or route say ```localhost:3000/about``` so what happens it actually wants or try to get a response from the server
as soon as user hits the  URL or route so we say that a browser is trying to get something from the server which is taken care by ```app.get()```

however sometimes let's say during filling of the form from some URL or route it try to post the content of form from the browser so in this case we say that ```app.post()``` will actually 
take care of that content sent from the browser to the server on same URL or route.

so now before diving in let's make it clear about form 

listen very carefully 

```
 <form action="/api" method="GET">
      <h1>REGISTER</h1>
      <input placeholder="Enter Your Name" type="text" name="name" id="name" />
      <input
        placeholder="Enter Your Email"
        type="email"
        name="email"
        id="email"
      />
      <input
        placeholder="Enter Your Password"
        type="password"
        name="password"
        id="password"
      />
      <input type="submit" value="Login" />
    </form>
  ```
   
now here it says as soon as form will be submitted browser will make a request (it is of 4 types if u cn recall) on the /api route and request type will be a GET so it can be only handled 
by ```app.get('/api' , .... )``` 

now if we change method to POST it will be handled by ```app.post()``` exclusively 

> TODO try both methods one by one with the follwing code and predict the o/p 

```
const express = require("express")
const app = express()
const path = require("path")
app.get("/", (req , res) => {
res.sendFile( path.join(__dirname, 'i.html' ) )
});
app.get("/api" , (req , res)=>{
    console.log("ABOVE")
   return res.send("GET")
})
app.post("/api" , (req , res)=>{
    console.log("BELOW");
   return res.send("POST")
})
app.listen(3000)
```

Can u really execute /api route if the method is post??

answer yes, follow this URL http://localhost:3000/api ( u can actaully do it without submitting the form ) ...... ... . ... . .
  
u can try printing ```req.url``` and see the results for both methods 

u can try printing ```req.body``` and see in both methods 


```
const bodyp = require("body-parser")
app.use(bodyp.urlencoded({extended:false}))
```

use above lines for req.body 


> GET carries request parameter appended in URL string while POST carries request parameter in message body which makes it more secure way of transferring data from client
   
##### but do u know what exactly api is ?? it's ok a kind of route or url but in api we send 

