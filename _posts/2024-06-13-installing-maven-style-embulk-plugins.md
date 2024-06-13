---
layout: posts
title: "Installing Maven-style Embulk plugins"
date: 2024-06-13
description: "We recently started to provide a couple of methods to install the Maven-style Embulk plugins more easily, which was not very easy in the beginning of Maven-style plugins, indeed. This article is a brief introduction of the methods to install the Maven-style Embulk plugins."
author: "dmikurube"
---

Since [Embulk v0.11.0 was released a year ago](https://github.com/embulk/embulk/releases/tag/v0.11.0), we have pushed the new Maven-style Embulk plugins rather than the legacy RubyGems-style plugins.

See also: [Embulk v0.11 is coming soon: JRuby](https://www.embulk.org/articles/2023/04/13/embulk-v0.11-is-coming-soon.html#jruby)

We recently started to provide a couple of methods to install the Maven-style Embulk plugins more easily, which was not very easy in the beginning of Maven-style plugins, indeed.

This article is a brief introduction of the methods to install the Maven-style Embulk plugins.

## Revisit: Embulk home

Embulk now has a concept of the "Embulk home" directory, which is a directory to contain `embulk.properties` and Embulk plugin installations. The Maven-style Embulk plugins will also be installed in the Embulk home directory.

See again: [Embulk v0.11 is coming soon: Embulk home](https://www.embulk.org/articles/2023/04/13/embulk-v0.11-is-coming-soon.html#embulk-home)

## #1: Embulk's built-in subcommand `install`

[Embulk v0.11.3](https://github.com/embulk/embulk/releases/tag/v0.11.3) introduced a new Embulk subcommand: `embulk install`, instead of `embulk gem install` for RubyGems-style plugins. This subcommand takes a Maven artifact notation as its argument. The example below installs [`org.embulk:embulk-input-s3:0.6.0` from Maven Central](https://central.sonatype.com/artifact/org.embulk/embulk-input-s3/0.6.0).

```
$ java -jar embulk-0.11.3.jar install "org.embulk:embulk-input-s3:0.6.0"
...
...
2024-06-13 15:46:11.537 +0900 [INFO] (main): The path "/home/user/.embulk/lib/m2/repository" (m2_repo) does not exist. Creating it as a directory.
2024-06-13 15:46:11.619 +0900 [INFO] (main): No alternative remote Maven repositories are specified. Downloading artifacts from Maven Central.
2024-06-13 15:46:11.633 +0900 [INFO] (main): Downloading org.embulk:embulk-input-s3:pom:0.6.0 from https://repo.maven.apache.org/maven2
2024-06-13 15:46:12.725 +0900 [INFO] (main): Downloaded org.embulk:embulk-input-s3:pom:0.6.0 at /home/user/.embulk/lib/m2/repository/org/embulk/embulk-input-s3/0.6.0/embulk-input-s3-0.6.0.pom
2024-06-13 15:46:12.776 +0900 [INFO] (main): Downloading com.amazonaws:aws-java-sdk-s3:pom:1.11.466 from https://repo.maven.apache.org/maven2
2024-06-13 15:46:13.027 +0900 [INFO] (main): Downloaded com.amazonaws:aws-java-sdk-pom:pom:1.11.466 at /home/user/.embulk/lib/m2/repository/com/amazonaws/aws-java-sdk-pom/1.11.466/aws-java-sdk-pom-1.11.466.pom
...
...
2024-06-13 15:46:14.857 +0900 [INFO] (main): Downloading org.embulk:embulk-input-s3:jar:0.6.0 from https://repo.maven.apache.org/maven2
2024-06-13 15:46:14.857 +0900 [INFO] (main): Downloading com.amazonaws:aws-java-sdk-s3:jar:1.11.466 from https://repo.maven.apache.org/maven2
...
...
2024-06-13 15:46:15.720 +0900 [INFO] (main): Downloaded org.embulk:embulk-input-s3:jar:0.6.0 at /home/user/.embulk/lib/m2/repository/org/embulk/embulk-input-s3/0.6.0/embulk-input-s3-0.6.0.jar
2024-06-13 15:46:15.721 +0900 [INFO] (main): Downloaded com.amazonaws:aws-java-sdk-s3:jar:1.11.466 at /home/user/.embulk/lib/m2/repository/com/amazonaws/aws-java-sdk-s3/1.11.466/aws-java-sdk-s3-1.11.466.jar
...
...
2024-06-13 15:46:15.730 +0900 [INFO] (main): Installed org.embulk:embulk-input-s3:jar:0.6.0 at /home/user/.embulk/lib/m2/repository/org/embulk/embulk-input-s3/0.6.0/embulk-input-s3-0.6.0.jar
2024-06-13 15:46:15.730 +0900 [INFO] (main): Installed com.amazonaws:aws-java-sdk-s3:jar:1.11.466 at /home/user/.embulk/lib/m2/repository/com/amazonaws/aws-java-sdk-s3/1.11.466/aws-java-sdk-s3-1.11.466.jar
...
...
```

This subcommand downloads also the dependencies of the specified Maven artifact transitively as you can see in the example above.

Note that you can change the destination Embulk home directory by Embulk's standard options. See the example below.

```
$ java -jar embulk-0.11.3.jar -Xembulk_home=/tmp/foo install "org.embulk:embulk-input-s3:0.6.0"
...

$ env EMBULK_HOME=/tmp/bar java -jar embulk-0.11.3.jar install "org.embulk:embulk-input-s3:0.6.0"
...
```

It now supports only [Maven Central](https://central.sonatype.com/) as the remote repository, unfortunately.

## #2: Out-of-Embulk Embulk plugin installer

Embulk has had the `mkbundle` subcommand and the `-b` option so that users can maintain plugin installations by `Gemfile`, but it works only for RubyGems-style plugins, of course.

[The Gradle `org.embulk.runset` plugin](https://github.com/embulk/gradle-embulk-runset) is an alternative for Maven-style Embulk plugin. It works out of the Embulk package at all.

To use this, set up an environment for [Gradle](https://gradle.org/install/) at first. [Gradle 8.7](https://docs.gradle.org/8.7/userguide/userguide.html) is at least required. You may want to choose [the Gradle wrapper](https://docs.gradle.org/8.7/userguide/userguide.html) in typical use-cases.

Next, write `build.gradle` to declare the Maven-based Embulk plugins you wanted to install.

```
plugins {
    id "org.embulk.runset" version "0.2.0"  // Just apply this Gradle plugin.
}

repositories {
    mavenCentral()
}

installEmbulkRunSet {
    // Set your Embulk home directory (absolute path) to install the Embulk plugins and "embulk.properties".
    embulkHome file("/home/user/my-embulk-home")

    // Specify the Maven-style Embulk plugin by the "artifact" directive.
    artifact "org.embulk:embulk-input-s3:0.6.0"

    // You can specify multiple versions of the same Embulk plugin so that you can choose the version at runtime.
    // You can also specify an artifact with the split-style notation.
    artifact group: "org.embulk", name: "embulk-input-s3", version: "0.5.3"

    // Specify this if you need JRuby.
    // It downloads jruby-complete-9.1.15.0.jar, and set the "jruby" Embulk System Property in "embulk.properties".
    jruby "org.jruby:jruby-complete:9.1.15.0"

    // Specify this if you need to set some Embulk System Properties manually.
    // It sets the "key" Embulk System Property to "value" in "embulk.properties".
    embulkSystemProperty "key", "value"
}
```

Then, run `gradle installEmbulkRunSet` (`./gradlew` when you use the Gradle wrapper) to set up.

```
$ gradlew installEmbulkRunSet

> Configure project :
Supplied embulkHome "/home/user/my-embulk-home" does not exist, then will be created.
Setting to copy org.embulk:embulk-input-s3:0.6.0:jar into org/embulk/embulk-input-s3/0.6.0
Setting to copy com.amazonaws:aws-java-sdk-s3:1.11.466:jar into com/amazonaws/aws-java-sdk-s3/1.11.466
...
...
Setting to copy org.embulk:embulk-input-s3:0.5.3:jar into org/embulk/embulk-input-s3/0.5.3
...
...
Setting to copy org.embulk:embulk-input-s3:0.5.3:pom into org/embulk/embulk-input-s3/0.5.3
...
...
Setting to copy org.jruby:jruby-complete:9.1.15.0:jar into org/jruby/jruby-complete/9.1.15.0

BUILD SUCCESSFUL in 2s
1 actionable task: 1 executed
```

The Embulk System Properties file `embulk.properties` is automatically generated in the specified Embulk home, too.

```
#Generated by the "org.embulk.embulk-runset" Gradle plugin.
#Thu Jun 13 16:53:31 JST 2024
key=value
jruby=file\:///home/user/my-embulk-home/lib/m2/repository/org/jruby/jruby-complete/9.1.15.0/jruby-complete-9.1.15.0.jar
```

## Run!

In either style of installation, you can run Embulk with the installed Maven-style Embulk plugins.

See the example `s3_with_maven.yaml` below.

```yaml
in:
  # The full-style type notation for Maven-style Embulk plugins.
  type:
    source: maven
    group: org.embulk
    name: s3
    version: 0.6.0
  bucket: ...
  parser:
    type: csv
    ...
out:
  type: stdout
```

Then, run Embulk!

```
$ java -jar embulk-0.11.4.jar -Xembulk_home=/home/user/my-embulk-home run s3_with_maven.yml
2024-06-13 17:01:55.373 +0900 [INFO] (main): embulk_home is set from command-line: /home/user/my-embulk-home
2024-06-13 17:01:55.378 +0900 [INFO] (main): m2_repo is set as a sub directory of embulk_home: /home/user/my-embulk-home/lib/m2/repository
2024-06-13 17:01:55.378 +0900 [INFO] (main): gem_home is set as a sub directory of embulk_home: /home/user/my-embulk-home/lib/gems
2024-06-13 17:01:55.378 +0900 [INFO] (main): gem_path is set empty.
2024-06-13 17:01:55.378 +0900 [DEBUG] (main): Embulk system property "default_guess_plugin" is set to: "gzip,bzip2,json,csv"
2024-06-13 17:01:55.634 +0900 [INFO] (main): Started Embulk v0.11.4
2024-06-13 17:01:55.811 +0900 [INFO] (0001:transaction): Loaded plugin embulk-input-s3 (maven:org.embulk:s3:0.6.0)
...
...
2024-06-13 17:01:55.948 +0900 [INFO] (0001:transaction): Loaded plugin embulk-output-stdout
...
...
2024-06-13 17:01:56.052 +0900 [INFO] (0001:transaction): Loaded plugin embulk-parser-csv
...
...
2024-06-13 17:01:56.691 +0900 [INFO] (0001:transaction): Start listing file with prefix [******]
2024-06-13 17:01:57.577 +0900 [INFO] (0001:transaction): Found total [1] files
2024-06-13 17:01:57.721 +0900 [INFO] (0001:transaction): Using local thread executor with max_threads=16 / output tasks 8 = input tasks 1 * 8
2024-06-13 17:01:57.759 +0900 [INFO] (0001:transaction): {done:  0 / 1, running: 0}
...
...
1,foo
2,bar
3,baz
2024-06-13 17:01:58.602 +0900 [INFO] (0001:transaction): {done:  1 / 1, running: 0}
2024-06-13 17:01:58.603 +0900 [INFO] (0001:transaction): Incremental job, setting last_path to [******.csv]
2024-06-13 17:01:58.618 +0900 [INFO] (0001:transaction): Embulk system property "plugins.output.stdout" is not set.
2024-06-13 17:01:58.619 +0900 [INFO] (0001:transaction): Embulk system property "plugins.default.output.stdout" is not set.
2024-06-13 17:01:58.621 +0900 [INFO] (main): Committed.
2024-06-13 17:01:58.629 +0900 [INFO] (main): Next config diff: {"in":{"last_path":"******.csv"},"out":{}}
```

We hope those installation methods will help you.
