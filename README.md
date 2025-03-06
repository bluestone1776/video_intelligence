# video_intelligence
SERVICE_ACCOUNT_CREDENTIALS_PATH for video_intelligence use in flutter app
The code defines a VideoAnalyzer class that performs the following steps:

Configuration from Environment:
It retrieves the API key and service account credentials path from a dotenv (.env) file. These values are used to build the endpoint URL for the Video Intelligence API.

Authorization:
A helper function, _getAuthClient(), loads the service account JSON file from assets and uses it to create an authorized client (using OAuth2) with the necessary scopes.

Video Upload:
The uploadVideoToGCS() function uploads a video file to Google Cloud Storage (GCS) using the authorized client. It detects the file’s MIME type and returns the GCS URI if the upload is successful.

Video Annotation:
The startVideoAnnotation() function calls the Video Intelligence API to initiate an annotation process (in this case, for explicit content detection). It returns an operation ID used to track the process.

Polling for Completion:
The pollOperation() function periodically checks the status of the annotation operation until it completes, then returns the result.

Content Analysis:
The isVideoAppropriate() function examines the annotation result to determine if the video contains explicit content based on the likelihood levels provided by the API.

Overall Flow:
Finally, the analyzeVideo() function ties everything together: it uploads the video, starts the annotation, polls for the result, and returns whether the video is appropriate.
