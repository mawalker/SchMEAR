#SchMEAR is a Web Server Project creator for: _S_pring, _M_aven, _E_clipse, google _A_pp engine, and _R_.e.s.t.

This 'guide' is for your benefit only for now, is not complete, but might help you out a lot for now, I plan on improving this dramatically here soon. 

To use this project creator you will need these tools:

*   JDK 7 (OpenJDK appears to work fine)

*   Eclipse

*   Maven 3.1

I Am Working on an archetype for maven, which will allow you to make a easily usable project out of the box.

Until then... 

edit this command: (change 'com.mycompany.app' and 'my-app' to appropriate values)
```
mvn archetype:generate \
-DgroupId=com.mycompany.app \
-DartifactId=my-app \
-DarchetypeGroupId=com.google.appengine.archetypes \
-DarchetypeArtifactId=skeleton-archetype \
-DinteractiveMode=false
```

and paste it into your linux machine's terminal (the '\' make this all a single line command) and run it. You will now have a working starter project, but it will be lacking lots of features you'll need. 

However, the project created doesn't provide every dependency that you would want to use. Specifically Spring is not included at all. Therefore you can copy/paste the non-specific portions of the pom.xml included alongside this README.md to achieve a project that will have the appropriate configuration.

Things to change from provided pom file:
*   lines 9 and 10 will have to be changed to match your chosen values
*   line 12 The entire '<developers>' section will need to changed
*   line 370 will need to be changed to the package you keep your 'domain' objects (which means where you keep your POJO files, that will represent how your data is stored into noSQL tables for you. (examine the sample projects included in this repo)).
*   Also, the /src/main/webapp/WEB-INF/dispatcher-servlet.xml will need to change to point to the package where your Spring Controllers (will) live.

This longer pom file, is done as well as I could to show 'best practices' when making a larger complex single pom file.
pom files (which is what maven uses to build your application) can become very complex, until you become famaliar with maven more in depth, with heirarchies of pom files, parental referencing, etc. This pom should provide all the features you need for now. Listed below is a short list of the commands you could be inerested in, with explanations.

----

Eventually the copying of POM files will not be required, and we'll have a couple generation options, but for now, thats what we have. 

----

Once your customized new project is created, These commands will be available to you when in the project's root directory with the pom file.
Maven is the build tool that does all the compilation, etc. for you.

To Clean all local working directories:

    mvn clean

To Build the project, including running all Unit Tests:

    mvn package

Building will run all the tests, but if you want to manually run tests (Will run all Unit Tests, non-'*IntegrationTest.java' tests):

    mvn test

Building and running all the IntegrationTests (This is not yet implemented, so is considered experimental/beta)

    mvn integration-test

To test the app on a local webserver instance:

    mvn appengine:devserver

To test the app on a local webserver instance: (and run in the background, non-blocking):

    mvn appengine:devserver_start

To stop a background running version of the local webserver:

    mvn appengine:devserver_stop
    
To update the project to the Google App Engine servers(must be authorized developer, and follow steps to authorize the 'client'):

    mvn appengine:update

What 'Schmear' means: a number of related things, ideas, etc., resulting in a unified appearance, attitude, plan, or the like (usually used in the phrase the whole schmear). From dictionary.reference.com
