# Publish over OneDrive plugin for Jenkins

Based on publish-to-ftp and extending publish-to and basic-credentials this Jenkins plugin publishes artifacts in a post-build to onedrive folders without the need to run a sync client on your build server.

# Registration
1. Register your client application on [Mirosoft Developers](http://go.microsoft.com/fwlink/p/?LinkId=193157)
2. The drive is created at the first login. Login into your account in the web browser, otherwise you will get an authentication error if you try to run the SDK with your credentials.
    - The user have to be logged in at least once to use your application.  
3. A development authentication token can be obtained on [OneDrive authentication](https://dev.onedrive.com/auth/msa_oauth.htm). 
4. More details can be found [here](https://dev.onedrive.com/app-registration.htm)

**Once your app is registered you'll want to note both your Client ID and Client Secret. They will be used when configuring you credentials in the next step.**

# Configure Credentials
The first step to configuring the pubish-over Onedrive plugin is to connect your Onedrive account. To do so, navigate to **Jenkins > Credentials**
Go to **Global Credentials** and **Add Credentials** of kind OneDrive API token.
Enter the Client ID and Client Secret into the fields and click authorize URL.
Text will appear under the Client Secret field with a link to generate the API token.
After allowing Jenkins access to OneDrive, the link will have the API token from after **code=** to the **ampersand**.
The API token can then be entered into the API token field on the Jenkins page.

# Set up directory
Under Jenkins configuration find the OneDrive configuration.
Name the configuration and specify the remote OneDrive directory (e.g. **/Jenkins**).
Click **Test Configuration** to ensure the OneDrive account can be authenticated and save the changes.

# Set up the build task
Go to the configuration view of the job.
Add the post build task **Send build artifacts over OneDrive**.
Under the name drop down menu select the name of the configuration you wish to use
    - This is the name you selected in the **Set up directory** step
Under Transfers specify the artifacts to upload to OneDrive.
Save the configuration and you're done!