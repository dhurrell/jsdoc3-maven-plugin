jsdoc3-maven-plugin
===================

An automatic documentation generator for JavaScript within the Maven Reporting lifecycle.

## What is the jsdoc3-maven-plugin? ##
The jsdoc3-maven-plugin is a [modern maven plugin](http://maven.apache.org/plugin-tools/maven-plugin-plugin/examples/using-annotations.html)
built for the purposes of generating [jsdoc](http://usejsdoc.org/) along with the Maven Reporting lifecycle.  By default, the
plugin will bind to the _site_ phase, though this is configurable as with any other Maven plugin with goals.

## Getting Started ##
The following examples enumerate the most common POM configurations for the jsdoc3-maven-plugin.  This plugin is made
available through [Sonatype](http://www.sonatype.org/) and is synchronized with the central Maven repository.

## Release ##
The current release version is 1.0.4, using jsdoc3 [3.2](https://github.com/jsdoc3/jsdoc/branches/releases/3.2).

## Deprecation Notice ##
Usage of this plugin as a build plugin is now deprecated.  Support for execution of this plugin within project.build.plugins
will be dropped with release version 1.1.0.  Examples below reflect modern usage as a reporting plugin.

## Current Status ##
[![Build Status](https://travis-ci.org/phasebash/jsdoc3-maven-plugin.png)](https://travis-ci.org/phasebash/jsdoc3-maven-plugin)

### Example POM: Recurse subdirectories only ##
    <plugin>
        <groupId>com.github.phasebash</groupId>
        <artifactId>jsdoc3-maven-plugin</artifactId>
        <version>1.0.4</version>
        <configuration>
            <recursive>true</recursive>
            <directoryRoots>
                <directoryRoot>${basedir}/src/main/webapp/resources/js</directoryRoot>
                <directoryRoot>${basedir}/src/main/javascript</directoryRoot>
            </directoryRoots>
        </configuration>
        <executions>
            <execution>
                <goals>
                    <goal>jsdoc3</goal>
                </goals>
            </execution>
        </executions>
    </plugin>

### Example POM: Recurse subdirectories + errant files ##
    <plugin>
        <groupId>com.github.phasebash</groupId>
        <artifactId>jsdoc3-maven-plugin</artifactId>
        <version>1.0.4</version>
        <configuration>
            <recursive>true</recursive>
            <directoryRoots>
                <directoryRoot>${basedir}/src/main/webapp/resources/js</directoryRoot>
                <directoryRoot>${basedir}/src/main/javascript</directoryRoot>
            </directoryRoots>
            <sourceFiles>
                <sourceFile>${baseDir}/src/main/resources/js/classic.js</sourceFile>
            </sourceFiles>
        </configuration>
        <executions>
            <execution>
                <goals>
                    <goal>jsdoc3</goal>
                </goals>
            </execution>
        </executions>
    </plugin>

### Example POM: Cherry pick ##
    <plugin>
        <groupId>com.github.phasebash</groupId>
        <artifactId>jsdoc3-maven-plugin</artifactId>
        <version>1.0.4</version>
        <configuration>
            <sourceFiles>
                <sourceFile>${baseDir}/src/main/resources/js/menu.js</sourceFile>
                <sourceFile>${baseDir}/src/main/resources/js/header.js</sourceFile>
                <sourceFile>${baseDir}/src/main/resources/js/content.js</sourceFile>
                <sourceFile>${baseDir}/src/main/resources/js/ads.js</sourceFile>
            </sourceFiles>
        </configuration>
        <executions>
            <execution>
                <goals>
                    <goal>jsdoc3</goal>
                </goals>
            </execution>
        </executions>
    </plugin>

## Mojo Parameters ##
* directoryRoots - File[]: An Array of Files which will be used as directory roots, any file within this directory will be included into the final jsdoc argument list.
* recursive (Optional) - Boolean: A flag to indicate whether or not all directory roots should be searched and all files included recursively.
* lenient (Optional) - Boolean: A flag to indicate whether or not the generator should tolerate errors (false), or keep plodding along despite them (true).
* sourceFiles (Optional) - File[]: An Array of Files which will be included into the final jsdoc argument list.
* outputDirectory (Optional) - File: The place where jsdoc should be written.  default: "${project.build.directory}/site/jsdoc"
* includePrivate (Optional) - Boolean: A flag to indicate whether @private symbols are included in the generated documentation.
* tutorialsDirectory (Optional) - File: A file indicating where [jsdoc tutorial](http://usejsdoc.org/about-tutorials.html) resources can be found.
* configFile (Optional) - File: A [configuration](http://usejsdoc.org/about-configuring-jsdoc.html#configuration-file) file to be passed to jsdoc for more detailed project configuration.

## Questions, Feedback? ##
Feel free to submit an issue ticket through github or contact me directly.  I will help you.

## License ##
The jsdoc3-maven-plugin has been released under [Apache 2.0](https://github.com/phasebash/jsdoc3-maven-plugin/blob/master/LICENSE.md) as per all it's dependencies.

