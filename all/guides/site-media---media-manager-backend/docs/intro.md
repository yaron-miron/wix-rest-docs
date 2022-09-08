SortOrder: 0
# Site Media - Media Manager API

## About This Service
This service contains functionality for working with the media that is stored in your site's Media Manager.

## Terminology
* **Special folders** 
  * `media-root` - A virtual folder that represents the top level of the site media  
    It will be used as the default `parentFolderId` if a request did not specify this param
  * `mobile-uploads` - A folder that contains all mobile uploads made to this site
  * `visitor-uploads` - A folder that contains files and folders that were uploaded by a site visitors or members
  * `purchesed-items` - A folder that contains files that were imported to the site media thought a purchase flow
* **MimeType** - a [standard](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) way to represent media types
* **File Assets** - Files in Wix Media are optimized for web use, each file is processed and may produce several variations of the file for use in different circumstance   
  For example:   
  * a video file can have assets of different resolutions or formats
  * an audio file can have assets of different qualities
  * video or audio files can have a preview asset that only contain a part of the file
  
  We call those assets, they are described in the Media property of the FileDescriptor.  
  The assets can be used by a URL or by calling the GenerateFileDownloadUrl API 
* **Private files**:   
  Files flagged with the private flag are protected from public use.
  The URLs of some assets and the original file will return 403 if used directly
  * When are private files used
    * An image that is sold (for example by the site WixArtStore)
    * A music track
    * A VOD video  
  * How to use private files
    * Accessing protected resources:  
    In order to download the original file or a protected asset use the GenerateFileDownloadUrl API
    * Public resources:  
      * Thumbnail - all thumbnails are public and can be used as with none private files
      * Preview asset - an optional asset with the `preview` identifier can be used as with none private files   
      For example:
        * A preview image that is smaller than the original image
        * A 30 seconds preview video 
        * A 30 seconds sample of an audio file
      * For assets that are protected the URL field will be an empty string
* **Operation Status**  
  The operation status of a file affects how this file can be used
  * READY - All the file asset URLs for the file can be used
  * PENDING - All the file asset URLs for the file are available, but the file itself may not exist yet 
     

## Limitations
* All the urls returned from the following requests are temporary.  
   
  * GenerateFileDownloadUrl
  * GenerateVideoSteamingUrl
  * GenerateFilesDownloadUrl
  * GenerateFolderDownloadUrl
  
  If no expiration is provided in the request a default expiration will be applied  
  The documentation of each endpoint will specify the default value and provide how to set it if possible
* GenerateFilesDownloadUrl cannot be used to download private files, To do that use the GenerateFileDownloadUrl API
* You cannot change a public file to be private or vice versa 
## Authorization
[Site browser request authentication](https://bo.wix.com/wix-docs/rnd/platformization-guidelines/authenticating-as-api-client#platformization-guidelines_authenticating-as-api-client_authenticating-from-a-browser---site-requests)

## Monitoring
* add here                                                             


