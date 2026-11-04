pipeline {                                    // 1  // Defines the start of the Jenkins pipeline block
    agent any                                 // Specifies the pipeline can run on any available agent
    environment {                             // 2  // Defines environment variables for the pipeline
        PATH = "/opt/maven/bin:$PATH"         // Adds Maven's path to the system's PATH variable
    }                                         // 2  // Ends the environment block

    stages {                                  // 3  // Defines the stages block where multiple stages are declared
        
        stage("build") {                      // 4  // Creates a stage named 'build'
            steps {                           // 5  // Defines the steps that will be executed in this stage
                sh 'mvn clean deploy'         // Runs the Maven clean and deploy command to build the project
            }                                 // 5  // Ends the steps block for 'build' stage
        }                                     // 4  // Ends the 'build' stage

        stage('SonarQube analysis') {         // 6  // Creates a stage named 'SonarQube analysis'
            environment {                     // 7  // Defines environment variables specific to this stage
                scannerHome = tool 'saidemy-sonar-scanner'  
                                              // Sets the SonarQube scanner tool
            }                                 // 7  // Ends the environment block for this stage

            steps {                           // 8  // Defines the steps that will be executed in this stage
                withSonarQubeEnv('saidemy-sonarqube-server') {
                                              // Executes the SonarQube analysis within the SonarQube environment
                    sh "${scannerHome}/bin/sonar-scanner"  
                                              // Runs the SonarQube scanner tool
                }                             // Ends the withSonarQubeEnv block
            }                                 // 8  // Ends the steps block for 'SonarQube analysis' stage
        }                                     // 6  // Ends the 'SonarQube analysis' stage

    }                                         // 3  // Ends the stages block
}                                             // 1  // Ends the pipeline block

