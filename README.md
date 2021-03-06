# hlsjs-UI

## Usage

```javascript
if (Hls.isSupported()) {
    var video = document.getElementById('video');
    var hls = new HlsUI({
        debug: true
    });
    // bind them together
    hls.attachMedia(video);
    hls.on(Hls.Events.MEDIA_ATTACHED, function() {
        console.log('video and hls.js are now bound together !');
        //hls.loadSource("https://storage.googleapis.com/shaka-demo-assets/angel-one-hls/hls.m3u8") //Direct, without meta data
        hls.loadSource({
            source: "https://storage.googleapis.com/shaka-demo-assets/angel-one-hls/hls.m3u8",
            title: "Angle One",
            live: true,
            qualityLabel: { // "bitrate": "Label",
                "482170": "144p",
                "784019": "240p",
                "1146764": "360p",
                "1410993": "480p",
                "1824731": "720p",
            },
            playbackRate: {
                "0.5": "0.5x",
                "1.0": "Normal",
                "2.0": "Double"
            },
            subtitle:[
              {
                url: "../sub/gk-en.srt",
                lang: "en",
                label: "",
                type: "srt" //srt | vvt
              },
              {
                url: "../sub/gk-hi.vtt",
                lang: "",
                label: "Subtitle", //lang must be ""
                type: "vtt" //srt | vtt
              }
            ]
        });
    });
}
```

Else Same as hlsjs Documentation https://github.com/video-dev/hls.js/blob/master/docs/API.md

# Credits
Thanks https://github.com/bazh/subtitles-parser for srt subtitle parser  
Thanks https://github.com/mozilla/popcorn-js/blob/master/parsers/parserVTT/popcorn.parserVTT.js for vtt subtitle parser
