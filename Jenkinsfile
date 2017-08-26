#!/usr/bin/env groovy

// this will start an executor on a Jenkins agent with the docker label
pipeline {
  agent none

  parameters {
      string(name: 'APPLICATIONNAME', defaultValue: 'AdditionService', description: 'docker image name')
      string(name: 'GOPATH', defaultValue: '0.1.${env.BUILD_NUMBER}', description: 'docker image tag')
  }

  stages {

      // stage('Checkout from GitHub') {
      //   checkout scm
      // }
      
      stage("Create binaries") {
        agent { "golang:1.8.0-alpine" }
        step {
          sh "cd ${goPath} && GOOS=linux GOARCH=amd64 go build"
        }
      }

      // stage("Build container") {
      //   // From https://blog.nimbleci.com/2016/08/31/how-to-build-docker-images-automatically-with-jenkins-pipeline/
      //   docker.withRegistry('localhost', 'registry-creds') {
      //       stage "build"
      //       def app = docker.build "${applicationName}:${buildNumber}"
      //
      //       stage "publish"
      //       // app.push 'latest'
      //       app.push "${commit_id}"
      //   }
      // }
  }
}
