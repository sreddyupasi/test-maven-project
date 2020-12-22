@Library('test-pipeline-library') _
import com.example.*

def pipeline = new Pipeline(this, "config.yml")
node {
    try {
        stage ('prerequisites'){
            pipeline.execute()
        }
        stage('build'){
            pipeline.codeBuild()
        }
        stage('database'){
            pipeline.codeDBConfig()
        }
        stage('deploy'){
            pipeline.codeDeploy()
        }
        stage('testing'){
            pipeline.codeTest()
        }
    } catch (err){
        currentBuild.result = "FAILED"
        throw err
    }
     finally {
        pipeline.notifyBuild()
    }
}
