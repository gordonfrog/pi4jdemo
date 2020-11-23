node {

    /**
     * pi4jdemo's Jenkins pipeline stage definitions for NATIVE (non-Docker) deployments.
     */

    // Clone the project from its Git SCM source.
    stage ("Git Clone") {
        git 'https://github.com/gordonfrog/pi4jdemo.git'
    }
   
    // Stop the prior deployment if necessary
    stage("Stop existing process") {
        sh 'lsof -n -i4TCP:8001 | grep LISTEN | awk \'{ print $2 }\' | xargs kill | true'
    }

    // Compile and test the application.
    stage ("Compile and Test") {
        sh "mvn clean package"
    }

    // Run the application
    stage("Run Application") {
        sh 'nohup mvn spring-boot:run &'
        sh "echo 'A running pi4jdemo app should soon be available for remote debugging on port 8001.'"
    }
    
}