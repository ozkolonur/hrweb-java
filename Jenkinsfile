node 
   stage 'checkout'

   // Checkout code
   git url: 'https://github.com/ozkolonur/hrweb-java'

   // Get the maven
   def mvnHome = tool 'mvn'

   stage 'build'
   // get Maven
   sh "${mvnHome}/bin/mvn versions:set -DnewVersion=${env.BUILD_NUMBER}"
   sh "${mvnHome}/bin/mvn package"

   stage 'test'
   parallel 'test': {
     sh "echo testing"
   }, 'verify': {
     sh "echo verify"
   }

   stage 'archive'
   archive 'target/*.jar'
}
