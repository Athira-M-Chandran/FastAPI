# FastAPI
A modern web framework for building APIs with Python.<br>
FastAPI is known for its speed, simplicity, and type annotations that enable automatic data validation and documentation.<br>

Here's a step-by-step guide to get you started with FastAPI:

Step 1: Installation
Make sure you have Python 3.7 or above installed. You can create a virtual environment if you prefer. Then, use pip to install FastAPI and uvicorn, which is a high-performance ASGI server: <br>
> `pip install fastapi uvicorn`

Step 2: Hello World<br>
Create a new Python file, for example, main.py, and open it in a text editor. Add the following code to create a basic FastAPI application and define a simple route:

>`from fastapi import FastAPI<br>
 > app = FastAPI()

  > @app.get("/")<br>
  > def read_root():<br>
  >  <t> return {"Hello": "World"}`
    
This code sets up a FastAPI application and defines a route at the root URL ("/") using the @app.get decorator.<br> The function read_root() is executed when a GET request is made to the root URL and returns a JSON response.

Step 3: Run the Application<br>
To start the application, open a terminal or command prompt, navigate to the directory where main.py is located, and run the following command:

> `uvicorn main:app --reload`

The main:app argument tells uvicorn to look for the app object in the main.py file. The --reload option enables auto-reloading, so the server restarts whenever you make changes to the code.

Step 4: Test the API<br>
Open your web browser and navigate to http://localhost:8000. You should see the JSON response: {"Hello": "World"}.

Step 5: Adding Request Parameters<br>
FastAPI makes it easy to handle request parameters. Modify the code in main.py to include a route that accepts a parameter:

> `@app.get("/items/{item_id}") `

>  `def read_item(item_id: int): `

>    ` return {"item_id": item_id}`

In this example, the route "/items/{item_id}" expects an integer parameter called item_id. The parameter is automatically validated and converted to the appropriate type.

Step 6: Optional Parameters and Query Parameters <br>
You can also define optional parameters and query parameters. Update the code as follows:

>`from typing import Optional '

>  `@app.get("/items/{item_id}")`
 
 > `def read_item(item_id: int, q: Optional[str] = None): `
 
 >       if q:
 
 >          return {"item_id": item_id, "q": q}
 
 >       return {"item_id": item_id}
      
In this case, the q parameter is optional and has a default value of None. If a query parameter q is provided in the URL, it will be included in the response.<br>
Query parameters are appended to the URL using a ? character, followed by key-value pairs separated by &. They are used to provide additional optional data to the API.

For example, to pass the q parameter in the URL, you can do as follows:<br>
> http://localhost:8000/items/42?q=test 

In this case, 42 is the value for the item_id parameter, and test is the value for the q parameter.

