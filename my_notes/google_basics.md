# Google Cloud Platform

### Vocabulary, organization and starting point
Your code belongs to a project. The code body can be in many different languages and can be in many different files. They all share the same project properties like credentials and API access etc.
Each project has a name, id and a number
You enable APIs for a project.
You get credentials for an API.
API has usage quota.
General Starting point: https://console.cloud.google.com/
The view is project specific and therefore it defaults to a project (most likely the last project used) but a dropdown is available top left to move to another project.
Terms used in the web to about Google Cloud Platform : cloud console, google cloud platform, gcp

### Links/Tips
find all the services (APIs) https://console.cloud.google.com/apis/library
Or via code: GET https://www.googleapis.com/discovery/v1/apis
Create and view credentials https://console.cloud.google.com/apis/credentials
Find the API documentation Go to https://console.cloud.google.com/apis/library then choose a card for the service you want . They usually have a Web demo with a button TRY THIS API
Usage quota https://console.cloud.google.com/apis/dashboard (will default to a project)
Choose the right project from the drop down
Then select an API from the list
Then select quota
Add a project  dropdown is available top left console
Manage projects  dropdown is available top left console

CLI: gcloud (see my link on it)
Client libraries: https://developers.google.com/api-client-library/
