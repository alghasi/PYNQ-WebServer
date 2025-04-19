Taksun Simple Web Server
Introdution
Backend Development
Frontend Development
Using Internet Template Code
Implementing AJAX
Using JavaScript Timer
Data Visualization with Chart.js
Hardware and vivado
XADC Driver in Linux
Web Server Sample Code for Backend
Import linrary
Read data from XADC driver in python
Override HTTP Handler method
Function for running server
Run server function in theread
Introdution
In this project, a web interface has been set up. To implement it, 3 main parts are needed:

1- Backend program

2- Web interface for the client

3- Hardware

Backend
Backend programming for a web server using Python involves creating the server-side logic that handles requests from clients (such as web browsers or mobile apps), processes data, interacts with databases, and sends responses back to the client. Python is a popular choice for backend development due to its simplicity, readability, and the availability of powerful frameworks and libraries. Below is an explanation of the key concepts and components involved in backend programming with Python:

Key Components of Backend Programming
Web Server:

A web server is software that listens for incoming HTTP requests from clients and sends back HTTP responses.
In Python, you can create a web server using frameworks like Flask, Django, or FastAPI, or even the built-in http.server module for simpler use cases.
HTTP Protocol:

The backend communicates with the client using the HTTP protocol. Common HTTP methods include:
GET: Retrieve data from the server.
POST: Send data to the server (e.g., form submissions).
PUT/PATCH: Update existing data.
DELETE: Remove data.
Routing:

Routing maps URLs (endpoints) to specific functions in the backend code. For example:
A request to /users might return a list of users.
A request to /products/123 might return details about a specific product.
Request Handling:

The backend processes incoming requests, extracts data (e.g., query parameters, JSON payloads), and performs actions like querying a database or running business logic.
Response Generation:

After processing a request, the backend sends a response to the client, typically in the form of HTML, JSON, or other formats.
Database Interaction:

Backend systems often interact with databases to store and retrieve data. Python supports databases like PostgreSQL, MySQL, SQLite, and MongoDB through libraries such as SQLAlchemy, Psycopg2, and PyMongo.
Authentication and Authorization:

Backend systems often handle user authentication (e.g., login) and authorization (e.g., checking if a user has permission to access a resource).
Middleware:

Middleware is code that runs before or after the main request handler. It can be used for tasks like logging, authentication, or error handling.
Python Frameworks for Backend Development
Flask:

A lightweight and flexible micro-framework for building web applications.
Ideal for small to medium-sized projects.
Provides basic functionality, allowing developers to add only the components they need.
Django:

A full-stack web framework with built-in features like an ORM (Object-Relational Mapper), admin panel, and authentication.
Ideal for large, complex projects.
Follows the "batteries-included" philosophy, providing many tools out of the box.
FastAPI:

A modern framework for building APIs with automatic documentation (OpenAPI and Swagger) and high performance.
Ideal for building RESTful APIs.
Known for its speed and support for asynchronous programming.
Built-in http.server:

Python's standard library includes a basic HTTP server for simple use cases.
Not suitable for production but useful for testing or learning.
This library is also used in this example

By combining Python's simplicity with powerful frameworks, you can build robust and scalable backend systems for web applications.

Front end application
Client web-based interfaces refer to the user-facing part of a web application that runs in a web browser. These interfaces are built using web technologies such as HTML, CSS, and JavaScript, and they allow users to interact with a web application or service. Here's a breakdown of the key components and concepts:

1. HTML (HyperText Markup Language)
Purpose: HTML provides the structure and content of the web page. It defines elements like headings, paragraphs, buttons, forms, and links.
Role in Client Interface: HTML is the backbone of the web interface, creating the basic layout and elements that users interact with.
2. CSS (Cascading Style Sheets)
Purpose: CSS is used to style and design the HTML elements. It controls the visual presentation, including colors, fonts, spacing, and layout.
Role in Client Interface: CSS ensures the interface is visually appealing and user-friendly, enhancing the overall user experience.
3. JavaScript
Purpose: JavaScript is a programming language that enables interactivity and dynamic behavior on web pages. It can manipulate HTML and CSS, handle user events, and communicate with servers.
Role in Client Interface: JavaScript makes the interface responsive and interactive. For example, it can validate form inputs, update content without reloading the page (AJAX), or create animations.
Summary
Client web-based interfaces are the front-end part of web applications that users interact with directly. They are built using HTML, CSS, and JavaScript, often enhanced by frameworks and libraries. These interfaces rely on APIs to communicate with servers, prioritize responsive and accessible design, and aim to deliver a seamless and engaging user experience.

use internet template code
instead of writing the whole code from sratch, use the template code

"https://themewagon.github.io/darkpan/"



Use AJAX
AJAX, which stands for Asynchronous JavaScript and XML, is a web development technique that allows web pages to communicate with a server asynchronously without requiring a full page reload. This means that specific parts of a web page can be updated dynamically in the background, while the rest of the page remains unchanged. AJAX is not a single technology but a combination of several technologies, including JavaScript, XML (or JSON, which is more commonly used today), HTML, and CSS. JavaScript is used to send and receive data from the server, while XML or JSON formats are used to structure the data being exchanged. The key advantage of AJAX is that it enhances user experience by making web applications faster and more interactive, as users can interact with the page without interruptions caused by full page reloads. For example, when you type a search query into Google, the suggestions that appear dynamically are powered by AJAX. Similarly, AJAX is widely used in features like live form validation, auto-complete, and real-time updates in social media feeds. By enabling asynchronous communication, AJAX reduces server load and bandwidth usage, making web applications more efficient and responsive.

