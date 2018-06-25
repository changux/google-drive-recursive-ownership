# Google Drive Recursive Ownership Tool

### Supported Files

G Suite for Government and G Suite for Education accounts can change ownership of any file owned by the current user, including uploaded/synced files suchs as PDFs.

Other Google Accounts such as G Suite for Business or Personal Google Accounts can only transfer ownership of Google files (Docs, Sheets, Sildes, Forms, Drawings, My Maps, and folders).

NOTE: Ownership can only be transferred to members of the same G Suite or Google domain. Ex. @gmail.com can only transfer to other @gmail.com addresses.

NOTE: The Google Drive API does not allow suppressing notifications for change of ownership if the _if_ the new owner does not already have access to the file. However, if the new owner _already_ has access to the file, upgrading their permissions to ownership will _not_ generate a notification.

### Setup

    git clone https://github.com/davidstrauss/google-drive-recursive-ownership
    pip install --upgrade google-api-python-client
    pip install nose tornado oauth2client 

### Usage

If transfer.py is contained in a folder listed in your system's PATH this can be run from anywhere. Otherwise it needs to be run from the directory where transfer.py is located.

    python transfer.py PATH-PREFIX NEW-OWNER-EMAIL SHOW-ALREADY-OWNER
    
 - `PATH-PREFIX` assumes use of "/" or "\" as appropriate for your operating system.
 - `SHOW-ALREADY-OWNER` "`true`"|"`false`" (default `true`) to hide feedback for files already set correctly
    
Windows Example:

    python transfer.py "Folder 1\Folder 2\Folder 3" new_owner@example.com true

Mac/Linux Example:

    python transfer.py "Folder 1/Folder 2/Folder 3" new_owner@example.com false

### Create clients_secret.josn

If you go to your Google developers console you should see a section titled OAuth 2.0 client IDs. Click on an entry in that list, and you will see a number of fields, including Client secret.

If you have not yet created credentials, click the Create credentials button, and follow the instructions to create new credentials, and then follow the steps outlined above to find the Client secret.

`Credentials --> OAuth Client ID --> Other --> "Name it" --> Download JSON.` 
