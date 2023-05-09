node{

	def buildNumber = BUILD_NUMBER
	stage("Git clone"){
		git url:'https://github.com/dinesh7040/java-web-app-docker.git',branch: 'master'
	}
	stage("Maven Clean Package"){
		def mavenHome= tool name: "Maven",type: "maven"
		 sh "${mavenHome}/bin/mvn clean package"
	}

	stage("Build Image"){
		 sh "docker build -t dockerhandson/java-web-app-docker:${buildNumber} ."
	}
	stage("Docker Login And Push"){
	    withCredentials([string(credentialsId: 'Dockerhubpwd', variable: 'Dockerhubpwd')]) {
	     sh "docker login -u dockerhandson -p ${Dockerhubpwd}"
    }
		 sh "docker push dockerhandson/java-web-app-docker:${buildNumber}"
	}
}
