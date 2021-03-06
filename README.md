# Examples for Distributed Computing

[<img alt="Travis CI Build Status" src="https://img.shields.io/travis/thomasWeise/distributedComputingExamples/master.svg" height="20"/>](https://travis-ci.org/thomasWeise/distributedComputingExamples/)
[<img alt="Shippable Build Status" src="https://img.shields.io/shippable/56d905429d043da07b368422.svg" height="20"/>](https://app.shippable.com/projects/56d905429d043da07b368422)

## 1. Introduction and Contents

### 1.1. Introduction

Distributed systems surround us everywhere today. Their most prominent example is the internet hosting the world wide web. The computing environment in enterprise computing systems is often distributed too, interconnecting different services from human resources, financial departments, to asset management systems. Many applications are even hosted in the cloud. Finally, large-scale engineering and scientific computing today rely heavily on clusters in order to parallelize their workload. These topics are discussed in my distributed computing lecture. In this repository, you can find the practical examples I use in my course.

### 1.2. Contents

1. [Sockets](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/)
  1. in [C](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/c)
  2. in [Java](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/java)

2. [HTML, CSS, and JavaScript](http://github.com/thomasWeise/distributedComputingExamples/tree/master/html/)

3. [Java Servlets](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/)
  1. [deployable examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/examples)
  2. [HTTP Proxy Servlet](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/proxy)

4. [JavaServer Pages](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServerPages/)
  1. [deployable examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServerPages/examples)
  2. [stand-alone JSPs](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServerPages/standAloneJSPsWithJetty)

5. [Java RMI](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaRMI/)
  
6. [XML](http://github.com/thomasWeise/distributedComputingExamples/tree/master/xml/)
  1. [examples for XML documents and related standards](http://github.com/thomasWeise/distributedComputingExamples/tree/master/xml/xml)
  1. [examples for XML processing with Java](http://github.com/thomasWeise/distributedComputingExamples/tree/master/xml/java)
  
7. [Web Services](http://github.com/thomasWeise/distributedComputingExamples/tree/master/webServices/)
  
8. [JSON RPC](http://github.com/thomasWeise/distributedComputingExamples/tree/master/jsonRPC/)
  
9. [Message Passing Interface](http://github.com/thomasWeise/distributedComputingExamples/tree/master/mpi/)
  
10. [Hadoop](http://github.com/thomasWeise/distributedComputingExamples/tree/master/hadoop/)
  
Each of the above links leads you to a sub-directory containing a set of examples. Each sub-directory has an own `README.md` file with detailed descriptions. 

Since I also use the same code in my slides, there are some special comments such as `//(*@\serverBox{2)}@*)` for formatting in my codes ... you can safely ignore them ^_^

## 2. Concept of the Course

The concept of this course is that we want to understand how the web and distributed enterprise application environments work. We want to do that by starting to explore how to communicate over a network at the lowest level of abstraction (normally) available to programmers, the [socket API](https://en.wikipedia.org/wiki/Network_socket). From there, we work our way up step-by-step higher levels of abstraction, i.e., simpler and more powerful API stacking on top of each other (and ultimately grounded in sockets). This way, we will gain a solid understanding how distributed applications and the web work. We will be able to look at a website and immediately have a rough understanding of how it may work, down to the nuts and bolts. For each level of abstraction that we explore, we therefore always learn example technologies. 

### 2.1. The Basics: Sockets, TCP, UDP, Parallelism, and Mashalling

As said, we start at the very bottom: Communication in distributed systems today is usually either based on the [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol) or [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol). Both protocols are accessed via the [socket API](https://en.wikipedia.org/wiki/Network_socket), for which we provide [examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/) in both [C](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/c) and [Java](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/java). As part of these examples, we also show how text can be encoded in Java and how to construct servers which can process multiple requests in [parallel](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/java/src/MinHTTPServerThreadPool.java). Sockets are thus the very basis of distributed applications, the lowest level with which a programmer might have to work.

### 2.2. The Outside View of an Enterprise: Dynamic Websites

We now are able to understand the basic communication processes going on in virtually any current computer network and the internet. We will use this understand to investigate how an organization or enterprise can present itself to the outside world via a website. We want to understand the technologies necessary to construct a website that can dynamically interact with a user.

#### 2.2.1. HTML, CSS, JavaScript

The [world wide web](https://en.wikipedia.org/wiki/World_Wide_Web) is based on three pillars: [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol), [HTML](https://en.wikipedia.org/wiki/HTML)/[CSS](https://en.wikipedia.org/wiki/Cascading_Style_Sheets)/[Javascript](https://en.wikipedia.org/wiki/JavaScript), and [URLs](https://en.wikipedia.org/wiki/Uniform_Resource_Locator). HTTP, the Hyper Text Transfer Protocol, is a text-based protocol to query resources which is usually transmitted over TCP connections. Actually, we already provide  example implementations of both the [server](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/java/src/MinHTTPServer.java) ([web server](https://en.wikipedia.org/wiki/Web_server)) and [client](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/java/src/MinHTTPClient.java) ([web browser](https://en.wikipedia.org/wiki/Web_browser)) client side of the HTTP communication using [sockets](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/java) (and even a small [parallel web server](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/java/src/MinHTTPServerThreadPool.java). We then provide some rudimentary [examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/html/) for [HTML](http://github.com/thomasWeise/distributedComputingExamples/tree/master/html/example_pain/index.html), [CSS](http://github.com/thomasWeise/distributedComputingExamples/tree/master/html/example_css/index.html), and [JavaScript](http://github.com/thomasWeise/distributedComputingExamples/tree/master/html/example_javascript_calculator/index.html).

#### 2.2.2. Java Servlets: HTTP Protocol Server-Side Implementation

Implementing HTTP based on sockets is quite complex. Sockets allow us access TCP. What we would like to have is a similarly elegant API to access HTTP (the next higher level of abstraction). One such technology are [Java Servlets](https://en.wikipedia.org/wiki/Java_Servlet). Servlets are used to implement the server-side of a HTTP conversation. A servlet is a sub-class of a special Java class which implements handler methods for different HTTP interactions ("[HTTP methods](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods)"). These methods are called by a [servlet container](https://en.wikipedia.org/wiki/Web_container), the actual implementation of the server. We can therefore fully concentrate on the application logic and don't need to worry about the protocol interaction itself. We provide a wide range of examples for [Java Servlets](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/), both [deployable examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/examples) as well as a stand-alone [HTTP Proxy Servlet](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/proxy). So with Java Servlets, we can build server components that can dynamically interact with a HTTP client (such as a web browser). This means that we can dynamically generate contents of a web page when a browser requests them. However, building complete dynamic web sites as Java Servlets is again quite cumbersome, as servlets are Java classes while web pages are HTML, which we would then write in form of string constants to be written to the output of a Servlet.

#### 2.2.3. JavaServer Pages: Implement Dynamic Web Pages

The next higher level of abstraction are [JavaServer Pages](https://en.wikipedia.org/wiki/JavaServer_Pages) (JSPs), which allow us to write HTML pages (or other text formats) and include Java source code in it. The pages are then served again by a servlet container. Whenever a page is sent to a client, the included Java code is first executed on the server side (and may generate additional output). Upon closer inspection, we can find that JSPs are actually "special" servlets: When a JSP is accessed for the first time, the servlet container dynamically creates the source code of a corresponding Java Servlet. This servlet is compiled, loaded, and then executed to create the dynamic content of the page to be sent to the client. Everything which was "text" in JSP becomes a String inside the servlet which is written to the servlet's HTTP response. Everything which was "code" in the JSP is copied directly into the handler methods of the servlet. JSPs are a more natural way to dynamically generate text (HTML) output and serve it to a client. By now, we have a solid understanding how dynamic contents in the web can be generated, how a user can interact with a web application via web forms by using her browser, and how we can realize sessions.

### 2.3. The Inside View of an Enterprise: Distributed Application Environment

While these technologies allow us to build a dynamic "outside" view of a company, the way the company presents itself in the web, we now explore the "inside" view of the distributed enterprise computing environment. Here the goal is to build an environment in which applications from different departments (financial department, human resources, asset management, ...) can be connected with each other in a future-safe, extensible way.

#### 2.3.1. Remote Procedure Calls with Java RMI

The first step on this road to enterprise computing are [Remote Procedure Calls](https://en.wikipedia.org/wiki/Remote_procedure_call) (RPCs), which we explore on the example of [Java Remote Method Invocation](https://en.wikipedia.org/wiki/Java_remote_method_invocation) (RMI). Our [examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaRMI/) show how an object of one application hosted on computer can be accessed from another program running on a another computer. This brings us already close to realizing distributed applications interconnected on a network. However, Java RMI is still a Java-specific technology and its protocol is binary. We would like to implement our distributed applications in a platform-independent way, by using very clear, well-specified, and easy-to-understand protocols.

#### 2.3.2. XML as Data Interchange Format

Our pursuit of such a technology forces us to first take the de-tour of learning about the Extensible Markup Language ([XML](https://en.wikipedia.org/wiki/Xml). XML is a self-documenting format for storing complex data structures in text. It is similar to HTML, but without any pre-defined semantic or presentation. These can be specified for each application. We both look at [examples for XML documents and related standards](http://github.com/thomasWeise/distributedComputingExamples/tree/master/xml/xml) themselves as well as [examples for XML processing with Java](http://github.com/thomasWeise/distributedComputingExamples/tree/master/xml/java).

#### 2.3.3. Web Services

We then discuss [Web Services](https://en.wikipedia.org/wiki/Web_service). Web services are the basic foundation of many distributed enterprise computing systems and [service-oriented architectures](https://en.wikipedia.org/wiki/Service-oriented_architecture). They are invoked using the [XML](http://github.com/thomasWeise/distributedComputingExamples/tree/master/xml/)-based [SOAP](https://en.wikipedia.org/wiki/SOAP) protocol usually over [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol). Their interface and provided functionality is described via the Web Service Description Language ([WSDL](https://en.wikipedia.org/wiki/Web_Services_Description_Language)), another XML standard. Based on what we already know, we could now send XML data to a Java Servlet via HTTP-POST, parse this data with these Java XML processing technologies, use the same technologies to generate an output XML document, and send this one back as the response of the Java Servlet. Actually, we could even use JavaServer Pages for this purpose. However, there again is a simpler way: We can build services as simple Java objects and publish them to the [Apache Axis2/Java](http://axis.apache.org/axis2/java/core/) server. The server will make them accessible via SOAP and automatically generate WSDL descriptions. These can then be used to generate proxy objects for the client side using, e.g., [Maven](http://maven.apache.org/). We investigate this technology on [several examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/webServices/).

#### 2.3.4. JSON RPC

[JSON RPC](https://en.wikipedia.org/wiki/JSON-RPC) is another remote procedure call ([RPC](https://en.wikipedia.org/wiki/Remote_procedure_call)) approach (specified [here](http://json-rpc.org/)) where the exchanged data structures are encoded in the JavaScript Object Notation ([JSON](https://en.wikipedia.org/wiki/JSON)). The data is exchanged via either [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) or [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol). JSON RCPs are similar to web services, but designed to be more light-weighted. We again discuss several [examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/jsonRPC/).

### 2.4. Large-Scale Distributed Computations and Data Processing (as used in Data Mining and Engineering)

As last important use case for distributed computing, we consider how large-scale distributed computations can be realized. Such computations are needed in many [scenarios](http://www.hadoopilluminated.com/hadoop_illuminated/Hadoop_Use_Cases.html), ranging from simulations in engineering to data mining and processing in enterprises.

#### 2.4.1. Message Passing Interface: Processes that Communicate Frequently

We now focus on how the computing power of massive clusters can be utilized for large-scale scientific and engineering computations. Such large computations or simulations are often divided into several smaller sub-problems. These smaller problems are then solved *cooperatively* by multiple threads or processes in parallel. This often involves the exchange of messages at regular time intervals between processes working on closely related sub-problems. Obviously, Web Services, Java Servlets, or even just Java and the HTTP protocol, would be the wrong technologies for that: For large-scale computations, we want to get as efficient as possible with as little overhead as possible. This especially concerns communication, which is very expensive and the [limiting factor](https://en.wikipedia.org/wiki/Amdahl's_law) for the speedup we can achieve with distribution. We want to exchange primitive data types efficiently and we want to use communication paradigms not supported by HTTP/TCP, such as broadcasts, multicasts, and asynchronous communication. For this, an implementation of the Message Passing Interface ([MPI](https://en.wikipedia.org/wiki/Message_Passing_Interface)) would be the method of choice. We explore this technology based on [several examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/mpi/) in the C programming language.

#### 2.4.2. MapReduce with Hadoop: Large-Scale Data Processing

In a final step we discuss a technology which combines the ability to create large-scale distributed computations (from the MPI world) with the rich tool support of the Java ecosystem: [MapReduce](https://en.wikipedia.org/wiki/MapReduce) with [Apache](http://hadoop.apache.org/) [Hadoop](https://en.wikipedia.org/wiki/Apache_Hadoop). MPI is the technology of choice if communication is expensive and the bottleneck of our application, frequent communication is required between processes solving related sub-problems, the available hardware is homogenous, processes need to be organized in groups or topological structures to make efficient use of collective communication to achieve high performance, the size of data that needs to be transmitted is smaller in comparison to runtime of computations, and when we do not need to worry much about exchanging data with a heterogeneous distributed application environment. Hadoop, on the other hand, covers use cases where communication is not the bottleneck, because computation takes much longer than communication (think Machine Learning), when the environment is heterogeneous, processes do not need to be organized in a special way and the division of tasks into sub-problems can be done efficiently by just slicing the input data into equal-sized pieces, where sub-problems have batch job character, where data is unstructured (e.g., text) and potentially huge (eating away the advantages of MPI-style communication), or where data comes from and results must be pushed back to other applications in the environment, say to HTTP/Java Servlet/Web Service stacks. Our [Hadoop examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/hadoop/) focus on the [MapReduce](https://en.wikipedia.org/wiki/MapReduce) pattern (which is a tiny little bit similar to scatter/gather/reduce in MPI, just for the scenario described above).

### 2.5. Summary

All in all, this course will give you a rough understanding of the dominant technologies in different fields of distributed computing, from dynamic websites over company-internal distributed application systems, to distributed engineering and scientific computations. Each field is explored with hands-on examples and you get to test and play with several example technologies.


## 3. Software Requirements

For each example, I explicitly list the required software and discuss how it can be obtained and installed. Here I give an overview over these software components.

### 3.1. Java JDK

Most of the examples I provide are written in the Java programming language and can run under arbitrary systems, given that Java is installed. In order to compile them, you need a [Java JDK](https://en.wikipedia.org/wiki/Java_Development_Kit) installed. My examples require [Java 7](https://en.wikipedia.org/wiki/Java_version_history#Java_SE_7) or later.

Under Windows, you need to download and install Java from the [Oracle website](http://www.oracle.com/technetwork/java/javase/downloads/index.html).

Under Linux, you would do `sudo apt-get install openjdk-7-jdk` (where you can replace `7` with any later version, such as `8`, if you like)

### 3.2. Maven

Several of my Java examples are built with [Maven](https://en.wikipedia.org/wiki/Apache_Maven). All of these examples have a `pom.xml` file in their root folder. In order to build them, you thus need to install Maven.

Under Windows, you need to download and install Maven from the [Apache website](http://maven.apache.org/download.cgi).

Under Linux, you would do `sudo apt-get install maven`.

If you are using Eclipse (see below), you do not need to install Maven as it is already integrated into Eclipse.

### 3.3. Eclipse 

I recommend [Eclipse](http://www.eclipse.org) as developer environment for all the Java examples in this repository. Each Java example actually comes already with an Eclipse `.project` file and with Eclipse `.settings`. Eclipse integrates both Maven and git. This means you can clone this repository from within Eclipse and directly import the Jave projects during this process. If you then right-click the Maven projects and choosen `Maven` -> `Update Project...`, Eclipse will also download and use all required libraries and dependencies as specified by the Maven `pom.xml` for you.

You can download Eclipse from the [Eclipse website](http://www.eclipse.org). I recommend to use at least Eclipse Mars.1 for its excellent Maven and git support.

### 3.4. GlassFish Server

For running some of the [Java Servlets](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/) and [JavaServer Pages](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServerPages/) examples, you need to download the [GlassFish Server](http://javaee.github.io/glassfish) from the corresponding [download website](http://javaee.github.io/glassfish/download). I recommend using at least GlassFish 4.1.2.

### 3.5. Apache Axis2/Java

For running the [Web Service](http://github.com/thomasWeise/distributedComputingExamples/tree/master/webServices/) examples, you will need to download [Apache Axis2/Java](http://axis.apache.org/axis2/java/core/) from the corresponding [download page](http://axis.apache.org/axis2/java/core/download.html). I recommend using at least Axis2 1.7.3.

### 3.6. GCC

In order to compile the examples written in the C programming language (such as the `C`-based [sockets examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/sockets/c)), you will need a C compiler such as GCC. Under Linux, it should normally be already installed and can otherwise be installed via `sudo apt-get install gcc`. Under Windows, you will need to install [MinGW](http://mingw.org/), usually via the [web installer](https://sourceforge.net/projects/mingw/files/Installer/mingw-get-setup.exe/download).

### 3.7. Cross-Compiling for Windows under Linux with GCC

Several of the C examples come for Windows or Linux. GCC allows you to cross-compile, i.e., if you are using Linux, you can compile C programs for Windows. For this purpose, you would first install `sudo apt-get install gcc-mingw-w64-i686` and then can use the command `gcc-mingw-w64-i686` in the same way you would use `gcc` under MinGW.

### 3.8. MPICH

In order to build and compile our [examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/mpi/) for using the Message Passing Interface (MPI), we need an [MPI implementation](https://en.wikipedia.org/wiki/Message_Passing_Interface#Implementations). We choose [MPICH](https://en.wikipedia.org/wiki/MPICH).

Under Linux, you can install the required files via `sudo apt-get install mpich libmpich-dev`.

### 3.9. Hadoop (also `ssh` and `rsync`)

In order to test our [Hadoop examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/hadoop/), we now need to set up a single-node Hadoop cluster. We therefore follow the guide given at [http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/SingleCluster.html](http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/SingleCluster.html). We need to install pre-requisits such as `ssh` and `rsync`. In the [Hadoop example readme](http://github.com/thomasWeise/distributedComputingExamples/tree/master/hadoop/README.md), we provide the installation guide for Hadoop 2.7.2 Linux / Ubuntu. It boils down to downloading and installing Hadoop from one of the mirrors provided at [http://www.apache.org/dyn/closer.cgi/hadoop/common/](http://www.apache.org/dyn/closer.cgi/hadoop/common/), plus following the guidelines of the linked tutorial.

## 4. Licensing

This work has purely educational purposes. Besides everything mentioned below, for anything in this repository, I impose one additional licensing condition: The code must never be used for anything which might violate the laws of Germany, China, or the USA. This also holds for any other file or resource provided here.

The examples in this repository are licensed under the [GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007](http://github.com/thomasWeise/distributedComputingExamples/tree/master/LICENSE), with the following exceptions:

### 4.1. Exception: Stand-Alone JSPs/JavaServlets

Everything in the directories [/javaServerPages/standAloneJSPsWithJetty](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServerPages/standAloneJSPsWithJetty) and [/javaServlets/proxy](http://github.com/thomasWeise/distributedComputingExamples/tree/master/javaServlets/proxy) is licensed under the [Apache License v2.0](http://www.opensource.org/licenses/apache2.0.php) and are partially derived from project [embedded-jetty-jsp](https://github.com/jetty-project/embedded-jetty-jsp) with copyright (c) 1995-2013 Mort Bay Consulting Pty. Ltd.

### 4.2. Exception: Hadoop Examples

Some of the [Hadoop examples](http://github.com/thomasWeise/distributedComputingExamples/tree/master/hadoop/) take some inspiration from the [maven-hadoop-java-wordcount-template](https://github.com/H4ml3t/maven-hadoop-java-wordcount-template) by [H3ml3t](https://github.com/H4ml3t), for which no licensing information is provided. The examples, are entirely differently in several ways, for instance in the way we build fat jars. Anyway, this original project is nicely described in [this blog entry](https://nosqlnocry.wordpress.com/2015/03/13/hadoop-mapreduce-wordcount-example-in-java-introduction-to-hadoop-job/).

Furthermore, the our [Hadoop word](http://github.com/thomasWeise/distributedComputingExamples/tree/master/hadoop/wordCount) is based on the well-known [word counting example](http://wiki.apache.org/hadoop/WordCount) for Hadoop's map reduce functionality. It is based on the version by provided Luca Menichetti [meniluca@gmail.com](mailto:meniluca@gmail.com) under the GNU General Public License version 2.