def changeLog(){
  gitChangelog returnType: 'STRING',
  from: [type: 'REF', value: ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}],
  to: [type: 'REF', value: 'master'],
  template: """
<h1> Git Changelog changelog </h1>

<p>
Changelog of Git Changelog.
</p>

{{#tags}}
<h2> {{name}} </h2>
 {{#issues}}
  {{#hasIssue}}
   {{#hasLink}}
<h2> {{name}} <a href="{{link}}">{{issue}}</a> {{title}} </h2>
   {{/hasLink}}
   {{^hasLink}}
<h2> {{name}} {{issue}} {{title}} </h2>
   {{/hasLink}}
  {{/hasIssue}}
  {{^hasIssue}}
<h2> {{name}} </h2>
  {{/hasIssue}}


   {{#commits}}
<a href="https://github.com/tomasbjerre/git-changelog-lib/commit/{{hash}}">{{hash}}</a> {{authorName}} <i>{{commitTime}}</i>
<p>
<h3>{{{messageTitle}}}</h3>

{{#messageBodyItems}}
 <li> {{.}}</li> 
{{/messageBodyItems}}
</p>


  {{/commits}}

 {{/issues}}
{{/tags}}
"""

}

pipeline{
	agent any
	environment {
        NAME = "test"
        WORKDIR = pwd()
	}
	stages {
		stage("First Stage") {
            steps{
                echo "Current commit: ${env.GIT_COMMIT} (build ${BUILD_NUMBER})"
                echo "Commit used in last build: ${env.GIT_PREVIOUS_COMMIT}"
                echo "Commit used in last successful build: ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}"

                gitChangelog returnType: 'STRING',
                from: [type: 'REF', value: 'git-changelog-1.50'],
                to: [type: 'REF', value: 'master'],

                echo changelogString
            }
		}
    }
    post {
        failure {
            echo "fail"
        }
        success {
            echo "success"
        }
    }
}