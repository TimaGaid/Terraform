#!/usr/bin/env groovy

def goImage = "golang:1.20rc3-bullseye"

properties([
  parameters([
    booleanParam(name: 'goBuild', defaultValue: false, description: 'this is go builderka')
  ])
])

pipeline {
  agent any {
    println("<=============== Start of pipeline ===============>")

    timestamps {
      stage("checkout scm"){
        checkout scm
      }
      stage("build go"){
        try{
          if (params.goBuild == true){
            timeout(time: 5, utils: 'MINUTES'){
              goImage.inside{
                dir (""){
                  sh "go install"
                }
              }
            }
          }else{
            println('Go build was skipd')
          }
        }catch{
          println()
        }
      }
    }
  }
  post{
    always{
      println("<=============== End of pipeline ===============>")
    }
  }
}