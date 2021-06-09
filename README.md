# TwitchClipsUploader
The goal of the project is to find the most popular daily clips on Twitch and upload them on youtube. Here is the link to the youtube channel: https://www.youtube.com/channel/UCvze_SaWLEjeF-H-CdP2Htw 
# About the project:
At first I wanted to upload 10 clips from the 10 top categories of the day, but i found out that youtube api quota lets you use a maximum 10 000 units of api calls per day. And uploading a video consumes 1600 units, so you can only upload 6 videos per day. So now it only uploads the top 6 clips of the day.
# How it works:
The script first uses the twitch api to find the 6 most popular clips of the previous day. Takes the clips url, title and the channels url. Then it uses https://github.com/ytdl-org/youtube-dl to convert the clips url to an mp4 url and sets the videos description, title, tags and so on. After that we can upload it to youtube with https://github.com/jonnekaunisto/simple-youtube-api. The script is hosted on https://www.heroku.com and is pinged using https://cron-job.org/en/ every day at 12AM, the code uploads 6 clips to youtube then goes back to sleep to preserve Heroku dyno usage. If I had a verified Heroku account I wouldn't need to use cron jobs, as I could use the free Heroku Scheduler.
# How to use:
1. First fork this repository.
2. Change the app.json to suit your project
3. Follow the guide here: https://support.google.com/cloud/answer/6158849?hl=en#zippy=%2Cuser-consent%2Cpublic-and-internal-applications%2Cauthorized-domains. And download the client secret key to your forked repository.
4. Download the Youtube Data API v3 in your API library.
5. Create a twitch aplication here: https://dev.twitch.tv/console/apps. Set the name, set the Oauth Redirect URL to https://localhost, set the category to Analytics tool.
6. Open the TwitchClipsUploader.py script and set the variable ClientID to your Twitch application client ID.
7. Complete the youtube audit form here: https://support.google.com/youtube/contact/yt_api_form?hl=en (If you don't do this your videos will be set to private)
8. Deploy to heroku:
<a href="https://heroku.com/deploy?template=https://github.com/Luscsus/TwitchClipsUploader">
  <img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy">
</a>



WORK IN PROGRESS
