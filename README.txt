to build this project you must Apache Maven at least 2.2.1 .
mvn clean install will install the mojos without running integration tests.
As there are some hardcoded integration tests with http port 1973, ajp 2001 and 2008, you could have some port allocation issues (if you don't know why those values ask olamy :-) )
mvn clean install -Prun-its will run integration tests too: to override the default used htpp port you can use -Dits.http.port= -Dits.ajp.port=
To deploy a snaphot version to http://people.apache.org/repo/m2-snapshot-repository/ (which is proxying by https://repository.apache.org/content/groups/snapshots-group/) you must run : mvn clean deploy .
Note you need some configuration in ~/.m2/settings.xml:
    <server>
      <id>apache.snapshots</id>
      <username>your asf id</username>
      <!--password></password-->
      <!--privateKey>path to your private key</privateKey-->
      <!--passphrase></passphrase-->
      <filePermissions>664</filePermissions>
      <directoryPermissions>775</directoryPermissions>
    </server

If you have a nice ssh key in ~/.ssh/ no need of configuring password, privateKey, passphrase.

Checkstyle: this project use the Apache Maven checkstyle configuration for ide codestyle files see http://maven.apache.org/developers/committer-environment.html .
