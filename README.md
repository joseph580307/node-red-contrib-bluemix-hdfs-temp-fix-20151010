bluemixhdfs
========================
This is a tempary fix node-red-contrib-bluemix-hdfs 0.2.3


Problem fixed:
---------------------------------------------------------------------------
The ibmhdfs in Node-RED on Bluemix was broken after the Analysys for Hadoop
server upgrade on July 2015.  The issue has been pending for 3 months.

With this temparay fix, you can use "ibm hdfs in" to write data to hadoop now.

To apply the fix:
 
1. Use BLuemix DevOps to edit the package.json in your IOT/Node-Red project.
   Change this line:
    "node-red-contrib-bluemix-hdfs":"0.x";
    to
    "node-red-contrib-bluemix-hdfs":"git+https://github.com/joseph580307/node-red-contrib-bluemix-hdfs-temp-fix-20151010.git",
        
2. Commmit the change. Build/Redeploy the project. 

3. Open your Node-RED. Add the "ibm hdfs in" node in your diagram. In the dialog, the 
   filename field MUST start with /.
   eg. /sensorinfo.json
   
4. Enable the "Append new line?".
   I didn't test the "Overwrite complete file" 
   
5. That's all. You can use Hadoop HDFS explorer to see if the file is created and data are appended.
   https://bi-hadoop-prod-<Cluster ID>.services.dal.bluemix.net:8443/gateway/default/hdfs/explorer.html

---------------------------------------------------------------------------

Reference:

https://www.npmjs.com/package/node-red-contrib-bluemix-hdfs
http://www.slideshare.net/JosephChang8/bluemix-hadoop-beginners-guide-part-i
