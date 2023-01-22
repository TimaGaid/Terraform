#!/usr/bin/env groovy

pipeline {
  agent any
    stages{
      stage("build go"){
        steps {
          script {
            def goImage = docker.build ('golang:1.20rc3-bullseye')
              goImage.inside{
                dir ("/home/jenkins/"){
                  sh "go install"
              }
            }
          }
        }
      }
    }
  }
// def goImage = "golang:latest"

// properties([
//   parameters([
//     booleanParam(name: 'goBuild', defaultValue: false, description: 'this is go builderka')
//   ])
// ])

// pipeline {
//   agent any {
//     println("<=============== Start of pipeline ===============>")

//     timestamps {
//       stage("checkout scm"){
//         checkout scm
//       }
//       stage("build go"){
//         try{
//             timeout(time: 5, utils: 'MINUTES'){
//               goImage.inside{
//                 dir ("/home/ubuntu/jenkins"){
//                   sh "go install"
//                 }
//               }
//             }
//           }else{
//             println('Go build was skipd')
//           }
//         }catch{
//           println()
//         }
//       }
//     }
//   }
//   post{
//     always{
//       println("<=============== End of pipeline ===============>")
//     }
//   }