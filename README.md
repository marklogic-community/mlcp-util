# Archived repository

This repository has been archived. All classes have been migrated to the
[ml-javaclient-util subproject in the ml-gradle repository](https://github.com/marklogic/ml-gradle/tree/master/ml-javaclient-util).
The classes will be available in the upcoming ml-gradle 6.0.0 release.


This library provides a bean-like interface for mlcp. It doesn't depend on mlcp - it just collects arguments
and then returns them as a list, which you can then feed into mlcp.

Typical usage of this library looks like this:

    MlcpBean bean = new MlcpBean();
    bean.setHost("localhost");
    // Set any other properties you want, and then build the array of args
    String[] args = bean.buildArgs();
    
    // Use mlcp OptionsFileUtil class to expand arguments, such as an options file
    String[] expandedArgs = OptionsFileUtil.expandArguments(args);
    
    // Optional - log the args before running mlcp, using whatever logging framework you wish
    logger.info(bean.viewArgs(expandedArgs));
    
    // Invoke mlcp
    ContentPump.runCommand(expandedArgs);
    
