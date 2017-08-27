#!/usr/bin/env groovy

// this will start an executor on a Jenkins agent with the docker label
pipeline {
  agent none

  parameters {
      string(name: 'applicationName', defaultValue: 'addition-operator', description: 'docker image name')
  }

  stages {

      // stage('Checkout from GitHub') {
      //   checkout scm
      // }

      stage("Create binaries") {
        agent {
          docker {
            image "golang:1.8.0-alpine"
            args '-v $PWD:/go/src/github.com/jgensler8/math-service --workdir /go/src/github.com/jgensler8/math-service'
          }
        }
        steps {
          sh "ls /go"
          sh "ls /go/src"
          sh "ls /go/src/github.com"
          sh "ls /go/src/github.com/jgensler8"
          sh "pwd"
          sh "env"
          sh "GOOS=linux GOARCH=amd64 go build ./${env.applicationName}"
          sh "ls"
          sh "ls ./${env.applicationName}"
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
