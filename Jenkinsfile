node {
    stage('Checkout git repo') {
      git branch: 'master', url: params.GitRespository
    }
    stage('build') {
        sh(script: "dotnet pack -c Release /p:NuspecFile=CrimsonDev.Gameteki.StyleCop.Rules.nuspec /p:Version=1.0.0.${BUILD_NUMBER}", returnStdout: true)
    }
    stage('deploy') {
    }
}