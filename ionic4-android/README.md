## Ionic4 Development Container

## Setup

Download android-accept-licenses.sh, save it under the tools folder and add execute permissions before using this Dockerfile.

```
mkdir tools
cd tools
wget https://raw.githubusercontent.com/oren/docker-ionic/master/tools/android-accept-licenses.sh
chmod +x android-accept-licenses.sh
```


### Built the Image

```
# tagname can be something like 1.0
docker build -t spopp/ionic4-android:tagname .
```

### Push Image to docker hub

```
docker push spopp/ionic4-android:tagname
```


## Create an Ionic4 Application

Create App

```
# One time install
npm install -g ionic

# Create Example app with tab layout
ionic start exampleApp tabs --type=angular
```


Build

```
ionic cordova build android --prod --no-interactive --release
```


## Run on Android

* Android device connected by USB in developer mode

Open bash terminal to container

```
docker run -it --privileged --volume=$(pwd):/opt/workspace ionic4-android bash
```

On the container execute to open the application in your phone

```
./gradlew installDebug
```

## Run web app in container

```
ionic serve
```

open <http://localhost:8100>
