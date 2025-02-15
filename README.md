# youtube-dl-server

**This is a fork that will return the streamable MP3 link for a YouTube video (or anything youtube-dl supports that (1) includes MPEG-DASH and (2) includes the MP3 file as the first item in the list)**

Usage example:

```
https://youtube-mp3-stream-url.herokuapp.com/v1/video?url=https://music.youtube.com/watch?v=LvyHVgocP_0&list=RDAMVMLvyHVgocP_0
```

A youtube-dl web server, powered by youtube-dl.

Intended to provide raw video url and other metadata as a json payload, not as a streaming server.

## Getting started
```
npm install
npm start
```

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

## API

```
GET /v1/video?url=<YOUTUBE_URL_HERE>&options=<OPTIONS>&schema=KEY1&schema=KEY2

Returns a json payload with requested information.

- url: required - Url of youtube video
- options: optional - options to be passed to youtube-dl. Defaults to -f "best". See https://github.com/ytdl-org/youtube-dl/blob/master/README.md
- schema: optional - array of keys to be returned, to avoid returning all the json dump from youtube-dl. E.g. /v1/video?url=https://www.youtube.com/watch?v=1PuGuqpHQGo&schema=url&schema=title


----

GET /watch?v=<YOUTUBE_VIDEO_ID_HERE>&options=<OPTIONS>

Redirects to the raw video url.

- v: required - Url or ID of the video, same as the url parameter of GET /v1/video
- options: optional - options to be passed to youtube-dl. Defaults to -f "best". See https://github.com/ytdl-org/youtube-dl/blob/master/README.md
```
