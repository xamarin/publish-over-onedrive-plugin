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
1. The first step to configuring the pubish-over Onedrive plugin is to connect your Onedrive account. To do so, navigate to **Jenkins > Credentials**
2. Go to **Global Credentials** and **Add Credentials** of kind OneDrive API token.
3. Enter the Client ID and Client Secret into the fields and click authorize URL.
4. Text will appear under the Client Secret field with a link to generate the API token.
5. After allowing Jenkins access to OneDrive, the link will have the API token from after **code=** to the **ampersand**.
6. The API token can then be entered into the API token field on the Jenkins page.

# Set up directory
1. Under Jenkins configuration find the OneDrive configuration.
2. Name the configuration and specify the remote OneDrive directory (e.g. **/Jenkins**).
3. Click **Test Configuration** to ensure the OneDrive account can be authenticated and save the changes.

# Set up the build task
1. Go to the configuration view of the job.
2. Add the post build task **Send build artifacts over OneDrive**.
3. Under the name drop down menu select the name of the configuration you wish to use
    - This is the name you selected in the **Set up directory** step
4. Under Transfers specify the artifacts to upload to OneDrive.
5. Save the configuration and you're done!