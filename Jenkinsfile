node {
   stage 'Checkout'

   git url: 'https://github.com/adriaandejonge/try-gradle/'
   def gradle = tool 'gradle'

   stage 'Build WAR'
   sh "${gradle}/bin/gradle build"
   sh "echo build war"
   sh "ls -al"
   
   stage 'Build Docker'
   sh "echo build docker"
   sh "ls build/libs/ -al"
   sh "wget https://get.docker.com/builds/Linux/x86_64/docker-1.9.1"
   sh "chmod +x docker-1.9.1"
   sh "mv docker-1.9.1 docker"
   sh "ls /var/run/"
   sh "./docker build -t adejonge/try-gradle ."
   sh "./docker push adejonge/try-gradle"
}
