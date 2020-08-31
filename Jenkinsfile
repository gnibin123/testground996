pipeline {
  agent any
  stages {

  stage('Stopping Eradah Unittest server')

  {
    bat 'ssh administrator@192.168.75.168 "sc stop EAP_Eradah_Unittest"'
    bat 'python D:\\ims_ecs\\Python\\3.7.2\\Scripts\\ERA_UNIT_STOP.py'
  }

  stage('Build Eradahlib') {
    build returnStatus: true,
    job: 'Eradah_Unittest_EradahLib',
    propagate: true
    echo 'Eradahlib Completed'
  }

  stage('Build MYMT') {
    build returnStatus: true,
    job: 'MYMT_BANKS_3.7_ERA',
    propagate: true
  }
  
  
    stage('Starting Eradah Unittest server')

  {
    bat 'ssh administrator@192.168.75.168 "sc start EAP_Eradah_Unittest"'
    bat 'call D:\\ims_ecs\\Python\\3.7.2\\Scripts\\Eradah_Monitor.bat'
  }
  
 

}

}
