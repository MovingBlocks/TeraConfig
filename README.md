TeraConfig
==========

Contains configuration files for Terasology-related repositories. This currently involves the  [Terasology](https://github.com/MovingBlocks/Terasology) main project, [TerasologyLauncher](https://github.com/MovingBlocks/TerasologyLauncher), [WorldViewer](https://github.com/MovingBlocks/WorldViewer) and [CrashReporter](https://github.com/MovingBlocks/CrashReporter).

This repository contains configuration files for 

* Code Analytics: CheckStyle, FindBugs and PMD
* Eclipse compiler settings
* Code formatting templates
* Comment template (file header!) and 
* Code snippets (logging)

Setup
-------

Add it to your project with:

    $ git submodule add https://github.com/MovingBlocks/TeraConfig.git config
  
Make sure to commit the newly created file "config" and the ".gitmodules" file in your project.

If you check out the project for the first time, use:

    $ git submodule init

This will clone the submodule from the remote git repository. It will always point to the same revision unless you manually update the submodule reference with:

    $ git submodule update
    
This is it!
