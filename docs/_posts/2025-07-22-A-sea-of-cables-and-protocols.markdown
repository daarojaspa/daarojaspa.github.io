---
title: "A sea of cables and protocols"
category: Software
--- 

A message from your friend: "Have you already uploaded the photo?" — a simple thing that enmascarates a complex and humongous network of cables and protocols that allows you two to communicate. Let's dive a little deeper into the internet.

First, you and your friend exchanged keys when you two added each other in (message app). Now, when she pressed send, the message she wrote was encrypted using the key you gave her — your public key. When the message arrives at your phone, before you even open it, it is decrypted using the key you did not share — your private key.

This protocol of having 2 keys, one private and one public — to share the public so others encrypt the messages they send you, and to decrypt with your private key — is called SSH. Now, this only accounts for the security part.

## Bits and Bytes

A bit is an interrupter that can be either on or off. In electronics, this normally relates with having a low voltage or current (represented by a 0) or a high voltage or current (represented by a 1). A bit is either a 0 or a 1.

If you group 8 bits, you have a byte. And with a byte, you can represent not 8 numbers but 256 numbers... how?

### Binary System

Imagine you have powers of 2 arranged from 2^0 to 2^7, and under this array, you have an interrupter that decides if the power of 2 over it is summed to the grand total or not. That is a binary system. All 8 bits on and you have 255.

Then you can add other codification systems on top of this one to use bytes to represent characters, like UTF-8 or ASCII.

So, your friend's message is converted to a series of bytes that are sent via waves to the Wi-Fi router at your friend's house, or to one of the cell phone antennas her cell phone is connected to (more than one at the same time). Then these devices convert it to an electrical signal that is sent via cable to an Internet Service Provider that is the company that conects you to the rest of the world. in colombia (Movistar,claro)

## IP Addressing and DNS

Just as your house has an address, your internet connection does too. All internet connections have an address. For this addressing, there are 2 protocols — IPv4 and IPv6. The first one uses 4 bytes to represent addresses. I'm sure you are used to seeing numbers like 127.0.0.1 (this is set as localhost).

Nowadays, IPv4 is used to represent some form of local network, and it's being used at the same time as IPv6, which has 8 bytes to represent addresses. IPv6 uses the hexadecimal system to represent them, so they look like AAAB\:FFF::1234, where :: represents a space where all numbers inside are 0.

Now, remembering all these numbers is hard. Imagine — wouldn't it be so much simpler to say to the Uber driver, "Take me to the house of Fulanito de Tal," and he immediately knew where to go? Well, the Uber driver is your browser, and there is an actual translator that allows this to happen. They are called Domain Name Servers. These servers translate the name of the place you want to go — e.g., minijuegos.com — to the IP address of the server in which minijuegos.com is hosted. This is how you and facebook can comunicate via letters using as delivery system something call TCP protocol.... wait you did not know you and facebook sended each other letters? well kind of, keep readding.
## Server-Client Model and HTTP Methods and Errors

You log in to your favorite social network—it doesn’t matter which one, what I’m about to explain is the same for all web pages.  
You pick a photo, fill out the description, and tag your friends’ accounts in it. Then, when you press *upload photo*, something amazing happens. Your device (the client) writes a letter to the social network’s backend (the server).  

What does the letter contain?  

It contains all the information you just filled out, plus more, in an already established format called a **POST request**.  
The server receives and processes all the information in the letter, then responds to your device with a **200 status code**, which means everything went fine and your post was created.  

These established formats for the letters the client and server send to each other are called **HTTP methods**. Besides POST, there are others such as **GET, PATCH, and DELETE**, each one with a specific purpose.  

The way the backend answers is defined by **HTTP status codes**. There are five main types:  

- **2xx** → success  
- **3xx** → redirection  
- **4xx** → client error  
- **5xx** → server error  

In short, HTTP sets the rules for how the structure or format of each “letter” should look. These letters are then encapsulated in a package that **TCP** (like FedEx in the real world) delivers to each endpoint.  

---

## Programming Languages

Now, imagine setting up all these protocols in pure binary. For you and me, writing and understanding how we are manipulating machines this way would be hell. Sharing that knowledge with others so they could help would be extremely difficult.  

This is why different **programming languages** exist. Each one was created to solve the need of giving a set of instructions to a particular hardware architecture (phones, old and new PCs, routers, antennas—if it has a CPU, it counts) in a way that allows people to express complex ideas and share them with others, without needing to rewrite everything whenever hardware changed.  

Because silver bullets don’t exist, programming evolved in layers: first came **assembly**, built over binary, then **C and C++** over assembly. From there, more languages were built, branching off when someone wanted to prove a new idea or paradigm (like object-oriented programming, functional programming, inheritance, etc.—don’t worry about the details for now).  

The goal has always been to make speaking to the machine as close as possible to speaking to a human—while staying precise.  

But all programming languages share some things in common:  

- **Rules for writing (syntax)**  
- **Rules for meaning (semantics)**  
- **Ways to store information (variables and data types)**  
- **Flow control structures (conditionals and loops)**  
- **Procedures for reuse (functions or methods)**  
- **Mechanisms for input and output**  
- **Levels of abstraction (reducing complex systems into simpler blocks)**  

Now i hope you have a great end of the day, with some  friends to tell them about what you have read here, and while you do it ¿ Does the language you guys are speaking have things in cummon whith programming languages?
