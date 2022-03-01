@Library('FirstLib@us-0278') _

pipeline {

   agent any

   environment {
       TEST_VAR = "super" // you can't change it
       TEST_VAR_UNCHANGEABLE = "You can't change this var!"
   }

   stages {
       stage("first") {
           steps {
                script {
                    def foo = "foo" 
                    bat "echo Hallo from git, ${TEST_VAR}-${foo}!"
                    bat "echo Hallo from git, ${env.TEST_VAR_UNCHANGEABLE}-${foo}!"

                    TEST_VAR = "CHANGED!"
                    env.TEST_VAR_UNCHANGEABLE = "Trying to change..."
                }
                script {                    
                    // failed
                    // bat "echo Hallo 2.0, ${TEST_VAR}-${foo}-${foo2}!"

                    def foo2 = "foo2"
                    bat "echo Hallo from git 2.0, and TEST_VAR: ${TEST_VAR}-${foo2}!"
                    bat "echo Hallo from git 2.0, and TEST_VAR_UNCHANGEABLE: ${TEST_VAR_UNCHANGEABLE}-${foo2}!"
                }
                // script {
                    // failed
                    // lib.SimpleHelloFromLib

                    // failed
                    // lib.SimpleHelloFromLib ''

                    // failed
                    // lib.SimpleHelloFromLib ""
                // }
                script {
                    def foo3 = "DK3"
                    lib.HalloFromLib "${foo3}"
                    
                    // failed
                    // def foo3 = 'DK4'
                    // failed
                    // lib.HalloFromLib '${foo3}'
                }
                script {
                    lib.call 'DKcall1'
                    lib.call "DKcall2"
                    lib.call ''
                }
           }
       }
   }
}