### Installing Java 8 on CentOS
Download jdk into /opt/ directory.
```
# cd /opt/
# wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.tar.gz"
```
Open archieve.
```
# tar xzf jdk-8u121-linux-x64.tar.gz
# cd /opt/jdk1.8.0_121/
```
Install. (at 2nd step choose the last one, or press enter if there is one option)
```
# alternatives --install /usr/bin/java java /opt/jdk1.8.0_121/bin/java 2
# alternatives --config java
```
(recommended) Setup javac and jar commands path.
```
# alternatives --install /usr/bin/jar jar /opt/jdk1.8.0_121/bin/jar 2
# alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_121/bin/javac 2
# alternatives --set jar /opt/jdk1.8.0_121/bin/jar
# alternatives --set javac /opt/jdk1.8.0_121/bin/javac
```
Change to your home directory and check whether java version is correct.
```
# java -version
java version "1.8.0_121"
Java(TM) SE Runtime Environment (build 1.8.0_121-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.121-b13, mixed mode)
```
