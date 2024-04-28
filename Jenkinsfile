pipeline{
    agent any
    environment{
        SONAR_HOME= tool "Sonar"
    }
    stages{
        stage('Cloning code from GitHub'){
            steps{
                git url: "https://github.com/Kirthik1104/wanderlust.git", branch: "DevSecOps"
            }
        }
        stage('Starting the SonarQube Server'){
            steps{
                sh "docker start sonarqube-server"
            }
        }
        stage('SonarQube Quality Analysis'){
            steps{
                withSonarQubeEnv('Sonar'){
                    echo "Waiting for 5 minutes for sonarqube to start the server"
                    sleep 60
                    sh "$SONAR_HOME/bin/sonar-scanner -Dsonar.projectKey=wanderlust -Dsonar.projectName=3-tier-application-usingDevSecOps"
                }
            }
        }
        stage('OWASP Dependency-Check & vulnerability analysis'){
            steps{
                dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'owasp'
                dependencyCheckPublisher pattern: '**dependency-check-report.xml'
            }
        }
        stage('Sonar Quality Gate Scan'){
            steps{
                timeout(time: 2, unit: "MINUTES"){
                    waitForQualityGate abortPipeline: false
                }
            }
        }
        stage('Trivy File System Scan'){
            steps{
                sh "trivy fs --format table -o trivy-fs-report.html . "
            }
        }
        stage('Deployment Using Docker Compose'){
            steps{
                sh "docker-compose down"
                sh "docker-compose up -d"
                sleep 60
                sh "docker exec bf289ed90d07 mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray" 
            }
        }
    }
}
