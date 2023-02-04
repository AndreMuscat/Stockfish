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
                                defaultValue: 'scriptcrunch', 
                                name: 'STRING-PARAMETER', 
                                trim: true
                            )
                        ])
                    ])
                }
            }
		}
    stage('Checkout') {
		steps {
         	sh '''
            	#!/bin/sh
    		echo "$STRING-PARAMETER"
			git checkout "$STRING-PARAMETER"
    		echo "$STRING-PARAMETER"
         	'''
		}
	}		
    stage('Compile code') {
            steps {
         	sh '''
    	    #!/bin/sh
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


