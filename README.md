# mvn-repo
Maxep's maven repository

### Deploying a Project

1. Clone the ```release``` or ```snapshot``` branch depending on deployment type.
2. Add the following section to the project's pom.xml:

  ```
    <distributionManagement>
      <repository>
        <id>repo</id>
        <url>https://raw.github.com/maxep/mvn-repo/releases</url>
      </repository>
      <snapshotRepository>
        <id>snapshot-repo</id>
        <url>https://raw.github.com/maxep/mvn-repo/snapshots</url>
      </snapshotRepository>
    </distributionManagement>
  ```
3. Deploy to the local repo's branch clone and push the artifacts to Github using the following command lines :

  ```
    mvn -DaltDeploymentRepository=snapshot-repo::default::file:/path/to/clone/of/mvn-repo/snapshots clean deploy
    cd /path/to/clone/of/mvn-repo
    git add .
    git commit -m "commit message"
    git push origin master
  ```

### Add Dependency

To add a project hosted on this repo as a dependency, add the following to your project's pom.xml

  ```
    <repositories>
      <repository>
          <id>maxep-releases</id>
          <url>https://raw.github.com/maxep/mvn-repo/releases</url>
      </repository>
    </repositories>
  ```
