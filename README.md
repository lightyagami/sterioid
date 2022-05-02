![Snake](https://telegra.ph/file/3eadd386697205a815e87.png)


**Snake Mirror Bot** is a _multipurpose_ Telegram Bot written in Python for mirroring/uploading files from the Internet to Google Drive.

# Features:
<details>
    <summary><b>Click here to check the features </b></summary>

## Features
- qBittorrent
- Leech Supported
- Thumbnail Support
- Size limiting for Torrent/Direct, Tar/Unzip, Mega and clone
- Stop duplicates for all tasks except for qBittorrent and youtube-dl tasks 
- Tar/Unzip G-Drive link 
- Select files from Torrent before downloading using qbittorrent
- Sudo with or without Database
- Multiple Trackers support
- Extracting **tar.xz** support
- Counting files/folders from Google Drive link
- View Link button instead of direct download link
- Shell and Executor
- Speedtest
- Status Pages for unlimited tasks
- Clone status
- Search in Mltiple Drive folder/TD
- Many bugs has been fixed
- Torrent search Supported:
```
nyaa.si, sukebei, 1337x, piratebay,
tgx, yts, eztv, torlock, rarbg
```
- Direct links Supported:
```
letsupload.io, hxfile.co, anonfiles.com, bayfiles.com, antfiles,
fembed.com, fembed.net, femax20.com, layarkacaxxi.icu, fcdn.stream,
sbplay.org, naniplay.com, naniplay.nanime.in, naniplay.nanime.biz, sbembed.com,
streamtape.com, streamsb.net, feurl.com, pixeldrain.com, racaty.net,
1fichier.com, 1drv.ms (Only works for file not folder or business account),
uptobox.com (Uptobox account must be premium), solidfiles.com

```
## From Original and Other Repositories
- Mirroring direct download links, Torrent, and Telegram files to Google Drive
- Mirroring Mega.nz links to Google Drive (If your Mega account not premium, it will limit 5GB/6 hours)
- Copy files from someone's Drive to your Drive (Using Autorclone)
- Download/Upload progress, Speeds and ETAs
- Mirror all Youtube-dl supported links
- Docker support
- Uploading to Team Drive
- Index Link support
- Service Account support
- Delete files from Drive
- Shortener support
- Custom Filename (Only for URL, Telegram files and Youtube-dl. Not for Mega links and Magnet/Torrents)
- Extracting password protected files, using custom filename and download from password protected Index Links see these examples:
<p><a href="https://telegra.ph/Magneto-Python-Aria---Custom-Filename-Examples-01-20"> <img src="https://img.shields.io/badge/See%20Telegraph-grey?style=for-the-badge&logo=telegraph" width="170""/></a></p>

- Extract these file types and uploads to Google Drive
```
ZIP, RAR, TAR, 7z, ISO, WIM, CAB, GZIP, BZIP2,
APM, ARJ, CHM, CPIO, CramFS, DEB, DMG, FAT,
HFS, LZH, LZMA, LZMA2, MBR, MSI, MSLZ, NSIS,
NTFS, RPM, SquashFS, UDF, VHD, XAR, Z.
```

</details>

# How to deploy?
Deploying is pretty much straight forward and is divided into several steps as follows:
## Installing requirements

- Clone this repository:
```
git clone https://github.com/VenomSnake/vhascometo

cd vhascometo
```

- Install requirements
For Debian based distros
```
sudo apt install python3
```
Install Docker by following the [official Docker docs](https://docs.docker.com/engine/install/debian/)

- For Arch and it's derivatives:
```
sudo pacman -S docker python
```
- Install dependencies for running setup scripts:
```
pip3 install -r requirements-cli.txt
```
## Generate Database
<details>
    <summary><b>Click Here For More Details</b></summary>

**1. Using ElephantSQL**
- Go to https://elephantsql.com/ and create account (skip this if you already have ElephantSQL account)
- Hit **Create New Instance**
- Follow the further instructions in the screen
- Hit **Select Region**
- Hit **Review**
- Hit **Create instance**
- Select your database name
- Copy your database URL, and fill to **DATABASE_URL** in config

**2. Using Heroku PostgreSQL**
<p><a href="https://dev.to/prisma/how-to-setup-a-free-postgresql-database-on-heroku-1dc1"> <img src="https://img.shields.io/badge/See%20Dev.to-black?style=for-the-badge&logo=dev.to" width="160""/></a></p>

</details>

## Setting up config file
<details>
    <summary><b>Click Here For More Details</b></summary>

```
cp config_sample.env config.env 
```
Fill up rest of the fields. Meaning of each fields are discussed below:
### Required Field
- `BOT_TOKEN`: The Telegram bot token that you get from [@BotFather](https://t.me/BotFather)
- `TELEGRAM_API`: This is to authenticate to your Telegram account for downloading Telegram files. You can get this from https://my.telegram.org DO NOT put this in quotes.
- `TELEGRAM_HASH`: This is to authenticate to your Telegram account for downloading Telegram files. You can get this from https://my.telegram.org
- `OWNER_ID`: The Telegram user ID (not username) of the Owner of the bot, you can get it from [@Userinfobot](https://t.me/userinfobot)
- `GDRIVE_FOLDER_ID`: This is the folder ID of the Google Drive Folder to which you want to upload all the mirrors.
- `DOWNLOAD_DIR`: The path to the local folder where the downloads should be downloaded to.
- `DOWNLOAD_STATUS_UPDATE_INTERVAL`: A short interval of time in seconds after which the Mirror progress message is updated. (I recommend to keep it `5` seconds at least)  
- `AUTO_DELETE_MESSAGE_DURATION`: Interval of time (in seconds), after which the bot deletes it's message (and command message) which is expected to be viewed instantly. (**NOTE**: Set to `-1` to never automatically delete messages)
### Optional Field
- `ACCOUNTS_ZIP_URL`: Only if you want to load your Service Account externally from an Index Link. Archive the accounts folder to a zip file. Fill this with the direct link of that file.
- `TOKEN_PICKLE_URL`: Only if you want to load your **token.pickle** externally from an Index Link. Fill this with the direct link of that file.
- `MULTI_SEARCH_URL`: To use search/list in multiple TD/folder. Run driveid.py in your terminal and follow it. It will generate a file **drive_folder** when you finish. Upload that file [here](https://gist.github.com/) with the same file name. Open the raw file of that gist, it's URL will be your required config. Check wiki for gist related help. 
- `DATABASE_URL`: Your Database URL. See [Generate Database](https://github.com/venomsnake/vhascometo/tree/master#generate-database) to generate database (**NOTE**: If you use database you can save your Sudo ID permanently using `/addsudo` command).
- `AUTHORIZED_CHATS`: Fill user_id and chat_id (not username) of groups/users you want to authorize. Separate them with space, Examples: `-0123456789 -1122334455 6915401739`.
- `SUDO_USERS`: Fill user_id (not username) of users whom you want to give sudo permission. Separate them with space, Examples: `0123456789 1122334455 6915401739` (**NOTE**: If you want to save Sudo ID permanently without database, you must fill your Sudo Id here).
- `IS_TEAM_DRIVE`: Set to `True` if `GDRIVE_FOLDER_ID` is from a Team Drive else `False` or Leave it empty.
- `USE_SERVICE_ACCOUNTS`: (Leave empty if unsure) Whether to use Service Accounts or not. For this to work see [Using Service Accounts](https://github.com/venomsnake/vhascometo#generate-service-accounts-what-is-service-account) section below.
- `INDEX_URL`: Refer to https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index The URL should not have any trailing '/'
- `MEGA_API_KEY`: Mega.nz API key to mirror mega.nz links. Get it from [Mega SDK Page](https://mega.nz/sdk)
- `MEGA_EMAIL_ID`: Your E-Mail ID used to sign up on mega.nz for using premium account (Leave though)
- `MEGA_PASSWORD`: Your Password for your mega.nz account
- `BLOCK_MEGA_FOLDER`: If you want to remove mega.nz folder support, set it to `True`.
- `BLOCK_MEGA_LINKS`: If you want to remove mega.nz mirror support, set it to `True`.
- `STOP_DUPLICATE`: (Leave empty if unsure) if this field is set to `True`, bot will check file in Drive, if it is present in Drive, downloading or cloning will be stopped. (**NOTE**: File will be checked using filename, not using filehash, so this feature is not perfect yet)
- `CLONE_LIMIT`: To limit the size of Google Drive folder/file which you can clone (leave space between number and unit, Available units are (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- `MEGA_LIMIT`: To limit the size of Mega download (leave space between number and unit, available units are (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- `TORRENT_DIRECT_LIMIT`: To limit the Torrent/Direct mirror size, leave space between number and unit. Available units are (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- `TAR_UNZIP_LIMIT`: To limit the size of mirroring as Tar or unzipmirror. Available units are (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- `VIEW_LINK`: View Link button to open file Index Link in browser instead of direct download link, you can figure out if it's compatible with your Index code or not, open any video from you Index and check if its URL ends with `?a=view`, if yes make it `True` it will work (Compatible with https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index Code)
- `UPTOBOX_TOKEN`: Uptobox token to mirror uptobox links. Get it from [Uptobox Premium Account](https://uptobox.com/my_account).
- `HEROKU_EMAIL`: E-Mail of the Heroku account in which the above app will be deployed (**NOTE**: Only needed if you are deploying on Heroku with Github Workflow).
- `HEROKU_API_KEY`: (Only if you deploying on Heroku) Your Heroku API key, get it from https://dashboard.heroku.com/account.
- `HEROKU_APP_NAME`: (Only if you deploying on Heroku) Your Heroku app name.
- `IGNORE_PENDING_REQUESTS`: If you want the bot to ignore pending requests after it restarts, set this to `True`.
- `STATUS_LIMIT`: Limit the no. of tasks shown in status message with button. (**NOTE**: Recommended limit is `4` tasks at max).
- `IS_VPS`: (Only for VPS) Don't set this to `True` even if you are using VPS, unless facing error with web server. Also go to start.sh and replace `$PORT` by `80` or any port you want to use.
- `SERVER_PORT`: (Only if IS_VPS is `True`) Base URL Port
- `BASE_URL_OF_BOT`: (Required for Heroku to avoid sleep/idling) Valid BASE URL of app where the bot is deployed. IP/Domain of your bot like `http://myip` or if you have chosen other port then `80` then `http://myip:port`, for Heroku fill `https://yourappname.herokuapp.com` (**NOTE**: Do not put slash at the end), still got idling? You can use http://cron-job.org to ping your Heroku app.
- `SHORTENER_API`: Fill your Shortener API key if you are using Shortener.
- `SHORTENER`: if you want to use Shortener in G-Drive and index link, fill Shortener URL here. Examples:
```
exe.io, gplinks.in, shrinkme.io, urlshortx.com, shortzon.com
```

Above are the supported url Shorteners. Except these only some url Shorteners are supported.

**Note**: You can limit maximum concurrent downloads by changing the value of **MAX_CONCURRENT_DOWNLOADS** in aria.sh. By default, it's set to `7`.
### Add more buttons (Optional Field)
Three buttons are already added of Drive Link, Index Link, and View Link, you can add extra buttons, these are optional, if you don't know what are below entries, simply leave them, don't fill anything in them.
- `BUTTON_FOUR_NAME`:
- `BUTTON_FOUR_URL`:
- `BUTTON_FIVE_NAME`:
- `BUTTON_FIVE_URL`:
- `BUTTON_SIX_NAME`:
- `BUTTON_SIX_URL`:
</details>

## Getting Google OAuth API credential file
- Visit the [Google Cloud Console](https://console.developers.google.com/apis/credentials)
- Go to the OAuth Consent tab, fill it, and save.
- Go to the Credentials tab and click Create Credentials -> OAuth Client ID
- Choose Desktop and Create.
- Use the download button to download your credentials.
- Move that file to the root of mirrorbot, and rename it to **credentials.json**
- Visit [Google API page](https://console.developers.google.com/apis/library)
- Search for Drive and enable it if it is disabled
- Finally, run the script to generate **token.pickle** file for Google Drive:
```
pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib
python3 generate_drive_token.py
```

## Deploy On VPS

**IMPORTANT NOTE**: In start.sh you must replace `$PORT` with 80 or any other port you want to use

- Start Docker daemon (skip if already running):
```
sudo dockerd
```
- Build Docker image:
```
sudo docker build . -t mirror-bot
```
- Run the image:
```
sudo docker run -p 80:80 mirror-bot
```
OR

**NOTE**: If you want to use port other than 80, so change it in [docker-compose.yml](https://github.com/venomsnake/vhascometo/blob/master/docker-compose.yml)

- Using Docker-compose so you can edit and build your image in seconds:
```
sudo apt install docker-compose
```
- Build and run Docker image:
```
sudo docker-compose up
```
- After edit files with nano for example (nano start.sh):
```
sudo docker-compose build
sudo docker-compose up
```
or
```
sudo docker-compose up --build
```
- To stop docker run 
```
sudo docker ps
```
```
sudo docker stop id
```
- To clear the container (this will not effect on image):
```
sudo docker container prune
```
- To delete the image:
```
sudo docker image prune -a
```

## Deploying on Heroku with Github Workflow
<p><a href="https://github.com/venomsnake/vhascometo/blob/master/heroku-guide.md"> <img src="https://img.shields.io/badge/Deploy%20To%20Heroku-blueviolet?style=for-the-badge&logo=heroku" width="170"/></a></p>

## Deploying on Heroku with heroku-cli and Goorm IDE
<p><a href="https://telegra.ph/How-to-Deploy-a-Mirror-Bot-to-Heroku-with-CLI-05-06"> <img src="https://img.shields.io/badge/see%20on%20telegraph-grey?style=for-the-badge" width="170"/></a></p>

## Deploying on Railway
[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template?template=https%3A%2F%2Fgithub.com%2Fvenomsnake%2Fvhascometo%2Ftree%2Fmaster&plugins=postgresql&envs=ACCOUNTS_ZIP_URL%2CAUTHORIZED_CHATS%2CAUTO_DELETE_MESSAGE_DURATION%2CBLOCK_MEGA_FOLDER%2CBLOCK_MEGA_LINKS%2CBOT_TOKEN%2CBUTTON_FOUR_NAME%2CBUTTON_FOUR_URL%2CBUTTON_FIVE_NAME%2CBUTTON_FIVE_URL%2CBUTTON_SIX_NAME%2CBUTTON_SIX_URL%2CCLONE_LIMIT%2CDOWNLOAD_DIR%2CDOWNLOAD_STATUS_UPDATE_INTERVAL%2CENV%2CGDRIVE_FOLDER_ID%2CIGNORE_PENDING_REQUESTS%2CINDEX_URL%2CIS_TEAM_DRIVE%2CMEGA_API_KEY%2CMEGA_EMAIL_ID%2CMEGA_PASSWORD%2CMEGA_LIMIT%2COWNER_ID%2CSHORTENER%2CSHORTENER_API%2CSTOP_DUPLICATE_CLONE%2CSTOP_DUPLICATE_MEGA%2CSTOP_DUPLICATE_MIRROR%2CTAR_UNZIP_LIMIT%2CTELEGRAM_API%2CTELEGRAM_HASH%2CTOKEN_PICKLE_URL%2CTORRENT_DIRECT_LIMIT%2CUPSTREAM_REPO%2CUPSTREAM_BRANCH%2CUPTOBOX_TOKEN%2CUSE_SERVICE_ACCOUNTS%2CVIEW_LINK&optionalEnvs=ACCOUNTS_ZIP_URL%2CAUTHORIZED_CHATS%2CBLOCK_MEGA_FOLDER%2CBLOCK_MEGA_LINKS%2CBUTTON_FOUR_NAME%2CBUTTON_FOUR_URL%2CBUTTON_FIVE_NAME%2CBUTTON_FIVE_URL%2CBUTTON_SIX_NAME%2CBUTTON_SIX_URL%2CCLONE_LIMIT%2CDOWNLOAD_DIR%2CDOWNLOAD_STATUS_UPDATE_INTERVAL%2CIGNORE_PENDING_REQUESTS%2CINDEX_URL%2CIS_TEAM_DRIVE%2CMEGA_API_KEY%2CMEGA_EMAIL_ID%2CMEGA_PASSWORD%2CMEGA_LIMIT%2CSHORTENER%2CSHORTENER_API%2CSTOP_DUPLICATE_CLONE%2CSTOP_DUPLICATE_MEGA%2CSTOP_DUPLICATE_MIRROR%2CTAR_UNZIP_LIMIT%2CTOKEN_PICKLE_URL%2CTORRENT_DIRECT_LIMIT%2CUPTOBOX_TOKEN%2CUSE_SERVICE_ACCOUNTS%2CVIEW_LINK&ACCOUNTS_ZIP_URLDesc=%28Optional%29+Only+if+you+want+to+load+your+service+accs+externally+from+an+index+link.+Archive+your+service+accs+json+files+to+a+zip+file+directly+%28don%27t+archive+the+accounts+folder.+Select+all+the+jsons+inside+and+zip+them+only+instead.+Name+the+zip+file+with+whatever+you+want%2C+it+doesn%27t+matter%29.+Fill+this+with+the+direct+link+of+that+file.&AUTHORIZED_CHATSDesc=Fill+User+ID+and+Chat+ID+of+you+want+to+authorize.+In+case+of+multiple+user+or+chat+id+separate+them+via+space.&AUTO_DELETE_MESSAGE_DURATIONDesc=Interval+of+time+%28in+seconds%29%2C+after+which+the+bot+deletes+it%27s+message+%28and+command+message%29+which+is+expected+to+be+viewed+instantly.+Note%3A+Set+to+-1+to+never+automatically+delete+messages.&BLOCK_MEGA_FOLDERDesc=If+you+want+to+remove+mega.nz+folder+support%2C+set+it+to+True.&BLOCK_MEGA_LINKSDesc=If+you+want+to+remove+mega.nz+mirror+support%2C+set+it+to+True.&BOT_TOKENDesc=The+telegram+bot+token+that+you+get+from+%40BotFather.&BUTTON_FOUR_NAMEDesc=Extra+buttons+%28optional%29.&BUTTON_FOUR_URLDesc=Fill+your+URL+if+you+are+using+extra+buttons.&BUTTON_FIVE_NAMEDesc=Extra+buttons+%28optional%29.&BUTTON_FIVE_URLDesc=Fill+your+URL+if+you+are+using+extra+buttons.&BUTTON_SIX_NAMEDesc=Extra+buttons+%28optional%29.&BUTTON_SIX_URLDesc=Fill+your+URL+if+you+are+using+extra+buttons.&CLONE_LIMITDesc=To+limit+cloning+Google+Drive+%28leave+space+between+number+and+unit%2C+Available+units+is+%28gb+or+GB%2C+tb+or+TB%29.&DOWNLOAD_DIRDesc=The+path+to+the+local+folder+where+the+downloads+should+be+downloaded+to.&DOWNLOAD_STATUS_UPDATE_INTERVALDesc=A+short+interval+of+time+in+seconds+after+which+the+Mirror+progress+message+is+updated.+%28I+recommend+to+keep+it+5+seconds+at+least%29.&ENVDesc=Setting+this+to+ANYTHING+will+enable+Webhooks+when+in+env+mode&GDRIVE_FOLDER_IDDesc=This+is+the+folder+ID+of+the+Google+Drive+Folder+to+which+you+want+to+upload+all+the+mirrors.&IGNORE_PENDING_REQUESTSDesc=If+you+want+the+bot+to+ignore+pending+requests+after+it+restarts%2C+set+this+to+True.&INDEX_URLDesc=Refer+to+https%3A%2F%2Fgitlab.com%2FPraveenBhadooOfficial%2FGoogle-Drive-Index+The+URL+should+not+have+any+trailing+%27%2F%27.&IS_TEAM_DRIVEDesc=Set+to+%27True%27+if+GDRIVE_FOLDER_ID+is+from+a+Team+Drive+else+False+or+Leave+it+empty.&MEGA_API_KEYDesc=Mega.nz+api+key+to+mirror+mega.nz+links.+Get+it+from+https%3A%2F%2Fmega.nz%2Fsdk.&MEGA_EMAIL_IDDesc=Your+email+id+you+used+to+sign+up+on+mega.nz.&MEGA_PASSWORDDesc=Your+password+for+your+mega.nz+account.&MEGA_LIMITDesc=To+limit+downloading+Mega+%28leave+space+between+number+and+unit%2C+Available+units+is+%28gb+or+GB%2C+tb+or+TB%29.&OWNER_IDDesc=The+Telegram+User+ID+of+the+Owner+of+the+Bot.+Get+it+by+using+%2Finfo+in+%40MissRose_bot.&SHORTENERDesc=If+you+want+to+use+shortener+in+Gdrive+and+index+link.&SHORTENER_APIDesc=Fill+your+shortener+api+key+if+you+are+using+shortener.&STOP_DUPLICATE_CLONEDesc=If+this+field+is+set+to+True%2C+bot+will+check+file+in+Drive%2C+if+it+is+present+in+Drive%2C+cloning+will+be+stopped.&STOP_DUPLICATE_MEGADesc=If+this+field+is+set+to+True%2C+bot+will+check+file+in+Drive%2C+if+it+is+present+in+Drive%2C+downloading+Mega+will+be+stopped.&STOP_DUPLICATE_MIRRORDesc=If+this+field+is+set+to+True%2C+bot+will+check+file+in+Drive%2C+if+it+is+present+in+Drive%2C+downloading+will+be+stopped.&TAR_UNZIP_LIMITDesc=To+limit+mirroring+as+Tar+or+unzipmirror.+Available+units+is+%28gb+or+GB%2C+tb+or+TB%29.&TELEGRAM_APIDesc=This+is+to+authenticate+to+your+Telegram+account+for+downloading+Telegram+files.+You+can+get+this+from+https%3A%2F%2Fmy.telegram.org.&TELEGRAM_HASHDesc=This+is+to+authenticate+to+your+Telegram+account+for+downloading+Telegram+files.+You+can+get+this+from+https%3A%2F%2Fmy.telegram.org.&TOKEN_PICKLE_URLDesc=%28Optional%29+Only+if+you+want+to+load+your+token.pickle+externally+from+an+index+link.+Fill+this+with+the+direct+link+of+that+file.&TORRENT_DIRECT_LIMITDesc=To+limit+the+Torrent%2FDirect+mirror+size%2C+Leave+space+between+number+and+unit.+Available+units+is+%28gb+or+GB%2C+tb+or+TB%29.&UPSTREAM_REPODesc=Link+for+Bot+Upstream+Repo%2C+If+you+want+default+update%2C+Fill+https%3A%2F%2Fgithub.com%2Fvenomsnake%2Fvhascometo.&UPSTREAM_BRANCHDesc=Branch+name+for+Upstream+Repo+%28Recommended+using+master+branch%29.&UPTOBOX_TOKENDesc=Uptobox+premium+token+to+mirror+uptobox+links.+Get+it+from+https%3A%2F%2Fuptobox.com%2Fmy_account.&USE_SERVICE_ACCOUNTSDesc=Whether+to+use+Service+Accounts+or+not.+For+this+to+work+see+%27Using+Service+Accounts%27+in+repo.&VIEW_LINKDesc=View+Link+button+to+open+file+Index+Link+in+browser+instead+of+direct+download+link%2C+you+can+figure+out+if+it%27s+compatible+with+your+Index+code+or+not%2C+open+any+video+from+you+Index+and+check+if+the+END+of+link+from+browser+link+bar+is+%3Fa%3Dview%2C+if+yes+make+it+True+it+will+work+%28Compatible+with+Bhadoo+Index+Code%29.&DOWNLOAD_DIRDefault=%2Fusr%2Fsrc%2Fapp%2Fdownloads&DOWNLOAD_STATUS_UPDATE_INTERVALDefault=5&ENVDefault=ANYTHING&UPSTREAM_REPODefault=https%3A%2F%2Fgithub.com%2Fvenomsnake%2Fvhascometo&UPSTREAM_BRANCHDefault=master)

**NOTE**: ADD Token.pickle in the new repository for upload to function or use URL method.
 ---

# Using Service Accounts for uploading to avoid user rate limit
For Service Account to work, you must set **USE_SERVICE_ACCOUNTS=**"True" in config file or environment variables,
Many thanks to [AutoRClone](https://github.com/xyou365/AutoRclone) for the scripts.
**NOTE**: Using Service Accounts is only recommended while uploading to a Team Drive.

## Generate Service Accounts. [What is Service Account](https://cloud.google.com/iam/docs/service-accounts)
<details>
    <summary><b>Click Here For More Details</b></summary>

Let us create only the Service Accounts that we need.
**Warning**: abuse of this feature is not the aim of this project and we do **NOT** recommend that you make a lot of projects, just one project and 100 SAs allow you plenty of use, its also possible that over abuse might get your projects banned by Google.

**NOTE:** 1 Service Account can copy around 750gb a day, 1 project can make 100 Service Accounts so that's 75tb a day, for most users this should easily suffice.
```
python3 gen_sa_accounts.py --quick-setup 1 --new-only
```
A folder named accounts will be created which will contain keys for the Service Accounts.

Or you can create Service Accounts to current project, no need to create new one

- List your projects ids
```
python3 gen_sa_accounts.py --list-projects
```
- Enable services automatically by this command
```
python3 gen_sa_accounts.py --enable-services $PROJECTID
```
- Create Sevice Accounts to current project
```
python3 gen_sa_accounts.py --create-sas $PROJECTID
```
- Download Sevice Accounts as accounts folder
```
python3 gen_sa_accounts.py --download-keys $PROJECTID
```
If you want to add Service Accounts to Google Group, follow these steps

- Mount accounts folder
```
cd accounts
```
- Grab emails form all accounts to emails.txt file that would be created in accounts folder
```
grep -oPh '"client_email": "\K[^"]+' *.json > emails.txt
```
- Unmount acounts folder
```
cd -
```
Then add emails from emails.txt to Google Group, after that add Google Group to your Shared Drive and promote it to manager.

**NOTE**: If you have created SAs in past from this script, you can also just re download the keys by running:
```
python3 gen_sa_accounts.py --download-keys project_id
```

</details>

## Add all the Service Accounts to the Team Drive
- Run:
```
python3 add_to_team_drive.py -d SharedTeamDriveSrcID
```

# Youtube-dl authentication using .netrc file
For using your premium accounts in Youtube-dl or for protected Index Links, edit the netrc file according to following format:
```
machine host login username password my_youtube_password
```
For Index Link with only password without username, even http auth will not work, so this is the solution.
```
machine example.workers.dev password index_password
```
Where host is the name of extractor (eg. Youtube, Twitch). Multiple accounts of different hosts can be added each separated by a new line.

# Credits

Thanks to:
- [`out386`](https://github.com/out386) heavily inspired from Telegram Bot which is written in JS
- [`Izzy12`](https://github.com/lzzy12) for build up this bot from scratch
- [`jaskaranSM`](https://github.com/jaskaranSM) for build up this bot from scratch
- [`Dank-del`](https://github.com/Dank-del) for base repo
- [`magneto261290`](https://github.com/magneto261290) for some features
- [`SVR666`](https://github.com/SVR666) for some features & fixes
- [`anasty17`](https://github.com/anasty17) for some features & help
- [`breakdowns`](https://github.com/breakdowns) for slam-mirrorbot
- [`zevtyardt`](https://github.com/zevtyardt) for some direct links
- [`yash-dk`](https://github.com/yash-dk) for implementation qBittorrent on Python
- [`VenomSnake`](https://github.com/venomsnake) for Snake Mirror bot