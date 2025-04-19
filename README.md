{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<div class=\"alert bg-primary\" style=\"text-align:center;\"><font size=\"6\"><b>Taksun Simple Web Server </b></font></div>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* [Introdution](#Introdution)\n",
    "* [Backend Development](#Backend)\n",
    "* [Frontend Development](#Front-end-application)\n",
    "* [Using Internet Template Code](#use-internet-template-code)\n",
    "* [Implementing AJAX](#Use-AJAX)\n",
    "* [Using JavaScript Timer](#Use-Timer-in-JS)\n",
    "* [Data Visualization with Chart.js](#chart-in-JS)\n",
    "* [Hardware and vivado](#Hardware)\n",
    "* [XADC Driver in Linux](#XADC-Driver-in-Linux)\n",
    "* [Web Server Sample Code for Backend](#web-server-sample-code-for-backend)\n",
    "* [Import linrary](#import-linrary)\n",
    "* [Read data from XADC driver in python](#Read-data-from-XADC-driver-in-python)\n",
    "* [Override HTTP Handler method](#Override-HTTP-Handler-method)\n",
    "* [Function for running server](#Function-for-running-server)\n",
    "* [Run server function in theread](#Run-server-function-in-theread)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "# Introdution\n",
    "In this project, a web interface has been set up. To implement it, 3 main parts are needed:\n",
    "\n",
    "1- Backend program\n",
    "\n",
    "2- Web interface for the client\n",
    "\n",
    "3- Hardware\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Backend\n",
    "\n",
    "Backend programming for a web server using Python involves creating the server-side logic that handles requests from clients (such as web browsers or mobile apps), processes data, interacts with databases, and sends responses back to the client. Python is a popular choice for backend development due to its simplicity, readability, and the availability of powerful frameworks and libraries. Below is an explanation of the key concepts and components involved in backend programming with Python:\n",
    "\n",
    "---\n",
    "\n",
    "### **Key Components of Backend Programming**\n",
    "\n",
    "1. **Web Server**:\n",
    "   - A web server is software that listens for incoming HTTP requests from clients and sends back HTTP responses.\n",
    "   - In Python, you can create a web server using frameworks like Flask, Django, or FastAPI, or even the built-in `http.server` module for simpler use cases.\n",
    "\n",
    "2. **HTTP Protocol**:\n",
    "   - The backend communicates with the client using the HTTP protocol. Common HTTP methods include:\n",
    "     - `GET`: Retrieve data from the server.\n",
    "     - `POST`: Send data to the server (e.g., form submissions).\n",
    "     - `PUT`/`PATCH`: Update existing data.\n",
    "     - `DELETE`: Remove data.\n",
    "\n",
    "3. **Routing**:\n",
    "   - Routing maps URLs (endpoints) to specific functions in the backend code. For example:\n",
    "     - A request to `/users` might return a list of users.\n",
    "     - A request to `/products/123` might return details about a specific product.\n",
    "\n",
    "4. **Request Handling**:\n",
    "   - The backend processes incoming requests, extracts data (e.g., query parameters, JSON payloads), and performs actions like querying a database or running business logic.\n",
    "\n",
    "5. **Response Generation**:\n",
    "   - After processing a request, the backend sends a response to the client, typically in the form of HTML, JSON, or other formats.\n",
    "\n",
    "6. **Database Interaction**:\n",
    "   - Backend systems often interact with databases to store and retrieve data. Python supports databases like PostgreSQL, MySQL, SQLite, and MongoDB through libraries such as SQLAlchemy, Psycopg2, and PyMongo.\n",
    "\n",
    "7. **Authentication and Authorization**:\n",
    "   - Backend systems often handle user authentication (e.g., login) and authorization (e.g., checking if a user has permission to access a resource).\n",
    "\n",
    "8. **Middleware**:\n",
    "   - Middleware is code that runs before or after the main request handler. It can be used for tasks like logging, authentication, or error handling.\n",
    "\n",
    "---\n",
    "\n",
    "### **Python Frameworks for Backend Development**\n",
    "\n",
    "1. **Flask**:\n",
    "   - A lightweight and flexible micro-framework for building web applications.\n",
    "   - Ideal for small to medium-sized projects.\n",
    "   - Provides basic functionality, allowing developers to add only the components they need.\n",
    "\n",
    "2. **Django**:\n",
    "   - A full-stack web framework with built-in features like an ORM (Object-Relational Mapper), admin panel, and authentication.\n",
    "   - Ideal for large, complex projects.\n",
    "   - Follows the \"batteries-included\" philosophy, providing many tools out of the box.\n",
    "\n",
    "3. **FastAPI**:\n",
    "   - A modern framework for building APIs with automatic documentation (OpenAPI and Swagger) and high performance.\n",
    "   - Ideal for building RESTful APIs.\n",
    "   - Known for its speed and support for asynchronous programming.\n",
    "\n",
    "4. **Built-in `http.server`**:\n",
    "   - Python's standard library includes a basic HTTP server for simple use cases.\n",
    "   - Not suitable for production but useful for testing or learning.\n",
    "   \n",
    "This library is also used in this example\n",
    "\n",
    "---\n",
    "\n",
    "By combining Python's simplicity with powerful frameworks, you can build robust and scalable backend systems for web applications."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Front end application\n",
    "\n",
    "Client web-based interfaces refer to the user-facing part of a web application that runs in a web browser. These interfaces are built using web technologies such as HTML, CSS, and JavaScript, and they allow users to interact with a web application or service. Here's a breakdown of the key components and concepts:\n",
    "\n",
    "### 1. **HTML (HyperText Markup Language)**\n",
    "   - **Purpose**: HTML provides the structure and content of the web page. It defines elements like headings, paragraphs, buttons, forms, and links.\n",
    "   - **Role in Client Interface**: HTML is the backbone of the web interface, creating the basic layout and elements that users interact with.\n",
    "\n",
    "### 2. **CSS (Cascading Style Sheets)**\n",
    "   - **Purpose**: CSS is used to style and design the HTML elements. It controls the visual presentation, including colors, fonts, spacing, and layout.\n",
    "   - **Role in Client Interface**: CSS ensures the interface is visually appealing and user-friendly, enhancing the overall user experience.\n",
    "\n",
    "### 3. **JavaScript**\n",
    "   - **Purpose**: JavaScript is a programming language that enables interactivity and dynamic behavior on web pages. It can manipulate HTML and CSS, handle user events, and communicate with servers.\n",
    "   - **Role in Client Interface**: JavaScript makes the interface responsive and interactive. For example, it can validate form inputs, update content without reloading the page (AJAX), or create animations.\n",
    "\n",
    "---\n",
    "\n",
    "### Summary\n",
    "Client web-based interfaces are the front-end part of web applications that users interact with directly. They are built using HTML, CSS, and JavaScript, often enhanced by frameworks and libraries. These interfaces rely on APIs to communicate with servers, prioritize responsive and accessible design, and aim to deliver a seamless and engaging user experience."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## use internet template code\n",
    "instead of writing the whole code from sratch, use the template code\n",
    "\n",
    "\"https://themewagon.github.io/darkpan/\"\n",
    "\n",
    "\n",
    "![](img\\Darkpen.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Use AJAX\n",
    "AJAX, which stands for **Asynchronous JavaScript and XML**, is a web development technique that allows web pages to communicate with a server asynchronously without requiring a full page reload. This means that specific parts of a web page can be updated dynamically in the background, while the rest of the page remains unchanged. AJAX is not a single technology but a combination of several technologies, including **JavaScript**, **XML** (or JSON, which is more commonly used today), **HTML**, and **CSS**. JavaScript is used to send and receive data from the server, while XML or JSON formats are used to structure the data being exchanged. The key advantage of AJAX is that it enhances user experience by making web applications faster and more interactive, as users can interact with the page without interruptions caused by full page reloads. For example, when you type a search query into Google, the suggestions that appear dynamically are powered by AJAX. Similarly, AJAX is widely used in features like live form validation, auto-complete, and real-time updates in social media feeds. By enabling asynchronous communication, AJAX reduces server load and bandwidth usage, making web applications more efficient and responsive.\n",
    "\n",
    "## Use AI\n",
    "We can use AI to write a simple code faster \n",
    "\n",
    "```javascript\n",
    "  function fetchData() {\n",
    "    fetch('posts/1') // URL of the Python server\n",
    "       .then(response => {\n",
    "         if (!response.ok) {\n",
    "              throw new Error('Network response was not ok');\n",
    "              }\n",
    "           return response.json();\n",
    "           })\n",
    "         .then(data => {\n",
    "         //add data to chart\n",
    "         addData(lab,data.val[0],data.val[1]);\n",
    "         lab = lab+1;\n",
    "         //show data in label \n",
    "         document.getElementById('result').innerHTML = `\n",
    "          <h2>Title: ${data.title}</h2>\n",
    "          <p>Body: ${data.val}</p>\n",
    "              `;\n",
    "           })\n",
    "          .catch(error => {\n",
    "  document.getElementById('result').innerHTML = 'Error fetching data';\n",
    "                });\n",
    "    };\n",
    "```"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Use Timer in JS\n",
    "```javascript\n",
    "setInterval(fetchData, 1500);\n",
    "```"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## chart in JS\n",
    "\n",
    "**Chart.js** is a popular open-source JavaScript library used for creating responsive, interactive, and visually appealing charts and graphs on web pages. It is lightweight, easy to use, and highly customizable, making it a go-to choice for developers who need to visualize data in their web applications. Chart.js supports a wide variety of chart types, including bar charts, line charts, pie charts, doughnut charts, radar charts, polar area charts, and more. The library uses HTML5's `<canvas>` element to render charts, ensuring smooth performance and compatibility with modern browsers. One of the key features of Chart.js is its simplicity—developers can create charts with just a few lines of code by defining datasets, labels, and configuration options. Additionally, Chart.js is highly interactive; users can hover over data points to see tooltips, click to highlight sections, or even animate charts for a dynamic experience. The library also supports responsiveness, meaning charts automatically adjust to fit different screen sizes, making them ideal for both desktop and mobile applications. With its extensive documentation, active community, and flexibility, Chart.js is a powerful tool for data visualization in web development.\n",
    "\n",
    "```javascript\n",
    "   function addData(label, data1,data2) {\n",
    "     window.myChart2.data.labels.push(label); // Add the new label\n",
    "     window.myChart2.data.datasets[0].data.push(data1);\n",
    "     window.myChart2.data.datasets[1].data.push(data2);\n",
    "     window.myChart2.update(); // Update the chart\n",
    "   }\n",
    " ```"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Hardware\n",
    "In this project, an attempt has been made to use symbolic data for display on the web. In this minimal hardware setup, the XADC sensor is used to read the processor temperature and core voltage. Additionally, to demonstrate that the XADC is directly accessible from within the PS (Processing System), no bitstream was used, and the project was even built without the need for the VIVADO project.\n",
    "\n",
    "Several objectives have been pursued in reading the sensors:\n",
    "\n",
    "1. **Using XADC directly without an IP core in the PL (Programmable Logic)**.  \n",
    "2. **Demonstrating the drivers provided for XADC within Linux**.  \n",
    "3. **Connecting Python to Linux drivers and reading data**.\n",
    "\n",
    "## XADC Driver in Linux\n",
    "driver address for xadc is **/sys/bus/iio/devices/iio:device0/**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "dev\t\t\t  in_voltage2_vccbram_raw    in_voltage6_vrefp_scale\r\n",
      "events\t\t\t  in_voltage2_vccbram_scale  in_voltage7_vrefn_raw\r\n",
      "in_temp0_offset\t\t  in_voltage3_vccpint_raw    in_voltage7_vrefn_scale\r\n",
      "in_temp0_raw\t\t  in_voltage3_vccpint_scale  name\r\n",
      "in_temp0_scale\t\t  in_voltage4_vccpaux_raw    of_node\r\n",
      "in_voltage0_vccint_raw\t  in_voltage4_vccpaux_scale  power\r\n",
      "in_voltage0_vccint_scale  in_voltage5_vccoddr_raw    sampling_frequency\r\n",
      "in_voltage1_vccaux_raw\t  in_voltage5_vccoddr_scale  subsystem\r\n",
      "in_voltage1_vccaux_scale  in_voltage6_vrefp_raw      uevent\r\n"
     ]
    }
   ],
   "source": [
    "!ls /sys/bus/iio/devices/iio:device0/"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "for example reading adc raw data for temperature is:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "2683\r\n"
     ]
    }
   ],
   "source": [
    "!cat /sys/bus/iio/devices/iio:device0/in_temp0_raw"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "$$ temperature = \\frac{RawData * 503.975}{4096} -273$$"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<div class=\"alert bg-primary\" style=\"text-align:center;\"><font size=\"6\"><b>Taksun Simple Web Server </b></font></div>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# web server sample code for backend\n",
    "## Import linrary"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [],
   "source": [
    "from http.server import SimpleHTTPRequestHandler, HTTPServer\n",
    "from urllib.parse import urlparse, parse_qs\n",
    "import threading\n",
    "import json\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Read data from XADC driver in python"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [],
   "source": [
    "def read_xadc_temperature():\n",
    "    try:\n",
    "        with open(\"/sys/bus/iio/devices/iio:device0/in_temp0_raw\", \"r\") as raw_file, \\\n",
    "             open(\"/sys/bus/iio/devices/iio:device0/in_voltage0_vccint_scale\", \"r\") as scale_file,\\\n",
    "             open(\"/sys/bus/iio/devices/iio:device0/in_voltage0_vccint_raw\", \"r\") as vcore_file:\n",
    "            raw = int(raw_file.read().strip())\n",
    "            scale = float(scale_file.read().strip())\n",
    "            core = int(vcore_file.read().strip()) \n",
    "            temp = (raw *503.975/4096) -273\n",
    "            vcore = scale * core;\n",
    "            return [temp,vcore]\n",
    "    except Exception as e:\n",
    "        print(f\"Error reading XADC temperature: {e}\")\n",
    "        return None"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Override HTTP Handler method"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [],
   "source": [
    "class MyHandler(SimpleHTTPRequestHandler):\n",
    "    def do_GET(self):\n",
    "        if self.path == '/posts/1':\n",
    "            posts = {\n",
    "                1: {\n",
    "                    \"id\": 1,\n",
    "                    \"title\": \"temp\",\n",
    "                    \"val\": read_xadc_temperature()\n",
    "                    }\n",
    "                    }\n",
    "            self.send_response(200)  # OK\n",
    "            self.send_header('Content-type', 'application/json')\n",
    "            self.end_headers()\n",
    "            response = json.dumps(posts[1]).encode('utf-8')\n",
    "            self.wfile.write(response)\n",
    "\n",
    "        else:\n",
    "            super().do_GET()\n",
    "\n",
    "    def log_message(self, format, *args):\n",
    "        pass\n",
    "\n",
    "    def log_request(self, format, *args):\n",
    "        pass"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Function for running server"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "def run_server():\n",
    "    PORT = 8000\n",
    "    server_address = ('', PORT)\n",
    "    httpd = HTTPServer(server_address, MyHandler)\n",
    "    print(f\"Serving on port {PORT}...\")\n",
    "    httpd.serve_forever()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Run server function in theread"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Serving on port 8000...\n"
     ]
    },
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "----------------------------------------\n",
      "Exception happened during processing of request from ('192.168.1.100', 59886)\n",
      "Traceback (most recent call last):\n",
      "  File \"/usr/lib/python3.6/socketserver.py\", line 317, in _handle_request_noblock\n",
      "    self.process_request(request, client_address)\n",
      "  File \"/usr/lib/python3.6/socketserver.py\", line 348, in process_request\n",
      "    self.finish_request(request, client_address)\n",
      "  File \"/usr/lib/python3.6/socketserver.py\", line 361, in finish_request\n",
      "    self.RequestHandlerClass(request, client_address, self)\n",
      "  File \"/usr/lib/python3.6/socketserver.py\", line 696, in __init__\n",
      "    self.handle()\n",
      "  File \"/usr/lib/python3.6/http/server.py\", line 418, in handle\n",
      "    self.handle_one_request()\n",
      "  File \"/usr/lib/python3.6/http/server.py\", line 406, in handle_one_request\n",
      "    method()\n",
      "  File \"<ipython-input-8-196754ec26f8>\", line 18, in do_GET\n",
      "    super().do_GET()\n",
      "  File \"/usr/lib/python3.6/http/server.py\", line 639, in do_GET\n",
      "    self.copyfile(f, self.wfile)\n",
      "  File \"/usr/lib/python3.6/http/server.py\", line 800, in copyfile\n",
      "    shutil.copyfileobj(source, outputfile)\n",
      "  File \"/usr/lib/python3.6/shutil.py\", line 82, in copyfileobj\n",
      "    fdst.write(buf)\n",
      "  File \"/usr/lib/python3.6/socketserver.py\", line 775, in write\n",
      "    self._sock.sendall(b)\n",
      "BrokenPipeError: [Errno 32] Broken pipe\n",
      "----------------------------------------\n"
     ]
    }
   ],
   "source": [
    "server_thread = threading.Thread(target=run_server)\n",
    "server_thread.daemon = True  \n",
    "server_thread.start()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
