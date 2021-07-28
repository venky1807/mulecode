pipeline {
	agent any
	stages {
		stage('Build Application') {
			steps {
				bat 'mvn clean install'
			}
		}
		stage('Deploy OnPremise') {
			steps {
				echo 'Deploying mule project due to the latest code commit….'
				echo 'Deploying to the configured environment….'
				bat 'mvn clean deploy -DmuleDeploy -DskipTests -Dmule.version=4.3.0 -Danypoint.username=venky210721 -Danypoint.password=Reddy@1357 -Dtarget=onprem -Dtarget.type=server -Denv=Sandbox -Dappname=Jenkins-poc'
			}
		}
	}
	post {
    failure {
        mail to: 'venkateshwar.guda@apisero.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
    }
     success {
        mail to: 'venkateshwar.guda@apisero.com',
             subject: "Successful Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
    }
    }
}