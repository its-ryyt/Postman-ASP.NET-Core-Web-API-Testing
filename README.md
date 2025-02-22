TodoMvcSolution ASP.NET Core 2.0
SmartIT
How to write simple Todo CRUD ASP.NET MVC Application.
Visual Studio 2017, ASP.NET Core 2.0

By John kocer- SmartIT

How to Use Swagger with ASP.NET Core Web APIs. 
Visual Studio 2017, ASP.NET Core 2.0, By John Kocer- SmartIT
Tags: Swagger, Visual Studio 2017,  ASP.NET Core, Web API, API Test, Do-to List, SmartIT 


In this session, we will learn 

-How to consume Todo inmemory database using TodoRepository.

-How to create custom ASP.NET MVC custom controller with CRUD operations.

-List of Objects

-Create a new insert object via View

-Update and object via Edit View

-Delete an Item via Delete View.

-Write HttpPost Create API method.

-Write Httppost Edit API method.

-Write HttpPost Delete API method.

-SmartIT DebugTraceHelper tool

- A lab exercise for you to demonstrate what have you learned from this training material to create your own Employee CRUD operation using EmployeeRepository included in this training material.
Download source code from GitHub: https://github.com/SmartITAz/TodoMvcSolution

<h2> How to use with Postman </h2>
</br>

<span> Manual Testing with Postman </span>

![image](https://github.com/user-attachments/assets/e03a6970-7734-4613-9447-4b11f18526cb)
</br>

If you are a developer, tester, or a manager, sometimes understanding various methods of API can be a challenge when building and consuming the application.

Generating good documentation and help pages for your Web API using Postman with .NET Core is as easy as making some HTTP calls.

Let’s start downloading simple To-do projects from GitHub.

<pre>  
  1.) Download and run the below TodoMvcSolution from this <a href="https://github.com/SmartITAz/TodoMvcSwaggerSolution">link</a>.

  <img src="https://github.com/user-attachments/assets/9ee2720a-372b-439c-8438-f685965dd964" >

</pre>

1.) Download Postman
</br>

Postman is a Google Chrome application for testing API calls. You can [download and install Postman](https://www.postman.com/) from below web site.

<pre>
  Here are the APIs we can test -  Get, Post, Put and Delete for this application.

  <img src="https://github.com/user-attachments/assets/92841808-df6d-4c52-b46d-5b8e467e82fe" >
</pre>

Here are the Web APIs we want to test.

```csharp
// Copyright 2017 (c) SmartIT. All rights reserved.
// By John Kocer
// This file is for Swagger test, this application does not use this file
using System.Collections.Generic;
using Microsoft.AspNetCore.Mvc;
using SmartIT.Employee.MockDB;

namespace TodoAngular.Ui.Controllers
{
  [Produces("application/json")]
  [Route("api/Todo")]
  public class TodoApiController : Controller
  {
    TodoRepository _todoRepository = new TodoRepository();

    [Route("~/api/GetAllTodos")]
    [HttpGet]
    public IEnumerable<SmartIT.Employee.MockDB.Todo> GetAllTodos()
    {
      return _todoRepository.GetAll();
    }

    [Route("~/api/AddTodo")]
    [HttpPost]
    public SmartIT.Employee.MockDB.Todo AddTodo([FromBody]SmartIT.Employee.MockDB.Todo item)
    {
      return _todoRepository.Add(item);
    }

    [Route("~/api/UpdateTodo")]
    [HttpPut]
    public SmartIT.Employee.MockDB.Todo UpdateTodo([FromBody]SmartIT.Employee.MockDB.Todo item)
    {
      return  _todoRepository.Update(item);
    }

    [Route("~/api/DeleteTodo/{id}")]
    [HttpDelete]
    public void Delete(int id)
    {
      var findTodo = _todoRepository.FindById(id);
      if (findTodo != null)
        _todoRepository.Delete(findTodo);
    }
  }
}
```

</br>

<b>Note</b> - Your local port number may be different than mine. Use your local port number.

<pre>
  <i> 
    http://localhost:63274/api/GetAllTodos // GET 
    http://localhost:63274/api/AddTodo //POST
    http://localhost:63274/api/UpdateTodo //PUT
    http://localhost:63274/api/DeleteTodo/5 // DELETE 
  </i>
</pre>
</br>

<h2> Testing GET with Postman </h2>

- Testing **GET** is very easy. First, we need to set **HTTP Action** from the drop-down list as **GET**.
- Then, we need to type or paste into the **API URL** box.
- Then, click the blue **SEND** button.
</br>

If the GET is successful, we see the status: <span style="color:green;">200 OK</span>.

<pre>
  <img src="https://github.com/user-attachments/assets/14fa0bf5-45ee-4ba0-8802-2c77245cb4df" >
</pre>
</br>

<h2> Testing POST with Postman </h2>

- First, we need to set Http Action from the dropdown list as **POST**.
- Then, we need to type or paste into the API URL box.
- AddTodo API accepts a Todo object in JSON format. We need to pass a new Todo JSON data.
- To pass **JSON** data we need to Select Body Tap.
- Select the Raw
- Select **JSON(Application/JSON)** as text format.
- Write or paste your Todo JSON data.
- Then, click the blue **SEND** button.
</br>

If the POST is successful, we see the status: <span style="color:green;">200 OK</span>.

You will see Status:200 for success and the return value in the Return Body tab. We sent Publish Postman Todo item with id=0 and we received id=5 as result.

<pre>
  <img src="https://github.com/user-attachments/assets/be2058f8-934d-436d-8d97-3c342a8d840d" >
</pre>
</br>

<h2> Testing PUT with Postman </h2>

- First, we need to set HTTP Action from the dropdown list as **PUT**.
- Then, we need to type or paste into the API URL.
- UpdateTodo API accepts a Todo object in **JSON** format. We need to pass an existing Todo JSON data.
- To pass **JSON** data we need to Select Body Tab
- Select the Raw format
- Select **JSON(Application/JSON)** as text format.
- Write or paste your Todo JSON
- Then click the blue **SEND**

If the PUT is successful, we see the status: <span style="color:green;">200 OK</span>.

You will see Status:200 for success and the return value in the Return Body Tab. We sent Publish Postman Todo item with "name": "Publish Postman-In progress" and we receive an updated todo result.

<pre>
  <img src="https://github.com/user-attachments/assets/ef0a173d-bd66-4e53-a7cc-b239fb0cd2d0" >
</pre>
</br>

<h2> Testing DELETE with Postman </h2>

- First, we need to set Http Action from the dropdown list as **DELETE**.
- Then, we need to type or paste into the API URL box.
- **DeleteTodo/5** API accepts an id on the  We need to pass an existing Todo with an Id value.
- Then, click the blue **SEND** button.

If the DELETE is successful, we see the status: <span style="color:green;">200 OK</span>.

<pre>
  <img src="https://github.com/user-attachments/assets/df69e86c-f480-49d9-8d07-930affa68c23" >
</pre>
</br>
