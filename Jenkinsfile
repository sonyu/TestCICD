steps {
    sh 'echo "Hello World"'
    git url: 'https://github.com/sonyu/TestCICD.git', branch: 'main'
    mvn clean package
    sh 'docker build -t myapp .'
    sh 'docker run -p 8080:8080 myapp'
}