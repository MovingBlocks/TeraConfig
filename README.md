# TeraConfig

Contains configuration files for Terasology-related repositories. This repository contains configuration files for code Analytics: 

* CheckStyle
* FindBugs
* PMD

## Using TeraConfig

Add the Terasology Artifactory to `repositories` in your gradle build file (e.g. `build.gradle`):
```gradle
maven {
    name = "Terasology Artifactory"
    url = "http://artifactory.terasology.org/artifactory/virtual-repo-live"
    allowInsecureProtocol = true  // 😱
}
```

With that, simply add it as a dependency and refer to it from the different tools like so:

```gradle
configurations {
    codeMetrics
}

dependencies {
    codeMetrics(group: 'org.terasology.config', name: 'codemetrics', version: '1.6.3', ext: 'zip')
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

## Releasing TeraConfig

1. Tag a commit according to the version you'd like to release
   - _the tag should be valid [SemVer](https://semver.org/#semantic-versioning-specification-semver) prefixed with `v`, e.g. `v1.2.3`_
2. Push the tag
3. The github action configured in this repository will automatically create and publish the respective artifact
