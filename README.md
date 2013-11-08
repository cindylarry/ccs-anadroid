# Outdated!! Please refer to the pushdownoo project!
-----


# Anadroid v2 compile & install 	


## Top level project folder:

- apktool.tar.gz  		: extract out the dex and resources files
- jdex2sex.tar.gz 		: disassembler to s-expresssion formed smali
- PlayPushDownOO  		: analytic engine + web interface + c/s communication
- play-2.0.4.tar.gz		: the binary image from http://www.playframework.com/documentation/2.0.4/Home
- test-apks	 			: some old test results produced by the analytic engine with only state graphs based on old android-knowledge
- README	 			: the file


## Anadroid is implemented in Scala, deployed as a web service using Scala Play Framework
accessible at

**pegasus.cs.utah.edu:8080 (this port will be open after May 9th 2013)**

or

**pegasus.cs.utah.edu:9090**

** The old analyzer is accessible via *pegasus.cs.utah.edu:8080/anadroid*, but it will be unavailable after May 9th, 2013 because the analyzer in that port will be upgraded to the new analytic engine to be tested by APAC test team. ** 

** The tentative link for old analyzer after May 9th, will be pegasus.cs.utah.edu:8088/anadroid. If it is not up, please send an email to liangsy@cs.utah.edu (in case I forgot) **


Google Chrome is recommended, with javascript enabled.
Details are on the web page.


### simple apk to test:

jpgnetnoloop.apk (from Keity and tomdroid), in PlayPushDownOO

other tested apks are in test-apks.

Contact liangsy@cs.utah.edu or my adviser might@cs.utah.edu for any questions.

 

## If you want to deploy yourself (not recommended), here are the instructions:

### ENVIRONMENT

1. Install Scala compiler 2.9.1
2. JDK 1.6 or later
3. Play Framework 2.0.4: http://www.playframework.com/documentation/2.0.4/Home
4. Graphviz
5. You will need eclipse to compile and run with play:
   Eclipse IDE for Java Developers
   Version: Helios Service Release 2

### How to compile and run:

First make sure you get the right version of Scala and Play framework.

Then, notice that the project folder will contain the following sub-folders:

- apktool 
- jdex2sex
- PlayPushDownOO (the analytic engine + web service)
- play-2.0.4

 `cd PlayPushDownOO`
 
 `../play-2.0.4/play`

   `compile`  # this is for compiling the PlayPushDownOO
   
   `run`	  # run the web service, default is localhost:9000
   
   `clean`     


** If compilation failed, you probably have to fix the library path issues. **
The  best way to do is to build a new play project and copy related files from PlayPushDownOO to the new play project.

and so do the following:

(1) In the top project folder, ./play-2.0.4/play

(2) command: play new yourNewNAME

(3) command: exit

(4) command: cd yourNewName

(5) ../play-2.0.4/play

(6) eclipsify

Move on to the next:  


+ Import PlayPushDownOO into eclipse if you want to conviniently inspect code, fixing library path issues and run clocally:

  - Open Eclipse:
  - Select File -> Import… -> Existing projects into Workspace
  - Pick PlayPushDownOO folder and click Finish.
    You should see the project files appear in the project explorer.

    Now let's resolve the compilation issues, note that 

  - Right click on the project, select Properties then Java Build Path
    In the Libraries tab, click Add Class Folder…
    Check target/scala-2.9.1/classes and target/scala-2.9.1/classes_managed
    Back in Java Build Path click Add external JARs…
    Select play\repository\local\org.scala-lang\scala-library\2.9.1\jars\scala-library.jar

    Fix some other libary paths in the same way. scala-compilr.src.jar

  

+ Copy the following folders to yourNewNAME from PlayPushDownOO:

   a. the entire folder app
   b. android-knowledge
   c. conf
   d. gethandlers.py, getIR.py, GetManifestInfo.py
   e. folder JVMClassReport
   f. the lib folder
   g. in PlayPushDownOO/project/build.scala to the correspondent path to yourNewNAME
   h. the public folder

+ goto yourNewNAME (which should be located in the top project folder).
and ../play-2.0.4/play to recompile



contact liangsy@cs.utah.edu for any questions.

