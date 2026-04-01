// pipeline {
//     agent any
//     stages {
//         stage('Hello') {
//             steps {
//                 echo 'Hello World from Jenkins 🚀'
//             }
//         }
//         stage('Hello1') {
//             steps {
//                 echo 'Hello World from Jenkins 🚀'
//             }
//         }
//     }
// }
pipeline {
    agent any

    environment {
        DB_HOST = 'db'
        DB_NAME = 'mydb'
        DB_USER = 'admin'
        DB_PASSWORD = 'admin123'
    }

    stages {
        stage('Install PostgreSQL Client') {
            steps {
                sh '''
                apt-get update
                apt-get install -y postgresql-client
                '''
            }
        }

            steps {
        sh '''
        PGPASSWORD=$DB_PASSWORD psql -h $DB_HOST -U $DB_USER -d $DB_NAME -c "
        CREATE TABLE IF NOT EXISTS employee (
            id SERIAL PRIMARY KEY,
            name VARCHAR(100),
            role VARCHAR(50)
        );
        "
        '''
    }
    }
}