---
layout: post
title: "Debugging Clojure with with-redefs"
description: ""
category: 
tags: [clojure debugging with-redefs]
---
{% include JB/setup %}

<p>
with-redefs is my new favorite Clojure debugging tool. with-redefs is a macro that allows you to temporarily
redefine any method with custom code. <a href="http://clojuredocs.org/clojure_core/clojure.core/with-redefs" target="_blank">
See the docs</a>. 
</p>
<p>
The obvious use case for this macro is unit tests. with-redefs is a frictionless way to mock out dependancies on external components.
See how they mock out http/post to return a constant response.
</p>

<script src="https://gist.github.com/mattmiller/5279712.js"> </script>

<p>
with-redefs is also invalueble for debugging. For example: I recently had trouble issueing map 
<a href="#" target="_blank">riak reduce jobs</a> from Clojure using the 
<a href="#" target="_blank">Welle client</a>. I am pretty new Riak and Welle so it was hard to tell
if the issues were caused by my improper use of the API.    
</p>

<script src="https://gist.github.com/mattmiller/5279871.js"> </script>

<p>
It would be great if I could see what is being passed to .mapReduce. with-redefs I can.
</p>

<script src="https://gist.github.com/mattmiller/5279990.js"> </script>

<p>
Now I can get a print out of what is being passed into .mapReduce before an exception occurs. While debugging I will modify my with-redef to print out the
args passed into methods farther and farther up the stack until I see something suspicious.
</p>