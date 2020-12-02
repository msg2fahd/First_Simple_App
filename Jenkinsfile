pipeline{
	agent any 
	 environment { 
 EMAIL_RECIPIENTS = '5mo6tx@gmail.com'
 }
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
				// echo "dmfdfcd"
				// echo "ewjgfygdbs"
				
			}
		}
	}
	 post {
 success {
 sendEmail("Successful")
 }
 failure {
 sendEmail("Failed")
 }
 }
}

echo "CHANGED FILES LOG."
 @NonCPS
 def getchangedfile(){
 	def updatestring =""
 def changeLogSets = currentBuild.changeSets
for (int i = 0; i < changeLogSets.size(); i++) {
    def entries = changeLogSets[i].items
    for (int j = 0; j < entries.length; j++) {
        def entry = entries[j]
        //echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
        def files = new ArrayList(entry.affectedFiles)
        for (int k = 0; k < files.size(); k++) {
            def file = files[k]
            updatestring += "->  ${file.editType.name} -  ${file.path} \n"
        }
    }
}
 if (!updatestring) {
 changeString = " - No new changes"
 }
 return changeString
}
def sendEmail(status) {
 mail (
 to: "$EMAIL_RECIPIENTS", 
 subject: "Build $BUILD_NUMBER - " + status + " ($JOB_NAME)", 
 body: "Changes:\n " + getchangedfile()  + "\n")
}
// def getChangeString() {
//  MAX_MSG_LEN = 100
//  def changeString = ""

 

//  echo "Gathering SCM changes"
//  def changeLogSets = currentBuild.changeSets
//  echo "this is the ${changeLogSets} file "
//  for (int i = 0; i < changeLogSets.size(); i++) {
//  def entries = changeLogSets[i].items
//  for (int j = 0; j < entries.length; j++) {
//  def entry = entries[j]
//  truncated_msg = entry.msg.take(MAX_MSG_LEN)
//  changeString += " - ${truncated_msg} [${entry.author}]\n"
//  }
//  }

 


// }


//====================================================================================================
// pipeline {
//  agent any

 

//  environment { 
//  EMAIL_RECIPIENTS = 'sheela2997@gmail.com'
//  }

 

//  stages {
//  stage('Build') {
//  steps {
//  echo 'Building..'
//  }
//  }
//  stage('Test') {
//  steps {
//  echo 'Testing..'
//  }
//  }
//  stage('Deploy') {
//  steps {
//  echo 'Deploying....'
//  }
//  }
//  }
//  post {
//  success {
//  sendEmail("Successful")
//  }
//  failure {
//  sendEmail("Failed")
//  }
//  }
// }

 

// @NonCPS
// def getChangeString() {
//  MAX_MSG_LEN = 100
//  def changeString = ""

 

//  echo "Gathering SCM changes"
//  def changeLogSets = currentBuild.changeSets
//  for (int i = 0; i < changeLogSets.size(); i++) {
//  def entries = changeLogSets[i].items
//  for (int j = 0; j < entries.length; j++) {
//  def entry = entries[j]
//  truncated_msg = entry.msg.take(MAX_MSG_LEN)
//  changeString += " - ${truncated_msg} [${entry.author}]\n"
//  }
//  }

 

//  if (!changeString) {
//  changeString = " - No new changes"
//  }
//  return changeString
// }

 

// def sendEmail(status) {
//  mail (
//  to: "$EMAIL_RECIPIENTS", 
//  subject: "Build $BUILD_NUMBER - " + status + " ($JOB_NAME)", 
//  body: "Changes:\n " + getChangeString() + "\n\n Check console output at: $BUILD_URL/console" + "\n")
// // }