/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'ruby:3.3.6-alpine3.20' } }
    stages {
        stage('Build') {
            steps {
                sh 'ruby --version' // Verify Ruby version
            }
        }
        stage('Test Ruby Code') {
            steps {
                // Run the Ruby script inline
                script {
                    writeFile file: 'test_script.rb', text: '''
def sum(a, b)
  return a + b
end

result = sum(1, 2)
puts "Sum of 1 and 2 is: #{result}"
exit result == 3 ? 0 : 1 # Exit with success if the test passes
'''
                    sh 'ruby test_script.rb'
                }
            }
        }
    }
}
