node {
   stage 'Checkout'

   git url: 'https://github.com/adriaandejonge/try-gradle/'
   def gradle = tool 'gradle'

   stage 'Build WAR'
   sh "${gradle}/bin/gradle build"

   stage 'Build Docker'
   sh "docker build -t adejonge/try-gradle ."
   
   stage 'Push to Docker Hub'
   sh "docker login -u YOURUSERNAME -p ??YOURPASSWORD?? -e YOUREMAIL"
   sh "docker push adejonge/try-gradle"

   stage 'Deploy to TST'
   sh "kubectl create -f k8s/pod-try-gradle.yaml"

}
