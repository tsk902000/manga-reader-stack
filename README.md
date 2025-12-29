# Introduction
Just a docker compose file for Manga Reader Stack 


# Steps for working
To make this work seamlessly, follow these three steps after running docker-compose up -d:

1. Configure Suwayomi for Komga
Suwayomi downloads manga into a folder structure like: Downloads/Source Name/Manga Title/Chapter.cbz.

Log into Suwayomi (localhost:4567).

Go to Settings > Downloads.

Ensure "Download as CBZ" is checked.

Important: In Komga, point your library to the /data folder. It will automatically see the subfolders Suwayomi creates.

2. Initialize Komga
Log into Komga (localhost:25600).

Create your admin account.

Add a new Library, name it "Manga," and point it to the /data folder.

In Library Settings, enable "Scan on startup" and "Watch for file changes."

3. Link Komf to Komga
Komf is a "sidecar" app. It doesn't have a complex GUI for everything; it mostly runs in the background.

Open the Komf Web UI (localhost:8085).

Under Server Settings, ensure the Komga URL is http://komga:25600 (this works because they are in the same Docker network).

Once linked, Komf will monitor your Komga library. When Suwayomi drops a new chapter, Komga sees it, and Komf will automatically reach out to AniList/MyAnimeList to grab the metadata.

A Quick Note on File Permissions
If you are on Linux, ensure the user running Docker has permissions to write to the ./manga-library folder. You can add user: "1000:1000" (replace with your UID/GID) to the services in the YAML if you run into "Permission Denied" errors.

Would you like me to show you how to add the "Kavita" reader to this stack as an alternative to Komga, or are you set on Komga?
