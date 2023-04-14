# ntfy Android Builder
A builder for the ntfy Android app that makes it easier to build a release for your custom server!
No local setup required, everything is built using GitHub Actions.

Note: This builder only supports building the Play release with Firebase Cloud Messaging.

## Preparation
1. Create a [Firebase](https://firebase.google.com) project and add an Android app, using `io.heckel.ntfy` as package ID when asked. Save the `google-services.json`.
2. Generate a new keystore using `keytool` if you don't have one already:
```bash
keytool -genkey -v -keystore your_keystore_name.keystore -alias your_alias_name -keyalg RSA -keysize 2048 -validity 10000
```
Make sure to save the password somewhere.
3. Fork this repository. You might want to consider making it private to hide your custom artifact builds.

## Setting up
1. Enable GitHub actions for your repository (if disabled!)
2. Create a base64-encoded copy of your previously generated keystore: `cat your_keystore_name.keystore | base64`
3. In Actions secrets, set the following:
    1. **APK_KEYSTORE**: The base64-encoded copy of your keystore generated in step 2.
    2. **APK_KEYSTORE_PASS**: The password to your keystore to be used for signing.
    3. **NTFY_APP_BASE_URL**: Default server base URL to be used in the app.
    4. **NTFY_FCM_CONFIG**: Contents of the Firebase Cloud Messaging config file, as downloaded in step 1 of Preparation.
4. Go the the GitHub actions tab, run the `Android CI` workflow and wait for a few minutes
5. Done! Your signed APK can be found in the list of artifacts.

## Getting help
If you need help with ntfy in particular, please contact them directly. I am not affilated with them in any way.

I am not planning on providing extensive support for this little project. Feel free to open an issue if you need help, but don't expect me to fix all of your problems.

Pull requests to enhance the workflow are of course always welcome!
