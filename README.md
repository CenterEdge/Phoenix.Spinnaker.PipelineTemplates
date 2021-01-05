V2 Pipeline Templates
----
Quick Steps For Updating And Testing
Update the template, save to Spinnaker using: spin pipeline-templates save --file <path to pipeline json>
Run in spinnaker, verify working correctly
Update repo
More information can be found at https://www.spinnaker.io/guides/spin/pipeline-templates/

You can also convert an existing pipeline into a template:

Create a pipeline in Spinnaker you wish to use as a starting point for the template
Get the pipeline's JSON file: spin pipeline get --name <pipelineName> --application <appName> Alternatively, you can save the json directly to a file: spin pipeline get --name <pipelineName> --application <appName> | tee new_template.txt
Edit the json to a template:
Add a reference to the pipeline templates schema "schema": "v2"
Add a variables section
"variables": [ { "type": "", "defaultValue": , "description": "", "name": "" }, { "type": "", "defaultValue": , "description": "", "name": "" } ]```

Use template variables in place of hard coded ones by using ${ templateVariables.<varName> }
Save the template to be usable: spin pipeline-templates save --file my_template.txt
Verify pipeline works in spinnaker
More information can be found at https://www.spinnaker.io/guides/user/pipeline/pipeline-templates/create/

Kubernetes Manifest Templates
----
Templates using kv2 are deployed via manifest files. Some kubernetes documentation, for use with the manifests, is located here: https://v1-18.docs.kubernetes.io/docs/reference/generated/kubernetes-api/v1.18/#-strong-api-overview-strong-