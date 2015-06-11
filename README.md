# AppFog Spring Boot Jumpstart

## Introduction

The AppFog Spring Boot Jumpstart is a sample application that can be used to get started quickly with a new Spring Boot web application on AppFog.

## Getting Started

### Installing Gradle

This sample application uses Gradle to manage dependencies and build the WAR file that will be later be deployed to AppFog.
To install Gradle, please follow the steps in https://docs.gradle.org/current/userguide/installation.html

### Building the app and pushing to AppFog

To get started, copy the contents of this repo to a new source code repository that you have edit privileges to. Clone that repository and [login to AppFog](https://www.centurylinkcloud.com/knowledge-base/appfog/login-using-cf-cli/). To deploy the application, run the following from the top-level project directory:

```
$ gradle build
$ cf push
```

Since the manifest.yml file sets the name of the application to `${random-word}`, the name of the application will be generated during the deployment process. Here is example output of the application deployment using `cf push`:

```
$ cf push
Using manifest file /Users/demo/projects/af-spring-boot-jumpstart/manifest.yml

Creating app fittable-sketchbook in org DEMO / space Dev as Demouser...
OK
h
Creating route fittable-sketchbook.useast.appfog.ctl.io...
OK

Binding fittable-sketchbook.useast.appfog.ctl.io to fittable-sketchbook...
OK

Uploading fittable-sketchbook...
Uploading app files from: /Users/demo/projects/af-spring-boot-jumpstart/build/libs/spring-boot-test.war
Uploading 537.2K, 86 files
Done uploading               
OK

Starting app fittable-sketchbook in org DEMO / space Dev as Demouser...
-----> Downloaded app package (11M)
-----> Java Buildpack Version: v3.0 | https://github.com/cloudfoundry/java-buildpack.git#3bd15e1
-----> Downloading Open Jdk JRE 1.8.0_45 from https://download.run.pivotal.io/openjdk/trusty/x86_64/openjdk-1.8.0_45.tar.gz (2.0s)
       Expanding Open Jdk JRE to .java-buildpack/open_jdk_jre (1.7s)
-----> Downloading Spring Auto Reconfiguration 1.7.0_RELEASE from https://download.run.pivotal.io/auto-reconfiguration/auto-reconfiguration-1.7.0_RELEASE.jar (0.2s)

-----> Uploading droplet (55M)

0 of 1 instances running, 1 starting
0 of 1 instances running, 1 down
0 of 1 instances running, 1 starting
1 of 1 instances running

App started


OK

App fittable-sketchbook was started using this command `SERVER_PORT=$PORT $PWD/.java-buildpack/open_jdk_jre/bin/java -cp $PWD/.:$PWD/.java-buildpack/spring_auto_reconfiguration/spring_auto_reconfiguration-1.7.0_RELEASE.jar -Djava.io.tmpdir=$TMPDIR -XX:OnOutOfMemoryError=$PWD/.java-buildpack/open_jdk_jre/bin/killjava.sh -Xmx160M -Xms160M -XX:MaxMetaspaceSize=64M -XX:MetaspaceSize=64M -Xss853K org.springframework.boot.loader.WarLauncher`

Showing health and status for app fittable-sketchbook in org DEMO / space Dev as Demouser...
OK

requested state: started
instances: 1/1
usage: 256M x 1 instances
urls: fittable-sketchbook.useast.appfog.ctl.io
last uploaded: Wed Jun 10 16:54:37 UTC 2015

     state     since                    cpu    memory           disk           details   
#0   running   2015-06-10 01:55:39 PM   0.6%   218.1M of 256M   131.1M of 1G  
```

Once the application is running, copy the value for `urls:`, in the case above `fittable-sketchbook.useast.appfog.ctl.io`, and go to that URL in a browser. You should see a page that looks like:

<img src="https://raw.githubusercontent.com/CenturyLinkCloud/af-static-jumpstart/master/images/welcome-to-appfog-screenshot.png"/>
 
## Customizing the app

### Knowing where the code is

* Web page: `src/main/webapp/index.html`.
* Application Controller: `src/main/java/sample/sb/Application.java`.
* Test: `src/main/java/sample/sb/ApplicationTests.java`.

### Moving forward

You could add a controller in `src/main/java/sample/sb/`, maybe like this one:

```
package sample.b;

import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.RequestMapping;

@RestController
public class HelloController {

    @RequestMapping("/hi")
    public String index() {
        return "Hey there!";
    }

}
```

There are a lot of good examples of Spring Boot applications [here](https://spring.io/guides/).