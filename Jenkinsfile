pipeline {
  agent {
    node {
      label "built-in"
      customWorkspace "/mnt/project"
    }
  }
  stages {
    stage ("git-clone") {
      steps {
        sh "rm -rf game-of-life"
        sh "git clone https://github.com/nileshtamboli123/game-of-life.git"
      }
    }
    stage ("maven-build") {
      steps {
        dir ("/mnt/project/game-of-life") {
          sh "mvn clean install"
        dir ("gameoflife-web/target") {
          sh "cp -r gameoflife.war /mnt/server/apache-tomcat-9.0.75/webapps"
        }  
        }
      }
    }
  }
}
