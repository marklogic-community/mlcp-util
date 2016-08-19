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
    
