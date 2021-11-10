node() {

  stage ('Checkout'){
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ravitejaops/helloworld-java-maven.git']]])
    }
  /*stage ('Build') {
    withMaven  {
    sh 'mvn -B -DskipTests clean package'
    }
  }*/

 stage ('Scan and Build Jar File') {
               withSonarQubeEnv(installationName: 'sonarJenkins', credentialsId: 'sonarJenkins') {
                sh 'mvn clean install sonar:sonar \
                   -D sonar.projectKey=com.scmgalaxy.mavensample:my-maven \
                   -D sonar.host.url=http://35.179.15.141:9090/sonar \
                   -D sonar.login=9542888cc05d9907ff959385af4bbf1564c7d6f0 \
                   -D sonar.projectVersion=1.0.0 \
                   -D sonar.sources=src/main/java/ \
                   -D sonar.sourceEncoding=UTF-8 \
                   -D sonar.language=java \
                   -D sonar.java.libraries=target/ \
                   -D sonar.tests=src/test \
                   -D sonar.junit.reportPaths=target/surefire-reports/ \
                   -D sonar.surefire.reportPaths=target/surefire-reports/ \
                   -D sonar.jacoco.reportPaths=target/jacoco.exec \
                   -D sonar.java.coveragePlugin=jacoco \
                   -D sonar.verbose=true'
                }
        }
}
