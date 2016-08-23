# maven-repo
Hosting a Maven repository on github, poor man's public maven repo!

A good reference:

- [Hosting a Maven repository on github](http://stackoverflow.com/questions/14013644/hosting-a-maven-repository-on-github)
- [simbest-maven-repo](https://github.com/simbest/simbest-maven-repo)

Here, use the simpler way to install packages into local repository.

```
mvn install:install-file -Dfile=${JAR_FILE_PATH} -DgroupId=${GROUP_ID} -DartifactId=${ARTIFACT_ID} -Dversion=${VERSION} -Dpackaging=jar -DlocalRepositoryPath=${THIS_PROJECT_PATH}/repository -DgeneratePom=true -DcreateChecksum=true
```

Git commit and push it to the github, poor man's public repo!

Add the following snippet to any project's pom that depends on your project:
```
<repositories>
    <repository>
        <id>YOUR-PROJECT-NAME-mvn-repo</id>
        <url>https://raw.github.com/YOUR-USERNAME/YOUR-PROJECT-NAME/mvn-repo/</url>
        <snapshots>
            <enabled>true</enabled>
            <updatePolicy>always</updatePolicy>
        </snapshots>
    </repository>
</repositories>
```
