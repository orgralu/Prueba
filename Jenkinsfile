node {

stage('Checkout') {
git credentialsId: 'c45408eb-ed34-4ba3-9a7a-bfe9f98a60e4', url: 'https://github.com/orgralu/Prueba.git'
}

stage ('Restore Nuget') {
bat "dotnet restore "
}

stage('Clean') {
bat 'dotnet clean '
}

stage('Build') {
bat 'dotnet build --configuration Release'
}

//stage ('Test') {
//bat "dotnet test Presupuesto.Core.Domain.Test/Presupuesto.Core.Domain.Test.csproj --logger trx;LogFileName=unit_tests.trx"
//mstest testResultsFile:"**/*.trx", keepLongStdio: true
//}

stage ('Question') {
def userInput = input( 'Do you approve deployment?' )
[$class: 'TextParameterDefinition', defaultValue: 'uat', description: 'Environment', name: 'env']
echo ("Env: "+userInput)
}

stage('Publish') {
bat 'dotnet publish -c Release -o G:/ws/NetCore/EjemploJenkins'
}

stage('Report Email') {
emailext body: 'Se terminó de desplegar', subject: 'Test - Se termino de desplegar', to: 'bgonzalez@byasystems.com.co'
}

}
