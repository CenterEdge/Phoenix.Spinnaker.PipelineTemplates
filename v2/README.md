# V2 Pipeline Templates

Quick Steps For Updating And Testing
----
1. Update the template, save to Spinnaker using:
	```spin pipeline-templates save --file <path to pipeline json>```
2. Run in spinnaker, verify working correctly
3. Update repo

More information can be found at https://www.spinnaker.io/guides/spin/pipeline-templates/

You can also convert an existing pipeline into a template:
1. Create a pipeline in Spinnaker you wish to use as a starting point for the template
2. Get the pipeline's JSON file:
	```spin pipeline get --name <pipelineName> --application <appName>```
	Alternatively, you can save the json directly to a file: ```spin pipeline get --name <pipelineName> --application <appName> | tee new_template.txt```
3. Edit the json to a template:
   * Add a reference to the pipeline templates schema ```"schema": "v2"```
   * Add a variables section
     ```json
"variables": [
  {
    "type": "<type>",
    "defaultValue": <defaultValue>,
    "description": "<some description>",
    "name": "<name of this variable>"
  },
  {
    "type": "<type>",
    "defaultValue": <defaultValue>,
    "description": "<some description>",
    "name": "<name of this variable>"
  }
]```
   * Use template variables in place of hard coded ones by using ```${ templateVariables.<varName> }```
4. Save the template to be usable: ```spin pipeline-templates save --file my_template.txt```
5. Verify pipeline works in spinnaker

More information can be found at https://www.spinnaker.io/guides/user/pipeline/pipeline-templates/create/ 