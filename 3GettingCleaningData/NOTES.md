## Week 1

### Getting xlsx package to work

The linking for Java in OsX isn't what R expects. In the shell:

```bash
cd $(/usr/libexec/java_home)
sudo mkdir -p bundle/Libraries
cd bundle/Libraries
sudo ln -fs ../../jre/lib/server/libjvm.dylib libserver.dylib


java -showversion # ???
```


```R
install.packages('xlsx')
library('xlsx')

install.packages('rJava', type='source')

library(rJava)
.jinit() # this starts the JVM

java -showversion



```bash
from Apple
https://support.apple.com/kb/DL1572?locale=en_US

export JAVA_HOME=/Library/Java/Home
java -version
```

```R
Sys.setenv(JAVA_HOME = '/Library/Java//Home')
# Java 1.6 will set up the 'Home' link under /Library/Java
Sys.setenv(LD_LIBRARY_PATH = '$LD_LIBRARY_PATH:$JAVA_HOME/lib')
