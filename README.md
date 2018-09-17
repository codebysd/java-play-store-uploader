[![Build Status](https://travis-ci.org/codebysd/java-play-store-uploader.svg?branch=master)](https://travis-ci.org/codebysd/java-play-store-uploader)
[![Open issues](https://img.shields.io/github/issues/codebysd/java-play-store-uploader.svg)](https://github.com/codebysd/java-play-store-uploader/issues)
[![Pull requests](https://img.shields.io/github/issues-pr/codebysd/java-play-store-uploader.svg)](https://github.com/codebysd/java-play-store-uploader/pulls)
[![GitHub issues](https://img.shields.io/github/release/codebysd/java-play-store-uploader.svg)](https://github.com/codebysd/java-play-store-uploader/releases)


# Play Store Uploader

This is a simple tool to upload android apk builds to play store. 
Suitable for automation of play store uploads in a CI system.

## Requirements

1. Java (JRE) 8 or above

## Install

1. Download the latest zip or tar archive from [Releases Section](https://github.com/codebysd/java-play-store-uploader/releases).
2. Unpack archive contents to any location.
3. Execute the binaries in `bin` directory. On unix use `PlayStoreUploader`, while on windows use `PlayStoreUploader.bat`.

## Usage

### 1. Setup Play Store

Ensure that the app is created on Play Store. Setup Play Store listing and other required information so that release management is enabled and new releases can be published. It is advised to do a manual upload and release at least once in the beginning.

### 2. Setup Release Tracks

Play Store allows to upload apps on release tracks like alpha, beta and production. Enable and setup the track you want to use, on Play Store console.

### 3. Get Service Account Key

To access Play Store API a JSON key file is needed. On Play Store, goto API Access section and configure a service account with Play Store API access. Download and save the JSON credentials of this account.

### 4. Build apk file

Build signed production android apk file to upload. In case of a CI server, this file should be already generated.

### 4. Run Upload Command

Execute the binary, passing required data in arguments.

```bash
PlayStoreUploader -key "key.json" -apk "app.apk" -track "alpha" -name "myApp" -notes "new release"
```

#### CLI Options

Running without any arguments will print available argument options.

```bash
Options:
 -apk VAL       : The apk file to upload
 -key VAL       : JSON key file of authorized service account
 -name VAL      : (optional) App name on Play Store (defaults to name in apk)
 -notes VAL     : (optional) Release notes
 -notesFile VAL : (optional) Release notes from file
 -track VAL     : Release track to use. Eg. alpha, beta, production etc
 ```

## Development

To build:

```bash
./gradlew clean assemble
```

To run:

```bash
./gradlew run --args "...arguments"
```

Pull requests and suggestions are welcome.
