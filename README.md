# React-Server-Notes


// Start with connecting express

//express: framework for creating servers

`const express = require('express')
const app = express()`

// assign server to run on port 8000 

`const PORT = 8000
const {faker} = require('@faker-js/faker')`

// app.listen takes in 2 parameters and is used to run the server
//the port and the function to run


`app.listen(PORT,() =>{
    console.log(`Server is up and running on port ${PORT}`)
})`


//from here to start the server run nodemon server.js



//Middleware 
//whatever is ran here will be applied to every route in the server before it runs

`app.use(express.json())
app.use(express.urlencoded({extended:true}))`

//the app.use are needed to put data into the body of the request so we can access it.
//These go in every file.




//create an instance of a user from the faker api

`const createUser = () =>{
    return {
        _id: faker.datatype.uuid(),
        first_name: faker.name.firstName(),
        last_name: faker.name.lastName(),
        email: faker.internet.email(),
        password: faker.internet.password(),
        phone_number: faker.phone.number()
    }
}`


//app.get takes in 2 parameters a path and what to do with the path

`app.get('/user',(req,res)=>{
    const user = createUser()
    res.json(user)
})


app.get('/user/:word',(req,res)=>{
    const word = req.params.word
    res.json(word)
})

app.post('/addUser',(req,res) => {
    //from post man we can console the request
    console.log(req.body)
    //and working backwards we can display the result as the request.body
    res.json(req.body)
})`
