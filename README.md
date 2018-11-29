![alt text](https://github.com/mumayank/AirLocation/blob/master/image.png "Logo")

# AirLocation

An Android library which simply gets you user's most accurate current location. Period.
+ Location is accurate up to 7 decimal places (highest accuracy)
+ No need to add any permissions in manifest
+ No need to add google play services location lib in gradle
+ Simple plug and play design.

Method counts ~50

Size ~50KB

[![](https://jitpack.io/v/mumayank/AirLocation.svg)](https://jitpack.io/#mumayank/AirLocation)

# Setup

Add this line in your root build.gradle at the end of repositories:

```gradle
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' } // this line
  }
}
  ```
Add this line in your app build.gradle:
```gradle
dependencies {
  implementation 'com.github.mumayank:AirLocation:LATEST_VERSION' // this line
}
```
where LATEST_VERSION is [![](https://jitpack.io/v/mumayank/AirLocation.svg)](https://jitpack.io/#mumayank/AirLocation)

# Usage

+ The activity in which you want to fetch location, must extend `AirLocationActivity` (FYI: AirLocationActivity extends AppCompatActivity)

+ Everytime you want to fetch location, just initialize `airLocation` variable (available from parent class `AirLocationActivity`)

Example:

```kotlin
airLocation = AirLocation(this, true, true, object: AirLocation.Callbacks {
                override fun beforeStart() {
                    // do something like show progress bar
                }

                override fun onComplete() {
                    // do something like hide progress bar, as this is called on both: onSuccess and onFailure
                }

                override fun onSuccess(location: Location) {
                    // do something like use this location
                }

                override fun onFailed(locationFailedEnum: AirLocation.LocationFailedEnum) {
                    // do something if required
                }

            })
```

+ If you ever `override` `onActivityResult` or `onRequestPermissionsResult` functions in your activity, then you must call their respective super functions.
