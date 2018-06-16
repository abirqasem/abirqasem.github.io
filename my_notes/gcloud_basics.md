#GCloud Basics



Google Cloud Project Management with gcloud CLI

Who am I?
gcloud auth list
How to change who I am?
gcloud config set account `ACCOUNT`
gcloud auth login

What are my projects?
gcloud projects list
What is my active project?
gcloud config list
How to change an active project?
For now: gcloud config set project `Project id`
How to deploy a project?
Caution: Once deployed you lose your previous version. There are no easy (obvious) undos. So please be very careful, especially with deployment of production system

	Test to see if you are in the right local directory in your machine or cloud 9.
	dev_appserver.py .
	And then open the app in a browser.
	Are you sure that is the latest version? If yes then
gcloud app deploy

How to download the running apps source code? This is good tool. You can get the guaranteed running code of your app (and you can get the code of older versions too. Unlike GAS

First try
appcfg.py -A `YOUR_PROJECT_ID` download_app `directory with full path of where you want the code`

	If appcfg.py is not in your path do this:

which gcloud

	This will give you the path where gcloud is installed
cd to that path and then further to /google-cloud-sdk/platform/google_appengine/

	ls and you you will see appcfg.py
	Run the command now.

How to see enabled APIs?
gcloud services list // enabled ones
gcloud services list --available // all available

How to enable or disable API?
gcloud services disable name
gcloud services enable name

Verify using
https://console.cloud.google.com/apis/dashboard?project=clspamdetector&duration=PT1H
Also gcloud services list will show you





1. `gcloud config list` will show you the google account and the

which project

switch project

switch account


local host will use the same project

gcloud app deploy
make sure you are in the right project folder

download running app source code directly
