# Xamarin-Plugins
Cross-platform Plugins for Xamarin and Xamarin.Forms

## SimpleAudioPlayer
SimpleAudioPlayer plays audio data as a stream. This allows you to store audio data in a portable class library and play it on all supported platforms.

### Supported Platforms
v0.9.0 supports Xamarin.iOS, Xamarin.Android and UWP
v0.9.9 adds Xamarin.Mac support

### Public Properties

**Duration**: length of audio in seconds

**CurrentPosition**: current playpack position in seconds

**Volume**: volume of audio between 0 and 1

**Balance**: balance between left and right as as double, -1 is left only, 0 is both, +1 is right only

**IsPlaying**: is the audio currently playing

**CanSeek**: can the playback position be updated

### Public Methods

**Load(Stream audioStream)**: load a compatible (wav, mp3, etc) audio from a stream

**Load(string fileName)**: load a compatible audio file stored in the executing platform project

**Play()**: play the currently loaded audio 

**Stop()**: stop playback and reset current position to start (0)

**Pause()**: pause playback (use Play() to resume)

**Seek(double position)**: seek to a specific location in the audio (in seconds)


### Example
Coded in the shared PCL using the Xamarin.Forms dependancy service
with **mysound.wav** stored in the PCL as an **Embedded Resource**
```
ISimpleAudioPlayer player = Plugin.SimpleAudioPlayer.CrossSimpleAudioPlayer.Current;
player.Load(GetStreamFromFile("mysound.wav"));
player.Play();
```

Or to load multiple instances
```
var player1 = Plugin.SimpleAudioPlayer.CrossSimpleAudioPlayer.CreateSimpleAudioPlayer();
var player2 = Plugin.SimpleAudioPlayer.CrossSimpleAudioPlayer.CreateSimpleAudioPlayer();
...
```

For more examples see the **Samples** folder or check out
https://github.com/adrianstevens/Xamarin-Forms/tree/master/DrumPad2
