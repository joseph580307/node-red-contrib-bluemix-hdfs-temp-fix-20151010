bluemixhdfs
========================


Fix Note
---------------------------------------------------------------------------
The ibmhdfs in Node-RED on Bluemix was broken after the Analysys for Hadoop
server upgrade on July 2015.  The issue has been pending for so long.

With this temparay fix, you can use "ibm hdfs in" to flow data to hadoop now.

To apply the fix:
 
1. Modify the package.json of you IOT/Node-Red server by change:
    "node-red-contrib-bluemix-hdfs":"0.x";
    to
    "node-red-contrib-bluemix-hdfs":"git+https://github.com/joseph580307/node-red-contrib-bluemix-hdfs-temp-fix-20151010.git",
        
2. Redeploy the application.  For me I use Bluemix DevOps. 

3. Add the "ibm hdfs in" node in your diagram. The filename, MUST start with /.
   eg. /sensorinfo.csv
   
4. Check the "Append new line?". "Overwrite complete file is not tested"
   
5. You can use Hadoop HDFS explore to see if the file is created and data are appended.

---------------------------------------------------------------------------

This is a Node-RED node meant for connecting to the Big Data on IBM Bluemix.
This Node-RED node can be used only within the IBM Bluemix environment. This node requires a bound Analytics for Apache Hadoop service to work.  

In case there is no bound Analytics for Apache Hadoop, then the node will warn about its inability to connect to the HDFS system and will not work.  


Install
-------
Install from [npm](http://npmjs.org)
```
npm install node-red-contrib-bluemix-hdfs
```

Usage
-------

**HDFS Out Node**

The HDFS Out node can be used to 

1. Create File
2. Append to File and 
3. Delete File

  
**HDFS In Out Node**

The HDFS In Out node can be used to 

1. Read the file contents
