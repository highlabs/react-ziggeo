## Ziggeo's React component v2
(For documentation on v1, see [here](https://github.com/Ziggeo/react-ziggeo/tree/master/docs/v1))

We have a demo project [here](https://github.com/Ziggeo/react-ziggeo/tree/master/demo) for you to clone.

## Video Recorder

```$xslt
import React from 'react'
import {ZiggeoRecorder} from 'react-ziggeo'
...
 
    recorderRecording = () => {
        console.log('Recorder onRecording');
    };

    recorderUploaded = () => {
        console.log('Recorder onUploaded');
    };
 
...
 
    <ZiggeoRecorder
        apiKey={API_KEY}
        video={VIDEO_TOKEN}
        height={180}
        width={320}
        onRecording={this.recorderRecording}
        onUploading={this.recorderUploading}
    />
 
...
```
[All Built-in Recorder Events](https://github.com/Ziggeo/react-ziggeo/#available-events-for-recorder)

##### Available `event listeners` for Recorder

```react2html
   
   - onPlaying
   - onPaused
   - onAttached
   - onLoaded
   - onEnded
   - onSeek 
   - onError
   - onManuallySubmitted
   - onUploaded
   - onUploadSelected
   - onRecording
   - onUploading
   - onRerecord,
   - onCountdown,
   - onRecordingProgress,
   - onUploadProgress,
   - onAccessForbidden,
   - onAccessGranted,
   - onCameraUnresponsive,
   - onVerified,
   - onNoCamera,
   - onNoMicrophone
```


## Video Player

```$xslt
import React from 'react'
import {ZiggeoPlayer} from 'react-ziggeo'
 
...
 
playing = () => {
    console.log('it\'s playing, your action here');
};
 
paused = () => {
    console.log('it\'s paused, your action when pause');
};
 
...
    <ZiggeoPlayer
      apiKey={'your api key provided by ziggeo'}
      video={'Video Token'}
      theme={'modern'}
      themecolor={'red'}
      skipinitial={false}
      onPlaying={this.playing}
      onPaused={this.paused}
      ...
    />
...
```
[All Built-in Player Events](https://github.com/Ziggeo/react-ziggeo/#available-events-for-player)

##### Available `events listeners` for Player
```react2html
   
   - onPlaying
   - onPaused
   - onAttached
   - onLoaded
   - onEnded
   - onError
   - onSeek 
```

#### Extensions

##### Get Recorder Instance and invoke `methods`
Add attribute `onRef={ref => (this.child = ref)}` to obtain access to recorder instances and their methods.

```javascript
    <ZiggeoRecorder
        apiKey={apiToken}
        onRef={ref => (this.child = ref)}
    />
```
Now you can call built-in methods:
```javascript
    this.child.get(args);
    this.child.play();
    this.child.record();
    this.child.upload();
    this.child.rerecord();
    this.child.stop();
    this.child.hidePopup();
    this.child.reset();
```
Also you can also obtain an instance:
```
    let recorderInstance = this.child.recorderInstance();
    // e.g. call: playerInstance.play();
    let properties = this.playerInstance.get('propertyName');
```

##### Get Recorder Instance and invoke `methods`
Add attribute `onRef={ref => (this.child = ref)}` to obtain access to player instances and their methods.

```javascript
    <ZiggeoPlayer
        apiKey={apiToken}
        video={videoToken}
        onRef={ref => (this.child = ref)}
    />
```
Now you can call built-in methods:
```javascript
    this.child.play();
    this.child.pause();
    this.child.stop();
    this.child.seek(seconds);
    this.child.set_volume(volume_level_1_to_100);
```
Also you can also obtain an instance:
```
    let playerInstance = this.child.playerInstance();
    // e.g. call: playerInstance.play();
    let properties = this.playerInstance.get('propertyName');
```

## Component Options
```javascript
    preventReRenderOnUpdate={boolean} // default is true
```

## Notes
By default, components prevent re-rendering the UI with the option `preventReRenderOnUpdate`, to overwrite this.
```javascript
    <ZiggeoRecorder
        preventReRenderOnUpdate={false}
    />
```
There are some issues with when being called right after initialization.


#### Additional Parameters

React SDK supports all of the following events and parameters:
- [Ziggeo Available Parameters](https://ziggeo.com/docs/sdks/javascript/browser-integration/parameters)
- [Ziggeo Available Embedding Events](https://ziggeo.com/docs/sdks/javascript/browser-interaction/events)
