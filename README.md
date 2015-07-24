TeraConfig
==========

Contains configuration files for Terasology-related repositories. This repository contains configuration files for code Analytics: 

* CheckStyle
* FindBugs
* PMD

To use it, simply add it as a dependency and refer to it from the different tools like so:

```gradle
configurations {
    codeMetrics
}

dependencies {
    codeMetrics(group: 'org.terasology.config', name: 'codemetrics', version: '1.0.0', ext: 'zip')
}

checkstyle {
    config = resources.text.fromArchiveEntry(configurations.codeMetrics, "checkstyle/checkstyle.xml")
}

pmd {
    ruleSetConfig = resources.text.fromArchiveEntry(configurations.codeMetrics, "pmd/pmd.xml")
}

findbugs {
    excludeFilterConfig = resources.text.fromArchiveEntry(configurations.codeMetrics, "findbugs/findbugs-exclude.xml")
}
```
    
This is it!
