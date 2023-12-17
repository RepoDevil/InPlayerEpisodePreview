In Player Episode Preview
====================

## About ##
This plugin adds an episode list to the video player, which allows you to preview every episode of the TV show without having to leave the player.

This plugin currently 100% client sided and works with the following clients:
* Jellyfin Web Client
* Jellyfin Media Player (JMP) Desktop Client

### Features ###
* List all episodes of a season
* Switch between seasons
* Show episode title, description, thumbnail and playback progress
* Start a new episode (only on the desktop client)

## Preview ##



## Installation ##

#### Jellyfin Web Client (Server) ####

NOTE: If you are using docker there could be permission issues while injection the script. 
Jellyscrub works in a similar fashion, checkout their [readme](https://github.com/nicknsy/jellyscrub/blob/main/README.md) for more information.

1. Add the manifest `https://raw.githubusercontent.com/Namo2/InPlayerEpisodePreview/master/manifest.json` as a Jellyfin plugin repository to your server.
2. Install the plugin `InPlayerEpisodePreview` from the repository.
3. Restart the Jellyfin server.

#### Jellyfin Media Player (JMP) Desktop Client ####

This is the recommended way to install the script on the desktop client.
If you don't feel comfortable editing the nativeshell.js file yourself (step 3 to 6), you can download the full release instead, which includes the script already added to the nativeshell.js file.
It is yet unclear if there could be potential issues, replacing the nativeshell.js file with the one from the release, so it is recommended to follow all steps below.

1. Download the latest release from https://github.com
2. Extract the zip file into your Jellyfin directory (e.g. C:\Program Files\Jellyfin\Jellyfin Media Player)
3. Inside your Jellyfin directory follow the folder path "web-client\extension"
4. Open the "nativeshell.js" file in a text editor.
5. Inside the file find the section `const plugins = [];`. Add a new line at the start of the list and paste in `'inPlayerPreviewPlugin',`. The section should now look similar to this:
```javascript
const plugins = [
    'inPlayerPreviewPlugin',
    'mpvVideoPlayer',
    'mpvAudioPlayer',
    'jmpInputPlugin',
    'jmpUpdatePlugin',
    'jellyscrubPlugin',
    'skipIntroPlugin'
];
```
6. Save the file and restart the JMP client.

## Drawbacks ##
* The plugin will download some extra data like the episode description.
* It is not possible to start another episode on the web client.

## Credits ##
The plugin structure is based and inspired on the [Jellyscrub](https://github.com/nicknsy/jellyscrub) plugin by [NickNSY](https://github.com/nicknsy).