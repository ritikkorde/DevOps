# Jenkins
- CI & CD -Continuous integrtion / continuous deliverY and continous deployment
- what is ci & cd?
- 1) methodology 2) automated
     3)ci= Continuous build and continuous test
   jenkins is the  heart of software development life cycle
CI/  integration tools= jenkins,Bamboo(altasian), tranis CI,Build bot
-jenkin is an open source,project written in JAVA that run windows ,MacOS,and other unix-like Operating system
-it is free
-strong community support
-lost off plugins are available
-worked on port no.8080
-jenkins automate the entire  SDLC
-jenkins was originally developed by sun microsystem in 2004 under the hudson=jenkins/hudson(paid)
-whenever developers write code ,we integrate all that code of all developers at that point of time and we build ,test and delever/deploy to the client . This process is called CI/CD.
-because of CI nows bugs will be reported fast and get rectified foot so the entire software development happen fast.
<h2> Developers---➡️ Github ---➡️JENKINS ---➡️Build tool(Maven)----➡️Test tool (Selenium)
</h2>
  # Plugins = plug and play (those tools communicate each other)
  # artifact = Archive(store those code ready for final deployment)
  -1)Once developer puts code in github ,jenkins pull that code and send to maven fr build
  -2)Once build is done ,jenkins pull that code and send to Selenium for testing.
  -3)Once testing is done ,then jenkins will pull that code and send to artifactory(archiving purpose) as per requirement and so on.
  # advantages
  -it has lots of plugins available
  -you can write your own plugins
  -you can use community plugins
  -Jenkins is not just tool it is a framework i.e you can do whatever you want all you need is plugins
  -we can attach slaves (nodes)to jenkins master .it instruct other slaves to do jobs (work distribute to slaves)
  # BUILD
  compile---➡️Code review---➡️unit testing--➡️integration testing--➡️packaging(WAR,JAR)
