---
layout: post
title: Installing OpenGrok on Ubuntu (Java Target Version Error)
categories:
- articles
tags:
- opengrok
- java
- sysadmin
---

Earlier today, I installed Solr on top of OpenJDK 1.6, running Tomcat 6. That went just fine, but I ran into trouble later, when I tried to install [OpenGrok][1], which [requires JDK 1.7][2]. When I ran `ant`, I got this error:

    -do-compile:
        [javac] Compiling 245 source files to /usr/local/src/OpenGrok/build/classes
        [javac] javac: invalid target release: 1.7

This was strange, since at the suggestion of [this StackOverflow answer][3], I put this line *after my opening \<project\> tag of build.xml*

    <echo message="Using Java version ${ant.java.version}."/>

And the result was that I was already running 1.7. After a lot of trial and error, I got it to work by running `update-alternatives` to officially set the java version to 1.7.

    sudo update-alternatives --set java /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java

Hopefully this can help out some other Java sysadmin neophytes.


[1]: http://opengrok.github.io/OpenGrok/
[2]: https://github.com/OpenGrok/OpenGrok/wiki/How-to-build-OpenGrok-from-source
[3]: http://stackoverflow.com/questions/4956209/problem-in-ant-build-invalid-target-release