Use AI
We can use AI to write a simple code faster

  function fetchData() {
    fetch('posts/1') // URL of the Python server
       .then(response => {
         if (!response.ok) {
              throw new Error('Network response was not ok');
              }
           return response.json();
           })
         .then(data => {
         //add data to chart
         addData(lab,data.val[0],data.val[1]);
         lab = lab+1;
         //show data in label 
         document.getElementById('result').innerHTML = `
          <h2>Title: ${data.title}</h2>
          <p>Body: ${data.val}</p>
              `;
           })
          .catch(error => {
  document.getElementById('result').innerHTML = 'Error fetching data';
                });
    };
Use Timer in JS
setInterval(fetchData, 1500);
chart in JS
Chart.js is a popular open-source JavaScript library used for creating responsive, interactive, and visually appealing charts and graphs on web pages. It is lightweight, easy to use, and highly customizable, making it a go-to choice for developers who need to visualize data in their web applications. Chart.js supports a wide variety of chart types, including bar charts, line charts, pie charts, doughnut charts, radar charts, polar area charts, and more. The library uses HTML5's <canvas> element to render charts, ensuring smooth performance and compatibility with modern browsers. One of the key features of Chart.js is its simplicity—developers can create charts with just a few lines of code by defining datasets, labels, and configuration options. Additionally, Chart.js is highly interactive; users can hover over data points to see tooltips, click to highlight sections, or even animate charts for a dynamic experience. The library also supports responsiveness, meaning charts automatically adjust to fit different screen sizes, making them ideal for both desktop and mobile applications. With its extensive documentation, active community, and flexibility, Chart.js is a powerful tool for data visualization in web development.

   function addData(label, data1,data2) {
     window.myChart2.data.labels.push(label); // Add the new label
     window.myChart2.data.datasets[0].data.push(data1);
     window.myChart2.data.datasets[1].data.push(data2);
     window.myChart2.update(); // Update the chart
   }
Hardware
In this project, an attempt has been made to use symbolic data for display on the web. In this minimal hardware setup, the XADC sensor is used to read the processor temperature and core voltage. Additionally, to demonstrate that the XADC is directly accessible from within the PS (Processing System), no bitstream was used, and the project was even built without the need for the VIVADO project.

Several objectives have been pursued in reading the sensors:

Using XADC directly without an IP core in the PL (Programmable Logic).
Demonstrating the drivers provided for XADC within Linux.
Connecting Python to Linux drivers and reading data.
XADC Driver in Linux
driver address for xadc is /sys/bus/iio/devices/iio:device0/

!ls /sys/bus/iio/devices/iio:device0/
dev			  in_voltage2_vccbram_raw    in_voltage6_vrefp_scale
events			  in_voltage2_vccbram_scale  in_voltage7_vrefn_raw
in_temp0_offset		  in_voltage3_vccpint_raw    in_voltage7_vrefn_scale
in_temp0_raw		  in_voltage3_vccpint_scale  name
in_temp0_scale		  in_voltage4_vccpaux_raw    of_node
in_voltage0_vccint_raw	  in_voltage4_vccpaux_scale  power
in_voltage0_vccint_scale  in_voltage5_vccoddr_raw    sampling_frequency
in_voltage1_vccaux_raw	  in_voltage5_vccoddr_scale  subsystem
in_voltage1_vccaux_scale  in_voltage6_vrefp_raw      uevent
for example reading adc raw data for temperature is:

!cat /sys/bus/iio/devices/iio:device0/in_temp0_raw
2683
 

Taksun Simple Web Server
web server sample code for backend
Import linrary
from http.server import SimpleHTTPRequestHandler, HTTPServer
from urllib.parse import urlparse, parse_qs
import threading
import json
Read data from XADC driver in python
def read_xadc_temperature():
    try:
        with open("/sys/bus/iio/devices/iio:device0/in_temp0_raw", "r") as raw_file, \
             open("/sys/bus/iio/devices/iio:device0/in_voltage0_vccint_scale", "r") as scale_file,\
             open("/sys/bus/iio/devices/iio:device0/in_voltage0_vccint_raw", "r") as vcore_file:
            raw = int(raw_file.read().strip())
            scale = float(scale_file.read().strip())
            core = int(vcore_file.read().strip()) 
            temp = (raw *503.975/4096) -273
            vcore = scale * core;
            return [temp,vcore]
    except Exception as e:
        print(f"Error reading XADC temperature: {e}")
        return None
Override HTTP Handler method
class MyHandler(SimpleHTTPRequestHandler):
    def do_GET(self):
        if self.path == '/posts/1':
            posts = {
                1: {
                    "id": 1,
                    "title": "temp",
                    "val": read_xadc_temperature()
                    }
                    }
            self.send_response(200)  # OK
            self.send_header('Content-type', 'application/json')
            self.end_headers()
            response = json.dumps(posts[1]).encode('utf-8')
            self.wfile.write(response)

        else:
            super().do_GET()

    def log_message(self, format, *args):
        pass

    def log_request(self, format, *args):
        pass
Function for running server
def run_server():
    PORT = 8000
    server_address = ('', PORT)
    httpd = HTTPServer(server_address, MyHandler)
    print(f"Serving on port {PORT}...")
    httpd.serve_forever()
Run server function in theread
server_thread = threading.Thread(target=run_server)
server_thread.daemon = True  
server_thread.start()
