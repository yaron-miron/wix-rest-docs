SortOrder: 1
# Example Flows

This article shares some possible use cases your app could support, as well as an example flow that could support each
use case. You're certainly not limited to these use cases, but they can be a helpful jumping off point as you plan your
app's implementation.

## Private file upload - Temporary access to a file, and redirect

Imagine a site that sales music tracks, an email promoting a new track is sent with a download link that will be valid
for two days. Users clicking the expired link will be redirected to a landing page that will offer to purchase the track

To do this

1. Use GenerateFileUploadUrl to create an upload url for the private file
   ```json
   {
     "displayName": "artist - new track.mp3",
     "mimeType": "audio/mpeg",
     "private": true,
     "sizeInBytes": "5582258"
   }
   ```
2. Upload the file
   ```javascript
   async function uploadAPrivateFile(uploadUrl, fileContent) {
     const params = {'filename':'artist - new track.mp3'};
     const headers = {
       'Content-Type': 'application/octet-stream'
     }      
   
     const uploadResponse = await httpClient.put( uploadUrl, fileContent, { headers, params } );
     return uploadResponse;
   }
   ``` 
3. Use GenerateFileDownloadUrl with the file id returned from the upload response
   ```json
   {
     "fileId": uploadResponse.data.file.id,
     "expirationInMinutes": 2800,
     "expirationRedirectUrl": "https://www.my-site.com/shop/music/tracks"
   }
   ```
   

## Sync files from an external asset management system with Wix Media
Business owners can keep their AMS updated with their Wix Media with a two-way sync. To synchronize Wix and an external system, think about how your app will handle these flows

### Part 1: Initial Setup
1. To ensure a 1:1 mapping with the external AMS, use the labels property of the FileDescriptor to store the AMS identifier
2. After a file is uploaded, update the labels field and add your custom id
3. Create a mapping from the Wix fields to the external AMS fields, to be used whenever Wix and the external AMS are synchronized. Store this mapping on your app's server.
4. You'll soon see that this flow relies on webHooks to trigger syncs between Wix and the external CRM. To keep your app from getting caught in an endless loop, include logic that ignores a webhook that's triggered as the result of a sync

### Part 2: Synchronizing to the External System
Listen for any changes to Site Media with these webhooks:

FileDescriptor Webhook  
Folder Webhook  

When a FileDescriptor webhook is triggered, your endpoint will receive the file information in the payload. You can bring those changes to the external AMS with a flow like this one:
1. Get file.id from the webhook data.
2. Parse the data object for any other relevant information.
3. Use the mapping (from the initial setup) to copy the relevant information to the external AMS.
4. Ignore the resulting event from the external AMS so you don’t create an endless loop of updates.

### Part 3: Synchronizing to Wix
Listen for changes to files and folders from the external CRM. When your app detects a change that it needs to synchronize, follow this basic flow:

1. Copy the relevant details using one of these CRUD endpoints. Use the endpoint that matches the event from the external CRM.
2. Ignore the resulting event from Wix, so you don’t create an endless loop of updates.
