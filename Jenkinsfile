#!groovy
@Library('roboshop-shared-library') _

// responsibility to pass what type of application and component is this to pipeline deicssion

def configMap = [
    application: "nodejsVm",
    component: "catalogue"
]
if( ! env.BRANCH_NAME.equalsIgnoreCase('main')){
    pipelineDecision.decidePipeline(configMap)
}
else{
    echo "This is PRODUCTION, deal with CR process"
}