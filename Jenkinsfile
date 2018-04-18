import groovy.json.JsonSlurper
import groovy.json.JsonOutput

pipeline {
    agent {
        label 'master'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    jira_call_url = "https://jira2.lgsvl.com/rest/api/2/search?jql=project%20%3D%20GLD4TV%20AND%20issuetype%20in%20%28%22CCC%20Task%22%2C%20%22Automated%20CCC%22%29%20AND%20status%20in%20%28Build%29%20AND%20summary%20%7E%20CCC%3A%20AND%20updated%20%3E%20startOfDay%28%29%20ORDER%20BY%20key%20ASC"
                    command = "curl -D- -u '${env.USER}:${env.PASSWORD}' -X GET -H 'Content-Type: application/json' " + jira_call_url + "  > json-temp.txt"
                    sh script: command
                    json_str = sh(name: "Run JQL Query2", script: 'cat json-temp.txt | grep ^{', returnStdout: true).trim()
                    json_obj = readJSON text: json_str
                    echo json_obj['expand']
                    json_obj['expand'] = "test,test1"
                    writeJSON file: "c.json" , json: json_obj
                }
            }
        }
        stage('Change') {
            steps {
                script {
                    json_read = readJSON file: "c.json"
                    echo json_read['expand']
                    /*
                    jql_str = "project = GLD4TV AND issuetype in (\"CCC Task\", \"Automated CCC\") AND status in (Screen, Approval, Integration, build) AND summary ~ CCC: ORDER BY key ASC";
                    writeFile(file: "out.txt", text: jql_str)
                    a = sh(script: "python -c 'import urllib;line = open(\"out.txt\").read().split(\"\\n\")[0];print(urllib.quote(line))'", returnStdout: true)
                    echo "Result: " + a
                    a = [:]
                    a['name'] = 'sunjoo'
                    a['age'] = 123
                    */
                    //echo JsonOutput.toJson(a)
                    //writeJSON(file:"var-json.txt", json: JsonSlurper.parseText(JsonOutput.toJson(a)))
                }
            }
        }
        stage('JSON Sample') {
            steps {
                script {
                    object = ["name":"Sunjoo Park", "company": "LG Electronics", "mail": "allessunjoo.park@lge.com"]
                    json_str = JsonOutput.toJson(object)
                    echo json_str
                    json_obj  = readJSON text: json_str
                    echo json_obj['name']
                    echo json_obj['company']
                    echo json_obj['mail']
                    writeJSON file: "json_out.txt", json: json_obj
                    sh 'cat json_out.txt'
                }
            }
        }
    }
}
