README - v2rayNG Auto-Update + Traffic UI Patch (Professional)
===============================================================

What's inside this ZIP:
- patch.diff : git-style patch with code changes
- app/src/... : Kotlin source files (MyApplication, Worker)
- app/src/... : layout XML snippet (activity_main_traffic.xml)
- app/src/... : preferences.xml for auto-update toggle
- .github/workflows/build-sign-apk.yml : GitHub Actions workflow to build & sign APK
- install_instructions_mobile.md : Step-by-step instructions for doing everything from an Android phone (Termux)
- quick_notes.txt : important legal/technical notes

Important:
- I cannot push to your repo or add secrets for you. You must upload these files into your fork (https://github.com/Amir200h/v2rayNG).
- After upload and adding GitHub secrets, Actions will build and produce signed APK artifacts you can download.
- Keep your keystore secure and backed up; it's permanent for your app signing.

Files placement (when uploading via GitHub web UI):
- Copy the contents of app/src/... into the repository's app/src/main/java/com/yourdomain/v2rayng/  (create folders if needed)
- Put activity_main_traffic.xml into app/src/main/res/layout/
- Put preferences.xml into app/src/main/res/xml/
- Add MyApplication.kt and SubscriptionUpdateWorker.kt into the java package mentioned above
- Add .github/workflows/build-sign-apk.yml to your repository at .github/workflows/

If anything fails in Actions, copy the error logs and paste here and I'll debug it quickly.
