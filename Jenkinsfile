pipeline {
    agent any
    stages {
			stage('Setup parameters') {
            steps {
                script { 
                    properties([
                        parameters([
                            choice(
                                choices: ['abc', 'def'], 
                                name: 'PARAMETER_01'
                            ),
                            booleanParam(
                                defaultValue: true, 
                                description: '', 
                                name: 'BOOLEAN'
                            ),
                            text(
                                defaultValue: '''
                                this is a multi-line 
                                string parameter example
                                ''', 
                                 name: 'MULTI-LINE-STRING'
                            ),
                            string(
                                defaultValue: 'whatever', 
                                name: 'TESTTHIS', 
                                trim: true
                            )
                        ])
                    ])
                }
            }
		}
    stage('Checkout code') {
            steps {
         	sh '''
    	    #!/bin/sh
    		echo "$PARAMETER_01"
    		echo "$TESTTHIS"
			git checkout "$TESTTHIS"
         	'''
            }
        }
	stage('Compile code') {
            steps {
         	sh '''
    	    #!/bin/sh
    		echo "$PARAMETER_01"
    		echo "$TESTTHIS"
			cd src
    		make help
    		make net
    		make build ARCH=x86-64-modern
         	'''
            }
        }
	stage('Empty') {
			steps {
         	sh '''
            	#!/bin/sh
    		echo "$PARAMETER_01"
         	'''
		}
	}

    }
}


