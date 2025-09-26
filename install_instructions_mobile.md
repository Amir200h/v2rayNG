Mobile (Termux) step-by-step to create a keystore and upload secrets
===================================================================

1) Install Termux (recommended from F-Droid). Open Termux.

2) Install OpenJDK (for keytool) and coreutils:
   pkg update && pkg upgrade -y
   pkg install openjdk-17-jdk -y
   pkg install coreutils -y

3) Generate keystore (replace prompts with your info):
   keytool -genkeypair -v -keystore my-release-key.jks -alias my_key -keyalg RSA -keysize 2048 -validity 10000

   - Enter passwords and details. Remember the passwords and the alias.
   - The file my-release-key.jks will be created in Termux home directory.

4) Convert to base64 for GitHub Secret:
   base64 my-release-key.jks > keystore.base64
   # show it:
   cat keystore.base64

   Copy the whole output (it's long).

5) In GitHub mobile web:
   - Go to your repo -> Settings -> Secrets and variables -> Actions -> New repository secret
   - Create secrets:
     KEYSTORE_BASE64  => paste the long base64 content
     KEYSTORE_PASSWORD => the keystore password you entered
     KEY_ALIAS => my_key
     KEY_PASSWORD => the key password (often same as keystore password)

6) Upload the files from this ZIP into your repo using "Add file -> Upload files" in GitHub web UI.
   Commit to a new branch (recommended) like feature/auto-update-traffic-ui.

7) Visit Actions tab, open the latest workflow run, wait for it to finish and download the artifact named signed-apk.

8) Download APK to phone and install (allow install from unknown sources if needed).
