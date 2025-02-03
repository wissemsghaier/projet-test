pipeline {
    agent any  // Exécute la pipeline sur n'importe quel agent disponible

    stages {
        

        stage('Build') {
            steps {
                echo "🏗️ Construction du projet Java avec Maven..."
                sh 'mvn clean package -DskipTests'  // Compile et génère le .jar
                archive 'target/*.jar'
            }
        }

    }
}































// pipeline {
//   agent any

//   stages {

//     stage('Build Artifact - Maven') {
//       steps {
//         sh "mvn clean package -DskipTests=true"
//         archive 'target/*.jar'
//       }
//     }
//     stage('Vulnerability Scan - Docker ') {
//       steps {
//         sh "mvn dependency-check:check"
//       }
//       post {
//         always {
//           dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'
//         }
//       }
//     }

//     stage('Vulnerability Scan - Docker') {
//       steps {
//         parallel(
//           "Dependency Scan": {
//             sh "mvn dependency-check:check"
//           },
//           "Trivy Scan": {
//             sh "bash trivy-docker-image-scan.sh"
//           }
//         )
//       }
//     }

//     stage('Unit Tests - JUnit and Jacoco') {
//       steps {
//         sh "mvn test"
//       }
//       post {
//         always {
//           junit 'target/surefire-reports/*.xml'
//           jacoco execPattern: 'target/jacoco.exec'
//         }
//       }
//     }
//     stage('Mutation Tests - PIT') {
//       steps {
//         sh "mvn org.pitest:pitest-maven:mutationCoverage"
//       }
//       post {
//         always {
//           pitmutation mutationStatsFile: '**/target/pit-reports/**/mutations.xml'
//         }
//       }
//     } 


//     stage('SonarQube - SAST') {
//       steps {
//         withSonarQubeEnv('sonarqube') {
//           sh "mvn sonar:sonar \
//               -Dsonar.projectKey=devsecops-numeric-application \
//               -Dsonar.host.url=<sonarqube-server-url>"
//       }
//         timeout(time: 2, unit: 'MINUTES') {
//           script {
//             waitForQualityGate abortPipeline: true
//           }
//         }
//       }
//     }

//     stage('Docker image build and push') {
//       steps {
//         sh 'docker build -t docker-registry:5000/java-app:latest .'
//         sh 'docker push docker-registry:5000/java-app:latest'
//        }
//      }
//     stage('Kubernetes Deployment - DEV') {
//       steps {
        
//         sh "kubectl apply -f k8s_deployment_service.yaml"
//       }
//     }

//     post {
//     always {
//       junit 'target/surefire-reports/*.xml'
//       jacoco execPattern: 'target/jacoco.exec'
//       pitmutation mutationStatsFile: '**/target/pit-reports/**/mutations.xml'
//       dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'
//     }


//    }
//  }

