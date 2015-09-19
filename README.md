The purpose of this project is to demonstrate the WAGON-426 bug (https://issues.apache.org/jira/browse/WAGON-426) and
 show the https://github.com/apache/maven-wagon/pull/16 FIX.

# Steps to reproduce WAGON-426

* backup your ~/.ssh/known_hosts file
* add the following line (test ecdsa fingerprint) in your ~/.ssh/known_hosts file
```
test ecdsa-sha2-nistp256 TESTTESTTESTTES
```
* run ```mvn site:site site:deploy```
* check the ~/.ssh/known_hosts file: the ecdsa key has disappeared

# Steps to test the fix

* add the following line (test ecdsa fingerprint) in your ~/.ssh/known_hosts file
```
test ecdsa-sha2-nistp256 TESTTESTTESTTES
```
* run ```mvn -Pfix site:site site:deploy``` (note the -Pfix that activates a profile that will download the fixed
version of maven-wagon from https://github.com/marob/maven-wagon)
* check the ~/.ssh/known_hosts file: the ecdsa key is still here