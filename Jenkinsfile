pipeline{
	agent any 
	stages{
		stage("Building JAR File..."){
			steps{
				echo "Cleaning Target Directory"
				bat 'mvn clean'
				echo "Running all Integration Test"
				bat 'mvn verify'
			}
		}
		stage("Scanning for Code Quality Check..."){
			steps{
				echo "Starting..."
				bat 'mvn sonar:sonar'
				echo "ending of quality check..."
			}
		}
	}
}