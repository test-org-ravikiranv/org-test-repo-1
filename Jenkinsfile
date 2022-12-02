pipeline 
{
	agent any
	tools{ maven "M3"}
	environment
	{
	DOCKERHUB_CREDENTIALS= credentials('DockerHub_Cred')
	}
	stages
	{
	stage("Git Checkout")
	{   
		steps
		{
		git branch: 'rk-branch', credentialsId: 'GitHub_Cred', url: 'https://github.com/ravikirankiran097/Spring-PetClinic.git'
		echo 'Git Checkout Completed'
		}
	}
	stage("Mvn Build")
	{   
		steps
		{
		sh 'mvn -Dmaven.test.failure.ignore=true clean install'
		echo 'Mvn Build Completed'
		}
	}
	stage('Build Docker Image')
	{ 
		steps
		{
		sh 'docker build -t ravikirankiran097/spring_petclinic:$BUILD_NUMBER .'
		echo 'Build Image Completed'
		}
	}
	stage('Login to Docker Hub')
	{ 
		steps
		{
		sh 'docker tag ravikirankiran097/spring_petclinic:$BUILD_NUMBER ravikirankiran097/spring_petclinic:$BUILD_NUMBER'
		sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
		echo 'Login Completed'
		}
	}
	stage('Push Image to Docker Hub')
	{ 
		steps
		{
		sh 'docker push ravikirankiran097/spring_petclinic:$BUILD_NUMBER'
		echo 'Push Image Completed'
		}
	}
	stage('Clean Docker Image')
	{ 
		steps
		{
		sh 'docker rmi ravikirankiran097/spring_petclinic:$BUILD_NUMBER'
		echo 'Cleanup Completed'
		}
	}
	}

//stages
 
	post
	{
	always
	{
		sh 'docker logout'
	}
	}
}

//pipeline
