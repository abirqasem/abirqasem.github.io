# Google Cloud Platform



### Vocabulary, organization and starting point
1. Your code belongs to a project. The code body can be in many different languages and can be in many different files. They all share the same project properties like credentials and API access etc.
2. Each project has a name, id and a number
3. You enable APIs for a project.
4. You get credentials for an API.
5. API has usage quota.

### [Web console](https://console.cloud.google.com/)
>The view is project specific and therefore it defaults to a project (most likely the last project used) >but a dropdown is available top left to move to another project.
>Terms used in the web to about Google Cloud Platform : cloud console, google cloud platform, gcp*



### Links/Tips
1. [List all the services (APIs)]( https://console.cloud.google.com/apis/library)
You can `curl https://www.googleapis.com/discovery/v1/apis` to get a JSON. 
2. [Create and view credentials]( https://console.cloud.google.com/apis/credentials)
3. [API documentation](https://console.cloud.google.com/apis/library) then choose a card for the service you want . They usually have a Web demo with a button TRY THIS API
4. [Usage quota](https://console.cloud.google.com/apis/dashboard) 
*This will default to a project. Choose a project you want from the drop down, select an API from the list and then select quota for that API*
5. CLI: [gcloud](gcloud_basics)
6. [Client libraries](https://developers.google.com/api-client-library/)
