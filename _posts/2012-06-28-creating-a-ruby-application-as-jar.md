---
layout: post
title: "Creating a Ruby Application as jar"
description: ""
category: 
tags: [ruby,jruby,java,packaging]
---
{% include JB/setup %}

Recently i am woking on a project,where i need to deploy the ruby code on a server and it was unclear till today
that even ruby can be exported as jar which is standard in java.After googling for a while i came across a tool
which will give me a jar by bundling the ruby files(in case of jruby we can compile and make it as .class files).
I have intension to run it with jruby so it works for me

Rawr is the simple awesome tool which does that, download the gem form [here](https://github.com/rawr/rawr)
can also read about it [here](http://rawr.rubyforge.org/) The commands given in the link should create the 
jar which we need.It also expects a ruby file when we run <code>java -jar path_to_jar</code> which is by default named 
as main,you can edit it in the <code>build_configuration.rb file</code> but i made sure that the ruby file i created
and the one in config file is the same.If all these are met then when you run the jar the ruby code executes.

But as i was deploying it on a server, i had no interest in exposing the source code(which will happen if i keep the
original rb file intact,as i am using jruby to run.I simply compiled the .rb files to .class files using following command

<code> jrubyc filename.rb
       jruby filename.class
</code>

Now the source is not exposed and the whole execution works with no problem on a server.