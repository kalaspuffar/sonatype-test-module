# sonatype-test-module

This is a test module for sonatype to test the deploy functionality.

### Settings.xml

Below is the setup for this repository. This should be put in your local maven repository `~/.m2/settings.xml`.
The file contains credentials for release and snapshot deployments.
You also need to specify a profile if you want to sign packages.
Lastly we add information about the default mirror, this is specifying the mirror to use for packages. We will use the public repository that contains snapshots, releases and the central repository.
```
<settings>
  <servers>
    <server>
      <id>nexus-releases</id>
      <username>[release-username]</username><
      <password>[release-password]</password>
    </server>
    <server>
      <id>nexus-snapshots</id>
      <username>[snapshot-username]</username>
      <password>[snapshot-password]</password>
    </server>
  </servers>
  <profiles>
    <profile>
      <id>localSonaId</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <properties>
        <gpg.executable>gpg</gpg.executable>
        <gpg.passphrase>[gpg-keyfile-password]</gpg.passphrase>
      </properties>
    </profile>
  </profiles>
  <mirrors>
    <mirror>
      <id>central</id>
      <name>central</name>
      <url>http://[host+port]/repository/maven-public/</url>
      <mirrorOf>*</mirrorOf>
    </mirror>
  </mirrors>
</settings>
```
