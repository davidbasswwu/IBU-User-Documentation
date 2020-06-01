# IBU v1.8

Notes:
- updated 01 June 2020
- some of these steps are for WWU users only.  Documentation for non-WWU users is coming soon.

<details>
<summary>Installation / Setup</summary>

- [ ] download from https://mabel.wwu.edu/ibu
- [ ] connect to VPN (remotevpn.wwu.edu or securevpn.wwu.edu)
- [ ] double-click the setup file
- [ ] if you encounter a warning/error screen:
    - macOS
        - if you see an "Unidentified publisher" message, cancel and right-click on the icon and click "Open".
    - Windows
        - if you see something like "Windows protected your PC".  Click "More Info" and then "Run Anyway" to proceed. 
        - ![Windows screenshot](https://bytebucket.org/wwulibraries/islandora-batch-uploader/raw/59aba294afec7ac78c2b6e43b3b7e36d6820e67a/static/windows-protected.png)
- configuration / setup ('gear' icon lower left corner)
    - if @ WWU, click the "Use Default Values" button
    - add the API keys you were given
    - click on the Eye (icon) in the top-right corner to see the hidden values
    - enter your email address, username and password and try to login
        - if you encounter a problem, close IBU and make sure you're connected to the VPN (if you are off-campus, using WiFi, or using IBU inside of a virtual machine) and then try again.
    ![config screen](https://github.com/davidbasswwu/IBU_Documentation/blob/master/img/00-configuration.png)
</details>

<details>
<summary>Uploading / Adding Files to Islandora</summary>

- From the Welcome screen, click "Upload"
    ![welcome screen](https://github.com/davidbasswwu/IBU_Documentation/blob/master/img/01-welcome.png)
    - Select "Owner"
        - Which organization on campus "owns" this file?  Who was it commissioned for?
    - Choose or create "Target Collection"
        - Nerd alert: this is not a true Islandora Collection; it's a virtual collection created using Drupal Taxonomies and Views.
    - Note: you will not be able to change the Owner or Target Collection on the next screen (Batch Description), but you can change the Target Collection on the Details screen (the last step of the process).
    - Access (Public or Restricted)
        - Please choose Public whenever possible.  Only Public view configurations are currently available on the Mabel website (as of May 2020).
    - Facial Recognition option
        - Note: if checked, IBU uses Clarifai to attempt to find faces in each photo, and will also try to suggest the name of the person in the event they've been tagged before.  All of that will be visible on the last (Details) page, but will not appear on the next screen.
    - Drag and drop files to begin upload process
    - Notes:
        - Start with small batches, and work your way to larger batches to make sure things are working first.
        - Make sure you have the files to upload on your local device (not a remote/network drive)
        - You should hear a "finger pop" when all of the files have been uploaded and ingested.
        - File formats processed by MABEL
            - Tested in IBU
                - tif
                - tiff
                - jpeg
                - jpg
                - png
                - pdf 
                - mp4
                - mov
                    - note: IBU converts .mov files to .mp4 to make them web-friendly, so additional processing time will be required.
            - Not yet tested in IBU
                - gif
                - mp3
                - jp2 
                - oga
                - ogg
                - flac
                - wav
                - m4v
                - mkv
                - mpeg
                - mpe
                - mpg
                - qt
                - ogv
            - Format-specific notes:
                - Still Images
                    - Please use the highest-quality (largest resolution) version you have.  Web-friendly thumbnails will be automatically generated.  Low-resolution files will generate a warning as shown in the following screenshot: [](https://d.pr/i/YiRuY2) 
                    - Recommended format: TIF
                        - .tiff files use the large-image viewer in MABEL, which has zoom and pan, and will eventually offer other features such as a tour/exhibit feature.
                    - Tiff and JPG formats can store GPS metadata, and that will be shown the the Details page if it exists.
                    - IBU features only available to this format are indicated below by "*img"
                - Video
                    - IBU features only available to this format are indicated below by "*vid"
                - PDF
                    - IBU features only available to this format are indicated below by "*pdf"
- Batch Description (Summary mode)
    - nothing is required in this interface, although it will save you time in the next screen if any of the values are the same for all files.
    - notice "Uploaded %" and "Ingest %".  Ideally, wait until both are at 100% before proceeding.
    - check the "Auto Increment" field to add consecutive numbers after each title (Test 1, Test 2, etc...).  
    - Adjust the "Tag Filter" percentage to show/hide Clarifai concepts
    - Adjust the "Group" slider to cluster images based on their similarity
        - if you see a yellow warning, that means that some of the thumbnails are not show.  Adjust the slider until they all appear.
    - Adjust the "Zoom" slider to make the thumbnails larger or smaller
    - failed ingest/upload > retry
    - TODO
        - remove file (email receipt for which ones)
- Detail Mode
    - required fields (indicated by a *)
        - Title
        - Release Form
        - at least one "tag" of any kind
    - "copy" icons/buttons/feature
        - copy
        - force copy
    - Release Notes
        - optional, internal (non-public) note about the permissions or release form.  You might consider adding the URL or the location of the signed release form here.
    - Title and Abstract > Suggested Captions
        - come from 3 sources:
            - the filename (stripped of some characters)
            - Microsoft AI (photos only)
            - Date Created (if defined, tries to find matches in the University calendar)
    - WWU Places
        - if you do not see any checkboxes, click the Eyecon to show more.  Click a place to confirm that the photo represents it, which will add a tag to the metadata, and also train the AI system to identify it automatically in the future.
    - People
        - if you checked the "Facial Recognition" box on the Welcome screen, you may see up to 5 faces listed here.  Choose or enter the name if you want to train it.  If you do not want to use Facial Recognition, you can always add the names to the Abstract, Title or "Add Your Own Tags".
    - Duplicate detection (v1.8)
        - if IBU can find a duplicate in MABEL, you will see a warning here.  To avoid duplicating the file, just click the Trash icon (lower-right corner) to remove this file from IBU.
        - It only finds "public" files
        - TODO: add a slider to adjust the sensitivity of the matching process. 
    - Notes:
        - you can click "Back", but be aware that anything you do on the previous (Batch summary) page may overwrite what you did on the Details page, so use this with caution.

</details>  

<details>
<summary>Editing Islandora Records</summary>

From the Welcome screen     
![welcome screen](https://github.com/davidbasswwu/IBU_Documentation/blob/master/img/01-welcome.png)
click "Edit":
- Enter IDs of records to edit
- edit each record as you normally would
- known issues (v1.8):
    - you cannot change the "Owner"
    - you can change the "Target Collection", but you cannot add one from this screen (yet) 
    - the copy/force copy feature has not been added to the "Target Collection" field yet.
- Publish, and look for the email receipt (check Clutter/Junk folders)