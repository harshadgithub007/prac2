pipeline {
    agent {
        label 'jai_mahakaal'
    }
    stages {
        stage ('git_checkout') {
            steps {
                # git url
            }
        }
        stage ('create_env') {
            steps {
                sh 'python3 -m venv venv'
            }
        }
        stage ('start_env') {
            steps {
                sh '. venv/bin/activate'
            }
        }
        stage ('install_dep') {
            steps {
                sh 'pip3 install -r requirement.txt'
            }
        }
        stage ('install_test_dep') {
            steps {
                sh 'pip3 install -r text.txt'
            }
        }
        stage ('run_test_cases') {
            steps {
                sh 'python3 -m unittest discover'
            }
        }
        stage ('build_python_application') {
            steps {
                sh 'python3 app.py sdist'
            }
        }
    }
    post {
        success {
            ArchiveArtifact '*/tar.gz'
            sh 'aws s3 cp *.tar.gz s3://my_bucket_name/python_archive_folder/'
        }
    }
}
