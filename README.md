Python Function NodeRED Node
=============================

Node-RED is a wonderful tool, but Javascript can be a rather painful language to write. 
Being able to write functions with the language of your choice, and not just Javascript,
might just be the last piece of functionality missing to make Node-RED perfect. Or not.
In any case, this quick hacked node will let you write functions using Python instead of Javascript!
How cool is that? Too cool to be used in production, that is for sure. 

I repeat, don't use this in production. And when you do (cause you will), please tell your manager
I already told you so. 

Install
-------

Requires Python (both 2.x and 3.x are supported) installed in the system. 

`npm install -g node-red-contrib-python-function`

Usage
-----

Just like the plain-old function node, but writting Python instead of Javascript.
The msg is a dictionary, (almost) all the Node-RED helper functions are avaiable, and its behaviour
 is expected to be exactly the same (at some point in the future at least).

Caveats
-------

- Although it will accept virtually any msg you give it, any non-JSON data type will be silently dropped from the msg permanently.
- Somethings is wrong with the current implementation of the IPC, that makes it blow up when there are +2 messages waiting to be processed
- Python is by default a synchronous runtime. The function is run in a dedicated child process,
  therefore it won't block the NodeJS main process, but in any case only 1 message is processed at a time. That is, of course, unless you
  use any of the concurrency features available in Python, like multithreading, multiprocessing, Tornado, Twisted...
- No sandboxing has been attempted whatsoever. After all, this is just to have some fun, not to be used in production, remember...?
