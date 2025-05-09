# Taksun Simple Web Server 

## Table of Contents
- [Introduction](#introduction)
- [Backend Development](#backend-development)
- [Frontend Development](#frontend-development)
- [Using Internet Template Code](#using-internet-template-code)
- [Implementing AJAX](#implementing-ajax)
- [Using JavaScript Timer](#using-javascript-timer)
- [Data Visualization with Chart.js](#data-visualization-with-chartjs)
- [Hardware and Vivado](#hardware-and-vivado)
- [XADC Driver in Linux](#xadc-driver-in-linux)
- [Web Server Sample Code for Backend](#web-server-sample-code-for-backend)


## Watch video of workshop on youtube
[![Watch video of workshop on youtube](PYNQ3.jpg)](https://youtu.be/pFl-Db5gi-k)


## Introduction
In this project, a web interface has been set up. To implement it, 3 main parts are needed:

1. Backend program  
2. Web interface for the client  
3. Hardware  

## Backend Development
Backend programming for a web server using Python involves creating the server-side logic that handles requests from clients, processes data, interacts with databases, and sends responses back to the client.

### Key Components of Backend Programming
1. **Web Server**: Software that listens for incoming HTTP requests and sends back responses.
2. **HTTP Protocol**: Methods like GET, POST, PUT/PATCH, DELETE.
3. **Routing**: Maps URLs to specific functions.
4. **Request Handling**: Processes incoming requests and extracts data.
5. **Response Generation**: Sends responses in HTML, JSON, etc.
6. **Database Interaction**: Libraries for PostgreSQL, MySQL, etc.
7. **Authentication**: Handles user login and permissions.
8. **Middleware**: Code that runs before/after main request handler.

### Python Frameworks
1. **Flask**: Lightweight micro-framework.
2. **Django**: Full-stack framework with many built-in features.
3. **FastAPI**: Modern framework for building APIs.
4. **Built-in `http.server`**: Basic HTTP server for simple use cases (used in this example).

## Frontend Development
Client web-based interfaces are built using:

1. **HTML**: Structure and content.
2. **CSS**: Styling and design.
3. **JavaScript**: Interactivity and dynamic behavior.

## Using Internet Template Code
Instead of writing code from scratch, use template code from:  
[https://themewagon.github.io/darkpan/](https://themewagon.github.io/darkpan/)

![Darkpen](img/Darkpen.png)

## Implementing AJAX
AJAX (Asynchronous JavaScript and XML) allows web pages to communicate with a server asynchronously without full page reloads. Example JavaScript code:

```javascript
function fetchData() {
  fetch('posts/1')
    .then(response => response.json())
    .then(data => {
      addData(lab, data.val[0], data.val[1]);
      lab = lab + 1;
      document.getElementById('result').innerHTML = `
        <h2>Title: ${data.title}</h2>
        <p>Body: ${data.val}</p>`;
    })
    .catch(error => {
      document.getElementById('result').innerHTML = 'Error fetching data';
    });
}
```
## Using JavaScript Timer
```javascript
setInterval(fetchData, 1500);
```
## Data Visualization with Chart.js
Chart.js is a JavaScript library for creating responsive, interactive charts. Example function to add data:

```javascript
function addData(label, data1, data2) {
  window.myChart2.data.labels.push(label);
  window.myChart2.data.datasets[0].data.push(data1);
  window.myChart2.data.datasets[1].data.push(data2);
  window.myChart2.update();
}
```
## Hardware and Vivado
This project uses symbolic data for display. The XADC sensor reads processor temperature and core voltage. Key objectives:

Using XADC directly without an IP core in PL.

Demonstrating Linux drivers for XADC.

Connecting Python to Linux drivers.

XADC Driver in Linux
Driver address: /sys/bus/iio/devices/iio:device0/

Example reading temperature:

```bash
cat /sys/bus/iio/devices/iio:device0/in_temp0_raw
Temperature calculation:
temperature=RawData×503.975/4096−273
```
temperature= 
4096
RawData×503.975−273

## Web Server Sample Code for Backend
Import Libraries
```python
from http.server import SimpleHTTPRequestHandler, HTTPServer
from urllib.parse import urlparse, parse_qs
import threading
import json
```
## Read Data from XADC Driver
```python
def read_xadc_temperature():
    try:
        with open("/sys/bus/iio/devices/iio:device0/in_temp0_raw", "r") as raw_file, \
             open("/sys/bus/iio/devices/iio:device0/in_voltage0_vccint_scale", "r") as scale_file, \
             open("/sys/bus/iio/devices/iio:device0/in_voltage0_vccint_raw", "r") as vcore_file:
            raw = int(raw_file.read().strip())
            scale = float(scale_file.read().strip())
            core = int(vcore_file.read().strip())
            temp = (raw * 503.975 / 4096) - 273
            vcore = scale * core
            return [temp, vcore]
    except Exception as e:
        print(f"Error reading XADC temperature: {e}")
        return None
```
## Override HTTP Handler
```python
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
            self.send_response(200)
            self.send_header('Content-type', 'application/json')
            self.end_headers()
            response = json.dumps(posts[1]).encode('utf-8')
            self.wfile.write(response)
        else:
            super().do_GET()
```
## Run Server
```python
def run_server():
    PORT = 8000
    server_address = ('', PORT)
    httpd = HTTPServer(server_address, MyHandler)
    print(f"Serving on port {PORT}...")
    httpd.serve_forever()

server_thread = threading.Thread(target=run_server)
server_thread.daemon = True
server_thread.start()
```
