# Sheets API

- good answer on authenticating to work with sheets: https://stackoverflow.com/questions/38949318/google-sheets-api-returns-the-caller-does-not-have-permission-when-using-serve
    Create a service account: https://console.developers.google.com/iam-admin/serviceaccounts/
    In options, create a key: this key is your usual client_secret.json - use it the same way
    Make the role owner for the service account (Member name = service account ID = service account email ex: thomasapp@appname-201813.iam.gserviceaccount.com
    Copy the email address of your service account = service account ID
    Simply go in your browser to the Google sheet you want to interact with
    Go to SHARE on the top right of your screen
    Go to advanced settings and share it with an email address of your service account ex: thomasapp@appname-201813.iam.gserviceaccount.com
