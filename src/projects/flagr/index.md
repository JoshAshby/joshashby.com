+++
title: "flagr"
template: "project"
+++

### What is it?

fla.gr is a personal site and project that eventually aims to be sort of my
replacement for the popular bookmarking service delicious. I have never really
liked the interface for delicious and recently have noticed it getting worse,
so I decided to build my own for personal use. Around July of 2012 I began work
on the first version of fla.gr. It wasn't much and was some of the ugliest code
I've ever written, but it worked as a proof of concept. Since then I've
rewritten both the core and the interface side of fla.gr a multitude of times
to use various different libraries or methods of handling the data.

### Where is it at right now?

Well right now it's in the process of having both it's data layer rewritten,
and it's templating language changed from the Python Cheetah languages to
Mustache templates. The data layer is moving from CouchCB to RethinkDB, and the
Redis side of things has had a face lift also.

### What does it use?

fla.gr runs on a small stack consisting of RethinkDB, Redis, Nginx, and Seshat.  
  
Seshat is a small web framework that I wrote just a month before starting
fla.gr, and makes use of gevent to act as a FastCGI server. It handles all of
the routing and handling sessions, allowing the actual fla.gr code to be a
little more higher level and with better abstraction.  
  
Redis is used primarily for sessions. All session data is stored in Redis
through an ORM wrapper I wrote, making sessions fast and easy to access. All
user data, "flags," and other pieces of data are all currently stored in
CouchDB because they doesn't need to be access quite as fast, however I'm in
the process of moving this layer over to RethinkDB, to allow for some more
dynamic interactions with the data.  

