@Library('FirstLib@us-0278') _

pipeline {
   agent any
   environment {
       TEST_VAR = "super"
   }
   stages {
       stage("first") {
           steps {
                script {
                    def foo = "foo" 
                    bat "echo Hallo from git, ${TEST_VAR}-${foo}!"
                }
                script {
                    def foo2 = "foo2" 
                    // bat "echo Hallo 2.0, ${TEST_VAR}-${foo}-${foo2}!" // fail
                    bat "echo Hallo from git 2.0, ${TEST_VAR}-${foo2}!"
                }
                script {
                    lib.SimpleHelloFromLib

                    // failed
                    // lib.SimpleHelloFromLib ''

                    // failed
                    // lib.SimpleHelloFromLib ""
                }
                script {
                    def foo3 = "DK3"
                    lib.HalloFromLib "${foo3}"
                }
                script {
                    lib.call 'DKcall'
                    lib.call ''
                }
           }
       }
   }
}