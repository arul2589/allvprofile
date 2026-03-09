pipeline {
    agent any
    tools{
        // tools which is instaled in jenkise tool config.
        maven "Maven3.9"
        jdk "JDK17"
    }
    stages {
        stage("fetch")//fetch the code from git hub.
            steps{
                git branch: 'atom' , url: 'https://github.com/arul2589/allvprofile.git'
            }        
    }
    stages {
        stage("test")//testing the pakage.
            steps{
                sh 'mvn test'
            }        
    }
    stages {
        stage("Build")//creating the target file
            steps{
                sh 'mvn install -Dskiptest'
            }
            post {
                success{
                    //creating the target file
                    echo "Archiving artifact"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }    
    }
}