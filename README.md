# voice-dfki-pavoque-styles

A male German unit selection voice built from from the [PAVOQUE Corpus of Expressive Speech](https://github.com/marytts/pavoque-data)

This voice provides different expressive styles, which can be triggered by wrapping a `RAWMARYXML` request into a `prosody` element:
```xml
<prosody style="STYLE">...</prosody>
```
where `STYLE` is one of *happy*, *angry*, *sad*, or *poker*.
See [Steiner et al. (2010)](http://www.isca-speech.org/archive/ssw7/ssw7_114.html) for details.

## Prerequisites

You will need to have [Java](https://www.java.com/), [Praat](http://praat.org/), [SoX](http://sox.sourceforge.net/), and the [Edinburgh Speech Tools](http://www.cstr.ed.ac.uk/projects/speech_tools/) installed.

On OSX with [Homebrew](http://brew.sh/), do
```
$ brew cask install java praat
$ brew install sox speech-tools
```
as needed.

On Debian-based Linux (including Ubuntu), do
```
$ sudo apt-get install default-jdk praat sox speech-tools
```
accordingly.

You will also need to have SSH configured to access **cloudark**.

### Initializing the build

Do
```
$ ./gradlew legacyInit
```

### Building the voice

To assemble, test, and package the voice for another MaryTTS installation, do
```
$ ./gradlew build
```
The packaged files will be placed under `build/distributions`.
Copy the zip file and xml descriptor into your MaryTTS installation's `download` directory, then run the `marytts-component-installer` to install the voice.

### Running the voice

To build the voice and run it in an ad-hoc MaryTTS server, do
```
$ ./gradlew run
```
Then, go to [http://localhost:59125](http://localhost:59125/).
