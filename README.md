<p align="center">
  <img src="https://openepcis.io/img/openepcis-logo.svg" alt="OpenEPCIS" width="30%">
</p>

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Maven Central](https://img.shields.io/maven-central/v/io.openepcis/openepcis-bom)](https://central.sonatype.com/artifact/io.openepcis/openepcis-bom)
[![Stars](https://img.shields.io/github/stars/openepcis/openepcis-bom?style=social)](https://github.com/openepcis/openepcis-bom)

<h1 align="center">OpenEPCIS BOM</h1>
This is the Maven parent for every [OpenEPCIS](https://openepcis.io) project. It centralizes dependency versions, the Java version, and build plugins, so all modules build consistently.

## Why

Without a shared parent, each module/repository sets its own versions for Quarkus, Jackson, and plugins, and they gradually drift apart. Using a single parent keeps them aligned: a module
declares a dependency without specifying a version, and the version comes from this parent.

## Use it

Inherit it as the parent:

```xml

<parent>
    <groupId>io.openepcis</groupId>
    <artifactId>openepcis-bom</artifactId>
    <version>0.9.3</version>
</parent>
```

Or import only the managed versions, if the project already has a parent:

```xml

<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>io.openepcis</groupId>
            <artifactId>openepcis-bom</artifactId>
            <version>${parent.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

OpenEPCIS repositories themselves follow the rolling `999-SNAPSHOT`, which always carries the newest
versions.

## What it manages

|                 |                                                                                          |
|-----------------|------------------------------------------------------------------------------------------|
| Java            | 25. Modules should not set `source`, `target` or `release` on their own                  |
| Quarkus         | 3.33.3 through `quarkus-bom`, plus the AWS services and CXF BOMs                         |
| Jackson         | 2.22.1 through `jackson-bom`                                                             |
| Other libraries | JSON-LD, JSON schema validation, Elasticsearch client, Swagger, commons                  |
| Build plugins   | compiler, surefire, failsafe, JaCoCo, Jandex, Checkstyle, license, javadoc, sources, GPG |

## Common commands

These work in any project that inherits this parent.

```bash
mvn git-code-format:format-code   # format the sources
mvn checkstyle:checkstyle         # run the style check
mvn license:format                # add the license header to new files
```

## Related

- [OpenEPCIS Tools](https://tools.openepcis.io/) - open source EPCIS 2.0 tools and services
- [OpenEPCIS](https://openepcis.io/) - Read more about OpenEPCIS
- [OpenEPCIS on GitHub](https://github.com/openepcis) - the repositories that use this BOM
- [benelog GmbH & Co. KG](https://www.benelog.com/) - Company behind the OpenEPCIS
- [GS1 EPCIS Standard](https://www.gs1.org/standards/epcis) - Learn more about EPCIS

## License

Licensed under the [Apache License 2.0](LICENSE).
