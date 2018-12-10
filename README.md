*This is not an official Google product*

## Natural Language API + Firebase realtime Twitter dashboard demo

1. `cd` into `nl-firebase-twitter/`
2. Create a project in the [Firebase console](http://firebase.google.com/console) and install the [Firebase CLI](https://firebase.google.com/docs/cli/)
3. `cd` into the `frontend/` directory and run `firebase login` and `firebase init` to associate this with the Firebase project you just created. When prompted, don't overwrite existing files. Create a **database** and **hosting** project (no Functions).
4. In your Firebase console, click "Add Firebase to your web app". Copy the credentials to the top of the main.js file
5. `cd` into the `backend/` directory and run `npm install` to install dependencies
6. Generate a service account for your project by navigating to the "Project settings" tab in your Firebase console and then selecting "Service Accouts". Click "Generate New Private Key" and save this in your `backend/` directory as `keyfile.json`
7. Generate [Twitter Streaming API](https://dev.twitter.com/streaming/overview) credentials and copy them to `backend/local.json`
8. Navigate to the Cloud console for our project. Enabled the Natural Language API and generate an API key. Replace `YOUR-API-KEY` in `backend/local.json` with this key.
9. Replace `searchTerms` in `backend/index.js` with the search terms you'd like to filter tweets on
10. Replace `FIREBASE-PROJECT-ID` in `backend/local.json` with the id of your Firebase project
11. Set up BigQuery: in your Cloud console for the same project, create a BigQuery dataset. Then create a table in that dataset. When creating the table, click **Edit as text** and paste the following:
```
id:STRING,text:STRING,user:STRING,user_time_zone:STRING,user_followers_count:INTEGER,hashtags:STRING,tokens:STRING,score:STRING,magnitude:STRING,entities:STRING
```
12. Add your BigQuery dataset and table names to `backend/local.json`.
11. Run the server: from the `backend/` directory run `node index.js`. You should see tweet data being written to your Firebase database
12. In a separate terminal process, run the frontend: from the `frontend/` directory run `firebase serve`
13. Deploy your frontend: from the `frontend/` directory run `firebase deploy`
