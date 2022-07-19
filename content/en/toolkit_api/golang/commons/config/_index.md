---
type: docs
title: "Config"
linkTitle: "Config"
no_list: true
gitUrl: "https://github.com/pip-services3-go/pip-services3-commons-go"
description: >
    A package containing  a set of classes and interfaces that allows you to add configurations to components.
---
---

<div class="module-body"> 


### Description
The config package contains a set of classes and interfaces that allows you to add configurations to components. These configurations can contain different sets of configuration paramters, which can be used to define things such as access control credentials.     


<br>

### Interfaces


#### [IConfigurable](iconfigurable)
An interface to set configuration parameters to an object. 
It can be added to any existing class by implementing a single **Configure()** method.
If you need to emphasise the fact that **Configure()** method can be called multiple times
to change object configuration in runtime, use [IReconfigurable](ireconfigurable) interface instead.

#### [IReconfigurable](ireconfigurable)
An interface to set configuration parameters to an object.  
It is similar to [IConfigurable](iconfigurable) interface, but emphasises the fact
that **Configure()** method can be called more than once to change object configuration
in runtime.

<br>

### Types

#### [ConfigParams](config_params)
Contains a key-value map with configuration parameters. 
All values stored as strings and can be serialized as JSON or string forms.
When retrieved the values can be automatically converted on read using GetAsXXX methods.

#### [NameResolver](name_resolver)
A helper class that allows to extract component name from configuration parameters.
The name can be defined in "id", "name" parameters or inside a component descriptor.

#### [OptionsResolver](options_resolver)
A helper class to parameters from "options" configuration section.

</div>