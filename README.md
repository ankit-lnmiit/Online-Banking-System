# Getting Started with Python on Bluemix

To get started, we'll take you through a sample Python Flask app, help you set up a development environment, deploy to Bluemix and add a Cloudant database.

## Prerequisites

You'll need the following:
* [Bluemix account](https://console.ng.bluemix.net/registration/)
* [Cloud Foundry CLI](https://github.com/cloudfoundry/cli#downloads)
* [Git](https://git-scm.com/downloads)
* [Python](https://www.python.org/downloads/)

## 1. Clone the sample app

Now you're ready to start working with the app. Clone the repo and change to the directory where the sample app is located.
  ```
git clone https://github.com/ankit-lnmiit/Online-Banking-System
cd Online-Banking-System
  ```

  Peruse the files in the *get-started-python* directory to familiarize yourself with the contents.

## 2. Run the app locally

Install the dependencies listed in the [requirements.txt ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://pip.readthedocs.io/en/stable/user_guide/#requirements-files) file to be able to run the app locally.

You can optionally use a [virtual environment ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://packaging.python.org/installing/#creating-and-using-virtual-environments) to avoid having these dependencies clash with those of other Python projects or your operating system.
  ```
pip install -r requirements.txt
  ```

Run the app.
  ```
python app.py
  ```

 View your app at: http://localhost:8000

## 3. Prepare the app for deployment

To deploy to {{site.data.keyword.Bluemix_notm}}, it can be helpful to set up a manifest.yml file. One is provided for you with the sample. Take a moment to look at it.

The manifest.yml includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. In this manifest.yml **random-route: true** generates a random route for your app to prevent your route from colliding with others.  You can replace **random-route: true** with **host: myChosenHostName**, supplying a host name of your choice. [Learn more...](https://console.bluemix.net/docs/manageapps/depapps.html#appmanifest)
 ```
 applications:
 - name: GetStartedPython
   random-route: true
   memory: 128M
 ```

## 4. Deploy the app

You can use the Cloud Foundry CLI to deploy apps.

Choose your API endpoint
   ```
cf api <API-endpoint>
   ```

Replace the *API-endpoint* in the command with an API endpoint from the following list.

|URL                             |Region          |
|:-------------------------------|:---------------|
| https://api.eu-de.bluemix.net  | Germany        |
|

Login to your {{site.data.keyword.Bluemix_notm}} account

  ```
cf login
  ```

From within the *get-started-python* directory push your app to {{site.data.keyword.Bluemix_notm}}
  ```
cf push
  ```

This can take a minute. If there is an error in the deployment process you can use the command `cf logs <Your-App-Name> --recent` to troubleshoot.

When deployment completes you should see a message indicating that your app is running.  View your app at the URL listed in the output of the push command.  You can also issue the
  ```
cf apps
  ```
  command to view your apps status and see the URL.

## 5. Add a database

MongoDB is already integrated with this app.
mongodb://<dbuser>:<dbpassword>@ds155634.mlab.com:55634/onlinebank
  


## 6. Use the database



1. Run your application locally.
  ```
python hello.py
  ```

  View your app at: http://localhost:8000. Any names you enter into the app will now get added to the database.

2. Make any changes you want and re-deploy to {{site.data.keyword.Bluemix_notm}}!
  ```
cf push
  ```

  View your app at the URL listed in the output of the push command, for example, *myUrl.mybluemix.net*.
# Online-Banking-System
