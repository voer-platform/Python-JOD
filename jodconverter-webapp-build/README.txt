#Author: Gbenga Badipe
#Date: 4/24/2012

## Important ##
The global variable JAVA_HOME should be set to point to your JAVA installation

########### INSTALLATION INSTRUCTIONS ###########
1. Configure JOD's parameters in a config file called "config.properties" located in: 'jodconverter-tomcat-2.2.2/bin/'

2. Open install.sh and confirm that the path to your open office libraries match with '/usr/lib/libreoffice/basis-link/ure-link/lib'. If it does not
   you will have to modify the path assigned to the variable PIPE_PATH in 'install.sh' to point to your open office libraries.

3. Install JOD by running the script 'install.sh' in the root directory using the command: 
   sudo ./install.sh

4. Check localhost:8080/converter/ to confirm the converter is running


########### PYTHON SCRIPT INSTRUCTIONS ###########

To execute batch conversion use the format:
----------------------------------------------
python convert.py -b [testbed directory]  [output directory] [number of documents] [format of documents] [output format]

Example: python convert.py -b /home/foo/ /home/foo/outputdir 3 doc odt

To execute a single file conversion use format:
-----------------------------------------------
python convert.py [file location] [output_directory] [format] [output format]

Example: python convert.py ~/foo.doc ~/outputdir/ doc odt


########### Startup and Shutdown of JOD ###########

Startup and shutdown scripts are also included in the root directory. Please use them to startup and shutdown JOD after installation.

########### TROUBLESHOOTING ###########

- You may have to install maven to run ./install.sh. This install script uses maven to build jodconverter-webaap.
  Example to install maven on ubuntu:

    $ sudo apt-get install maven2

- To have JODConverter and maven work, you should have Oracle Sun JDK installed instead of OpenJDK.
  Example to install Oracle Sun JDK on ubuntu:

    $ sudo apt-get install python-software-properties
    $ sudo add-apt-repository ppa:webupd8team/java
    $ sudo apt-get update
    $ sudo apt-get install oracle-java7-installer

- You may need to run install.sh and startup.sh with sudo -E to include your custom environment variables.

    $ export JAVA_HOME=/usr/lib/jvm/java-7-oracle
    $ sudo -E ./install.sh

- To re-compile jodconverter core you can run:

    $ cd lib/jodconverter-core/
    $ mvn -DskipTests -Djava.library.path=/full/path/to/Python-JOD/jodconverter-webapp-build/lib/hyperic-sigar-1.6.5/sigar-bin/lib install

  And copy the compiled package outside.

    $ cp target/jodconverter-core-3.0-SNAPSHOT.jar ../../

