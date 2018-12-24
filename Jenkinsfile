node {
    stage('Checkout git repo') {
        checkout scm
    }

    stage('build') {
        sh(script: "sed -i 's/%VERSION%/1.0.0.${BUILD_NUMBER}/g' *.nuspec")
        sh(script: "sed -i 's/%VERSION%/1.0.0.${BUILD_NUMBER}/g' *.props")
        sh(script: "dotnet pack -c Release /p:NuspecFile=CrimsonDev.Gameteki.StyleCop.Rules.nuspec /p:Version=1.0.0.${BUILD_NUMBER}", returnStdout: true)
    }

    stage('deploy') {
        withCredentials([string(credentialsId: 'nuget_apikey', variable: 'NUGET_APIKEY')]) {
            sh(script: "dotnet nuget push CrimsonDev.Gameteki.StyleCop.Rules.nupkg -k ${NUGET_APIKEY} -s https://api.nuget.org/v3/index.json")
        }
    }
}