# BuildSignal Bamboo Plugin

Plugin for Atlassian Bamboo to record build status for use with external build status displays.

## Building
Install Atlassian's development kit.  
From the cloned project folder, run `atlas-package`

## Installation
Log in to Bamboo as an administrator and navigate to "Bamboo Administration > Manage add-ons"
Click the link "Upload add-on"
Upload the packaged jar plugin

## Configuration
The plugin requires to Bamboo Global Variables  
As a Bamboo administrator navigate to "Bamboo Administration > Global variables"  
Add `lights.clientId` and `lights.url` variables  
ClientID just needs to match the client id in the python client on your rasberry pi  
URL needs to match the AWS API Gateway URL for your lambda functions

## Notes
Only the primary job status is sent to the api.  Branch builds are not included.  
The "job id" sent is Bamboo's project key and plan key, concatenated with a separating dash "{Project}-{Plan}"  
This allows light configurations for all builds within a project by using a regex looking for "Project-.*"  

Failure to send the status only results in log output.  It will not impact the status of your builds.  