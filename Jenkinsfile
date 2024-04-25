node('springpetclinic') {
    stage('git') {
        git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
    }
    stage('build') {
        sh '''sudo sh -c \'echo 1 >  /proc/sys/vm/drop_caches\'
        sleep 10
        mvn clean package -DskipTests
        sleep 10
        sudo sh -c \'echo 1 >  /proc/sys/vm/drop_caches\''''
    }
    stage('Archive artifacts') {
        archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
    }
}

