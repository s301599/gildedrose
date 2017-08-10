node {
    
    stage ('Preperation'){
        
git credentialsId: 'c663434e-cd4c-451e-a0a0-9ad53341d659', url: 'https://github.com/s301599/gildedrose.git'
  
    }
    
    stage ('Build'){
    sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'

    }
    
    stage ('Results')
    {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'

        
    }
    
      stage ('Javadoc')
    {
         sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'

            archive 'target/site/**/*'


        
    }
    
}
