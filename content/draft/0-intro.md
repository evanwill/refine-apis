---
title: Intro
#nav: true
---

# Web APIs

Server-side Web Application Program Interfaces (APIs) are defined methods designed to make interaction with a server easier--think of them as recipes or contracts, where if you provide the expected input you will receive an expected output.
Web APIs provide an abstract way to interact with a server from the outside using a web protocol (http) to request or submit data.

{% capture plugs %}
Think about the outlets in your house.
Any device with the standard plug can be connected to the socket and receives the standardized amount of power. 
You do not need to know anything about the power generation or electrical grid that delivers it to your house (other than paying the bill). 
Likewise, the utility company doesn't need to know what you are plugging in, it just delivers the expected voltage.
This makes the interaction considerably simpler--you do not need to rig up custom wiring and voltage regulators for every device.
{% endcapture %}
{% include card.md text=plugs title="For Example..." img="rawpixel-1061399-unsplash.jpg" alt="power strip and plugs" %}

Many cultural institutions provide APIs allowing users to access information about their collections via simple HTTP requests. 
These sources enable new queries and aggregations of text that were previously impossible, cutting across boundaries of repositories and collections to support large scale analysis of both content and metadata.

This workshop uses the term *server-side web APIs* to refer to services exposed on the web via a well documented set of HTTP requests.
However, API is a generic term that is used in many different programming contexts, generally "a set of clearly defined methods of communication among various components" ([API, Wikipedia](https://en.wikipedia.org/wiki/Application_programming_interface)).

