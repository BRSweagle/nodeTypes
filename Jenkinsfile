pipeline {
  agent any
  stages {
    stage('Config') {
      parallel {
        stage('Config') {
          steps {
            SWEAGLEExport(actionName: 'GetConfig', mdsName: 'MDSName', fileLocation: 'FileLocation', exporter: 'all', format: 'json')
            SWEAGLESnapshot(actionName: 'Snapshot', mdsName: 'MDSName', description: 'SnapshotConfig', tag: 'Version/Build')
            SWEAGLEUpload(actionName: 'UploadConfig', fileLocation: 'FileLocation', format: 'json', nodePath: 'Dimension,Node,Node1', description: 'Description', tag: 'BuildVersion')
            SWEAGLEValidate(actionName: 'Validation', mdsName: 'MDSName', errMax: 1, retryCount: 3, retryInterval: 3, showResults: true)
          }
        }
        stage('Shell') {
          steps {
            sh 'cd /Users/boondock/documents'
          }
        }
      }
    }
  }
}