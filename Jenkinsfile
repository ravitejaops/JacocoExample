node() {

  stage ('Checkout'){
    checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ravitejaops/JacocoExample.git']]])
    }
  /*stage ('Build') {
    withMaven  {
    sh 'mvn -B -DskipTests clean package'
    }
  }*/

 stage ('Scan and Build Jar File') {
               withSonarQubeEnv('sonarqube') {
                sh 'mvn clean install sonar:sonar \
                   -D sonar.projectKey=com.scmgalaxy.mavensample:my-maven \
                   -D sonar.host.url=http://18.133.170.11:9000/sonar \
                   -D sonar.login=64c4d8679d2ed38a5b1d92c9fb33ea01046b5f7d \
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
  stage ('cleanWorkspace') {
  cleanWs()
  }
}
