pipeline {
    agent any

    triggers {
        cron('H/10 * * * *')
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Tomcat (/webapp)') {
            steps {
                sh '''
                echo "Deploying application to Tomcat..."

                mkdir -p /usr/local/tomcat/webapps/webapp
                rm -rf /usr/local/tomcat/webapps/webapp/*

                cp -r 404.html LICENSE.txt READ-ME.txt README.md \
                      about.html charity-organization-website-template.jpg \
                      contact.html css donation.html event.html feature.html \
                      img index.html js lib scss service.html team.html testimonial.html \
                      /usr/local/tomcat/webapps/webapp/

                echo "Deployment successful"
                '''
            }
        }
    }
}
