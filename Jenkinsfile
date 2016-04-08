node {
   stage 'Checkout'

   git url: 'https://github.com/adriaandejonge/try-gradle/'
   def gradle = tool 'gradle'

   stage 'Build WAR'
   sh "${gradle}/bin/gradle build"

   stage 'Build Docker'
   sh "wget https://get.docker.com/builds/Linux/x86_64/docker-1.9.1"
   sh "chmod +x docker-1.9.1"
   sh "mv docker-1.9.1 docker"
   sh "ls /var/run/"
   sh "./docker build -t adejonge/try-gradle ."
   sh "./docker push adejonge/try-gradle"

   stage 'Deploy to TST'
   sh "wget https://storage.googleapis.com/kubernetes-release/release/v1.2.0/bin/linux/amd64/kubectl"
   sh "chmod +x kubectl"
   sh "./kubectl create -f k8s/pod-try-gradle.yaml"

}
