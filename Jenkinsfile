pipeline {
	agent { label 'Java' }
 
	stages {
		stage ('STAGE 1') {
			steps {
				echo 'Building JAVA project'
                		sh '''
                			set +x
                			if [[ -d "JAVA1" ]];then
                				cd JAVA1 && git pull
                        			mvn clean install
                			else
                				git clone https://github.com/Anusha1913/JAVA1.git
                  				cd JAVA1
                  				mvn install
                  				echo "Build Successful"
                				sh 'sleep 30'
						fi
				'''
			}	
		}
		stage ('STAGE 2') {
			steps {
				echo "Building C Projects"
                sh '''
                set +x
                if [[ -d "c_programs" ]];then
                   cd c_programs && git pull
                   make
                else
                   git clone https://github.com/Anusha1913/c_programs.git
                   cd c_programs
                   make
                fi
                if [[ -x "./ABC.exe" ]];then
                   echo "Buid Sucess"
                else
                   echo "Build Failed"
                fi
                sleep 10
                '''
			}	
		}
		
	}
}
