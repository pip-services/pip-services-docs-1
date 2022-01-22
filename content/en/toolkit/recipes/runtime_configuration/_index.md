---
type: docs
no_list: true
title: "Runtime configuration"
linkTitle: "Runtime configuration"
weight: 10
description: >-
     How to set up and change your configurations at runtime.
---

{{< tabselector "Node" ".NET" "Golang" "Dart" "Python" "Java" >}}

### Key takeaways

### Introduction

In this tutorial, you will learn how to configure at runtime an application based on Pip.Services components. For this, we will use the example already developed in the “Three tier architecture” tutorial and expand it to consider two different databases. Then, we will see how to select one of these databases at runtime.

### Basic concepts

Two of the main concepts behind Pip.Services are inversion of control and the locator pattern, which are used to manage object creation and object binding.

Inversion of control is applied through the use of factories to create objects. The advantage here is that we can specify our class in a generic way, for example, by indicating that it is a persistence unit, but without having to specify connection parameters and other aspects.

The locator pattern is implemented via the use of a YAML configuration file. This feature allows us to make configuration choices at runtime. For example, we can change connection parameters, such as IP addresses or database names, and we can provide more than one option for a type of component.

The sections and example that follow explain how this is done in detail.

### Brief description of the example

In this tutorial, we will expand on the example presented in the tutorial titled “Three-tier architecture” and available through this website. 

That example comprised an application that selects a random name from a database and shows a message saying “Hello {random name}!” on a browser. The database used was MySQL.

Our code expansion will consist of including a second database (PostgreSQL) containing a similar table and adding the capacity to choose between the two at runtime via environmental variables.

### Changes to our example

In this example, we consider two databases, one MySQL and another PostgreSQL and we select one of them at runtime for the application.

For this, we create an interface that defines a common naming and permits to shift between both databases.

We also create a class per database. 

#### Common interface

One of the principles behind Pip.Services is symmetric implementation. This means that different libraries use similar method names and signatures. As a result, we can create an interface that defines the CRUD methods implemented by one or more databases. This will allow us to have a common central point from which we can define the operations that we need.

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
  {{< include "./__code1_python.md" >}}
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

#### Controller

Our controller is similar to the one defined in the “Three tier architecture” tutorial. The only difference is that we define the _persistence variable as of type IMyDataPersistence. This will allow us to refer to our database independently of the specific cases. 

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
  {{< include "./__code2_python.md" >}}
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

#### MySQL

This class adds the common interface as a parent. As the getOneRandom() method is protected, we override it and add the composeFilter() method to create a filter that considers the specifics of MySQL.

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
  {{< include "./__code3_python.md" >}}
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

#### PostgreSQL

As we are working with two databases, we need to create a class similar to the one we created for MySQL. In this case, it inherits from IdentifiablePostgrePersistence and our common interface IMyDataPersistence. 

Similar to our MySQL class, we also override the getOneRandom() method and add a composeFilter() method to adapt our filter to the specifics of PostgreSQL.

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
  {{< include "./__code4_python.md" >}}
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

#### Configuration file

In order to be able to select between both databases, we need to include both configurations in our config file. In addition, we need to include a conditional IF statement that will check on the environment variable and select the correct database.

Our file will look something like this:

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
  {{< include "./__code5_python.md" >}}
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

### Final code

Now that we have completed all the necessary additions and modifications to our program, we can join all the parts and get the final application. Its code is:

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
  {{< include "./__code6_python.md" >}}
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

### Running our app

The fact that we can choose between two different databases brings an extra step to our process, which is, selecting the operating database.

This is done by assigning a value to the environmental variable representing the selected database. We can do this by setting our variable from Windows or through code. We can then deselect this database by assigning an empty string or by not assigning a value to its environment variable. The following example shows how to select our MySQL database and run the application. 

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
 Not available  
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

{{< tabsection >}}
  {{< include "./__code7_python.md" >}}
{{< /tabsection >}}

{{< tabsection >}}
  Not available  
{{< /tabsection >}}

### Results

If we selected the MySQL database, we will see the following message:

![figure 1](./figure1.png)

Alternatively, if we selected the PostgreSQL database, we will see the following message:

![figure 2](./figure2.png)

### Wrapping up

In this tutorial, we have examined how to create a web application that allows us to select between two different databases at runtime. 
Although this example is simple, it can be extended to consider many other scenarios, as the principles and concepts employed in its construction are the same.

