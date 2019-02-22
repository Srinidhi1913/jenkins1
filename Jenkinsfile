node {
stage ('Prepare') {
echo "Github"
git 'https://github.com/Srinidhi1913/jenkins1.git'
}
stage ('Build') {
echo "Maven"
sh 'mvn package -f spring-boot-samples/spring-boot-sample-war/pom.xml'
}
stage ('Test') {
echo "test"
}
stage ('Nexus') {
echo "nexus"
nexusArtifactUploader artifacts: [[artifactId: 'spring-boot-sample-war', classifier: '', file: 'spring-boot-samples/spring-boot-sample-war/target/spring-boot-sample-war-1.4.0.BUILD-SNAPSHOT.war', type: 'war']], credentialsId: '95800f90-058e-4260-b7a1-eaf50ab430f6', groupId: 'org.springframework.boot', nexusUrl: '52.15.81.192:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.4.0.BUILD-SNAPSHOT'
}
stage ('Deploy') {
echo "tomcat"
  echo "going to temp"
sh 'cd /tmp;' 
  echo "wget"
sh 'wget http://52.15.81.192:8081/nexus/content/repositories/snapshots/org/springframework/boot/spring-boot-sample-war/1.4.0.BUILD-SNAPSHOT/spring-boot-sample-war-1.4.0.BUILD-20190221.013909-4.war;'
  echo "copy to folder"
sh 'sudo cp spring-boot-sample-war-1.4.0.BUILD-20190221.013909-4.war /var/lib/tomcat/webapps/;'
}
}
