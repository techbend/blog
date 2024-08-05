---
title: "Creating Transmutate: A Tool for Easier gRPC and Proto Files in Python"
seoDescription: "Transmutate: a Python library for automatic Proto file generation, data validation, and streamlined gRPC service creation from dataclasses"
datePublished: Mon Aug 05 2024 17:53:46 GMT+0000 (Coordinated Universal Time)
cuid: clzhait7z000o08kvd0pt11l2
slug: creating-transmutate-a-tool-for-easier-grpc-and-proto-files-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722880346579/61086857-bbe3-4627-8cd8-105c972361b6.webp
tags: github, opensource, python3, grpc

---

### Introduction

Recently, I worked on a project that needed many **gRPC functions**. If you've used gRPC, you know it helps different software programs talk to each other efficiently. However, making Proto files for every Python dataclass was taking a lot of time and effort.

I needed to find a way to do this faster, so I built a Python library called **Transmutate**. This library helps create Proto files automatically from Python dataclasses. It also helps check if data is correct and makes working with gRPC easier.

### The Problem with Proto Files

When using gRPC, we have to create Proto files. These files describe the data that the programs send to each other. Here are some problems I faced:

1. **Writing Proto Files**: Manually writing Proto files for each dataclass was boring and easy to make mistakes.
    
2. **Keeping Things in Sync**: When I changed the Python dataclass, I had to remember to update the Proto file, which sometimes I forgot to do.
    
3. **Data Validation**: I needed to make sure that the data followed certain rules, like checking if an email address was correct.
    

### How Transmutate Solves These Problems

**Transmutate** automates a lot of these tasks. Here’s how it helps:

#### 1\. Automatic Proto Generation

With Transmutate, you don't have to write Proto files manually. The library generates them for you from your Python dataclasses.

Here's a simple example:

```bash
from transmutate.base_model import BaseModel
from typing import List

class Person(BaseModel):
    name: str
    age: int
    email: str
    phone_numbers: List[str]

# Generate Proto message
proto_definition = Person().to_proto()
print(proto_definition)
```

This will automatically create a Proto message like this:

```bash
message Person {
  string name = 1;
  int32 age = 2;
  string email = 3;
  repeated string phone_numbers = 4;
}
```

#### 2\. Built-In Field Validation

Transmutate allows you to add checks to make sure the data is valid. You can write functions that check each field. Here's an example:

```bash
class Person(BaseModel):
    name: str
    age: int
    email: str

    def validation_age(self):
        if not (0 <= self.age <= 120):
            raise ValueError("Age must be between 0 and 120.")

    def validation_email(self):
        if "@" not in self.email:
            raise ValueError("Invalid email address.")
```

In this example, the library will automatically run these checks when creating a `Person` object.

#### 3\. Easy gRPC Service Creation

Transmutate also helps create gRPC service definitions quickly. Here’s how you can define a service:

```bash
from transmutate import Service, RpcType

class TestService(Service):
    name = "TestService"
    types = [RpcType.UNARY]
    request_dataclass = Person
    response_dataclass = AnotherMessage

service_definition = TestService().generate_service_definition()
print(service_definition)
```

This generates a gRPC service definition without you having to write it manually.

### Why Use Transmutate?

Here are some reasons why **Transmutate** is useful:

* **Save Time**: You spend less time writing Proto files and more time on real work.
    
* **Reduce Errors**: Automatic generation of Proto files reduces mistakes.
    
* **Simple to Use**: It works with existing Python code and is easy to add to your projects.
    
* **Automatic Validation**: Built-in checks ensure your data is correct.
    

Creating **Transmutate** helped me handle gRPC functions more easily. Instead of spending hours writing and managing Proto files, I can now focus on building features and solving problems.

You can find **Transmutate** on [GitHub](https://github.com/tavallaie/transmutate). Feel free to check it out, and if you find it helpful, please [consid](https://github.com/tavallaie/transmutate)er starring the repository or contributing to the project. Your feedback is welcome, and I hope this library makes your work with gRPC easier, just as it did for me.