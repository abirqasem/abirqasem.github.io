#gcloud cheatsheet



`gcloud` is a command line tool to manage google cloud platform projects. 

### Identiy and Projects

**Who am I?**
>`gcloud auth list`

**How to change who I am?**

>`gcloud config set account your gmail`

> If needed 
>
>`gcloud auth login`

**List my projects**
>`gcloud projects list`

**What is my active project?**
>`gcloud config list`

**How to change an active project?**

>`gcloud config set project project id`

### App Management

#### Deployment
**Caution**: 
>> Once deployed you lose your previous version. There are no easy (obvious) undos. So please be very
>> careful, especially with deployment of production system

_Always_ check if you are in the right local directory in your machine or cloud 9.

`dev_appserver.py .`
	 
Open the app in a browser.
	 **Are you sure that is the latest version?** 
	 If yes then `gcloud app deploy`

#### Downloading the running apps source code 
This is very useful because you can always have access to actual code that is running as your app (you can get the code of older versions too), no matter wherever you are (say you are in a cafe and do not have the desktop). 
 
>The command is 

`appcfg.py -A YOUR_PROJECT_ID download_app DESTINATION_DIRECTORY`

If `appcfg.py` is not in your path, find out where `gcloud` is by `which gcloud`

> This will give you the path where `gcloud` is installed
`cd` to that path and then further to `/google-cloud-sdk/platform/google_appengine/`

`ls` and you you will see `appcfg.py`

>>_Run the command now._

### API manangement

**How to see enabled APIs?**
`gcloud services list` // show me the enabled ones

`gcloud services list --available` // show me all available APIS

**How to enable or disable API?**

`gcloud services disable APi_NAME`

`gcloud services enable APIN_NAME`

Youc can verify the action using  [console](https://console.cloud.google.com/apis/dashboard)
or just  `gcloud services list` 

Some useful [Google Cloud Basics](google_basics)


