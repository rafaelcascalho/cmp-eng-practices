# Copy Firestore to Dev/Sandbox

**Abstract:**

From time to time there is a necessity to copy the Firestore database from the production project \(`me-doit-intl-com`\) to the development project \(`doitintl-cmp-dev`\) to ensure we have up-to-date data for stable testing or building new features.

Requirements:

* [Reference](https://firebase.google.com/docs/firestore/manage-data/move-data)
* [gcloud SDK](https://cloud.google.com/sdk/docs/quickstarts) 
* [firebase-tools](https://firebase.google.com/docs/cli)

**Step 1 - Set a default project to avoid deleting the prod database :\)**

`gcloud config set project doitintl-cmp-dev`

**Step 2 - Export prod firestore database \(~45 minutes\)**

`gcloud firestore export gs://doitintl-cmp-prod-firestore-export \\  
--async --project me-doit-intl-com`

**Step 3 - Delete dev firestore database \(~20 minutes\)**

`firebase firestore:delete --project doitintl-cmp-dev --all-collections`

**Step 4 - Import to dev firestore database \(~1 hour\)**

`gcloud firestore import gs://doitintl-cmp-prod-firestore-export/FOLDER --async --project doitintl-cmp-dev`

