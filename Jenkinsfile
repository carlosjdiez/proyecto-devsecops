pipeline {
    agent any
    stages {
        stage('Descargar Código') {
            steps {
                echo 'Clonando el repositorio desde GitHub...'
                // Cambia esta URL por la tuya
                git branch: 'desarrollo', url: 'https://github.com/carlosjdiez/proyecto-devsecops.git'
            }
        }
        stage('Construir Imagen Docker (Build)') {
            steps {
                echo 'Construyendo el contenedor seguro...'
                sh 'docker build -t mi-app-segura:latest .'
            }
	}
        stage('Escaneo de Seguridad (Trivy)') {
            steps {
                echo 'Escanenado vulnerabilidades críticas...'
		sh 'docker run --rm -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/aquasecurity/trivy:latest image --exit-code 1 --severity CRITICAL mi-app-segura:latest'
	    }
	}
    }
}
