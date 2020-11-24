# Hotmart Course Downloader
## A Chrome extension to single-click download all videos from a Hotmart course.

## It works only if the course uses one of the native hotmart players. It's not supposed to work on 3rd party embedded players (like vimeo's).

### This project is still in development.
### I am not responsible for the misuse of this project. I do not encourage or support the use of this project for the purposes of piracy or unauthorized distribution of any hotmart content. This project was made in order to study some concepts of javascript and web programming.
### It uses the decrypt class from [hls.js](https://github.com/video-dev/hls.js), to decrypt AES-128 crypted MPEG-TS files.
#### 1 - How to install
**1.1** - Type "chrome://extensions", on chrome's url field;

**1.2** - Enter in Development Mode, by pressing the button on the top right;

**1.3** - Press on the "load unpacked extension", on the top left;

**1.4** - Find the HotmartCourseDownloader folder.

**You need to install [VLC](https://www.videolan.org/) or any player that supports MPEG-TS encoding, to be able to play the downloaded videos (better explanation at the "to do" section).**

#### 2 - How to use
**2.1** - Go to the first class of your course (you need to be logged, and own it, ofc)

**2.2** - Press the extension button, and wait 10s (if the player is the "Midnight" one, the one that looks like theater mode, you need to press play before pressing the extention button)

**2.3** - The extension will start to download it, and once done, it will save at "your default download folder/course name/module name/video name.mp4". 
**You can see the download progress on the extention background script console.** Once done, it will go to the next class and repeat.

#### 3 - Messages, download progress and how to find the extension backgroud script console
To see the user messages and download progress, you need to access the background script console. To find it, do the following:

**3.1** - Type chrome://extensions/ on the url field and press enter;

**3.2** - Look for the extention and click on its "background.html", that will appear as a link, in blue;

**3.3** - Go to the tab "console" on the window that will show up.

**3.4** - Done. All the messages and download progress appear on this window.

#### 4 - Features

The extention will:

- Find the class name, module name, course name, current url, current video hash, next video hash and the video id, on the page DOM;
- Replace the current video hash on the current url, with the next video hash, to create the next video url;
- From the video id, request the master.m3u8 playlist;
- From the master playlist, get all avaiable resolutions;
- Request a 720p or better segment list;
- From the segment list, get the key hash and the all the AES-128 crypted MPEG-TS segments;
- Request the actual key;
- Request and decrypt all those segments with the key;
- Merge them, and once merged, it will download as a single ".mp4" file.
- Then, move to the next class on the playlist, using the next video url, created at the beginning.

#### 5 - To do
- [ ] Find a way to encode the final .mp4 file to a "true" .mp4 format (at the moment it's just a bunch of .ts files concatenated, thats why you need to download VLC to play them);
- [ ] The "front-end" (popup, options, user messages and errors);
- [ ] Names and icons;
