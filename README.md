# laravel sonarqube
Code coverage report for your laravel project with SonarQube


![Alt text](screenshot-1.png?raw=true "php Project 1")

![Alt text](screenshot-2.png?raw=true "php Project 2")


## Check OS bit:
 		uname -i

## Prerequisite Installations for SonarQube

1. Install JAVA JRE

		sudo apt-get update
		java -version — (check if java is not already installed)
		sudo apt-get install default-jre


2. Install MYSQL


3. Install SonarQube :
Create SonarQube database and user

		CREATE DATABASE sonar CHARACTER SET utf8 COLLATE utf8_general_ci;
		CREATE USER 'sonar' IDENTIFIED BY 'sonar';
		GRANT ALL ON sonar.* TO 'sonar'@'%' IDENTIFIED BY 'sonar';
		GRANT ALL ON sonar.* TO 'sonar'@'localhost' IDENTIFIED BY 'sonar';
		FLUSH PRIVILEGES;



3.1 Download & Unzip SonarQube Distribution


		wget http://dist.sonar.codehaus.org/sonarqube-${SONAR_VERSION}.zip
		unzip sonarqube-${SONAR_VERSION}.zip
		mv sonarqube-${SONAR_VERSION} /opt/sonar

 3.2 Edit and Configure sonar.properties


		sudo nano /opt/sonar/conf/sonar.properties
		sonar.jdbc.username=sonar
		sonar.jdbc.password=sonar
		sonar.jdbc.url=jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true&useConfigs=maxPerformance
		sonar.web.host=127.0.0.1
		sonar.web.context=/sonar
 		sonar.web.port=9000


3.3 Run SonarQube Server


		sudo /opt/sonar/bin/linux-x86-32/sonar.sh start



3.4 Install SonarQube Runner


		wget http://repo1.maven.org/maven2/org/codehaus/sonar/runner/sonar-runner-dist/2.4/sonar-runner-dist-${SONAR_RUNNER_VERSION}.zip

		unzip sonar-runner-dist-${SONAR_RUNNER_VERSION}.zip
		mv sonar-runner-${SONAR_RUNNER_VERSION} /opt/sonar-runner



 3.5 Edit and Configure sonar-runner.properties


		sudo  nano /opt/sonar-runner/conf/sonar-runner.properties
		sonar.host.url=http://localhost:9000/sonar
		sonar.jdbc.url=jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true&useConfigs=maxPerformance

		sonar.jdbc.username=sonar
		sonar.jdbc.password=sonar




## Install PHP Plugin for SonarQube

Click on administration->configuration anc check php is available in installed tab, elase go to available tab and search for php and once found, click on install button. Once installed you need to restart the sonarqube.



## Configure with your Laravel project

 Create a new file  [sonar-project.properties](sonar-project.properties) in root folder of laravel project.

	



## Now run following command

Run solar runner

 	sudo /opt/sonar-runner/bin/sonar-runner -e -X



## Securing SonarQube Installation

Change Password for Admin User

    	http://localhost:9000/sonar
    	Click on Log In
    	Login with credentials admin/admin.
    	After logging in Click on My Profile present as sub-menu under logged user name in top-right corner.
    	Change Password accordingly.
