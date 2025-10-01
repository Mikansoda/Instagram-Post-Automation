# About the project: An automation tool to create scheduled Instagram Posts
This project is an automated and semi-automated Instagram post that creates posts images, captions, and hashtags based on recent, trending, and relevant property/real estate news. For inability of obtaining Instagram API key, semi-automation routes using Buffer scheduler is provided.

# Tech stack
1. Automation Platform: n8n (workflow automation)
2. Semi-Automation Scheduler: Buffer
3. Containerization & Deployment: Docker and docker compose

# Third-Party Integrations
1. Cloudinary: media storage & image/video management
2. Pexels: stock photos API
3. Google Sheets & Google Drive: data & file storage

# Database Design
The database is designed with google sheets, with the purpose of posts archival, posesses few entities:
1.  Publish Schedule
    Logs timestamp upon workflow trigger
2.  Notes
    Status toggles, useful for semi-automated scheme where Instagram API Key is not granted. To track posts' status.
3.  Caption
    Contains caption of post.
4.  Pexel Url
    Stores image url from pexel, unique constraint. Posts should not have similar image, identified by pexel url.
5.  Cloudinary Url
    Stores image urls from cloudinary, unique constraint. Usage of Cloudinary is to keep the workflow organized and maintain stable URLs for other automations. This ensures flexibility for modifying or transforming files in the future.
6.  Image Url
    Stores image urls from google drive. Auto download link upon clicked,for an easier process for semi-automation using buffer.
7.  Drive Post Id
    Used to reference specific files in Google Drive, ensuring the workflow knows exactly which file to access or post.
8.  Articles Url 1 & 2
    Stores url of article used as source for creating caption.
9.  Hashtags
    Stores hashtags used in post.

# Installation and Setup

1. Clone the repository
2. Create a google sheet
3. Create an `.env` (example included in this repository) file which includes:
```
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=your_user
N8N_BASIC_AUTH_PASSWORD=your_password
PEXELS_KEY=your_pexels_key
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_UPLOAD_PRESET=your_upload_preset
IG_USER_ID=your_instagram_user_id
IG_ACCESS_TOKEN=your_token
TZ=Asia/Jakarta
```

4. Download the JSON file and upload to your N8N workflow to instantly copy

**Note:**  
Some credentials for connection setup are not available in env, such as Google Gemini, Cloudinary, Google Drive, and Google Sheets, please perform initial credential setup prior use.

**Author:**<br>
Developed by Zahra