<h1 align="center">DEGPEG</h1>
<!-- <p align="center">
  <a href="https://jitpack.io/#degpeg-media/degpeg-b2c-sdk-android"> <img src="https://jitpack.io/v/degpeg-media/degpeg-b2c-sdk-android/month.svg"/></a>
  <a href="https://jitpack.io/#degpeg-media/degpeg-b2c-sdk-android"> <img src="https://jitpack.io/v/degpeg-media/degpeg-b2c-sdk-android.svg"/></a>
</p> -->

Degpeg is Live Commerce Platform with unique features like multi-streaming ( compatible with 30+ Social platforms ) for brands & content creators worldwide. The vision of Degpeg is to empower live streaming in a way that can be used not only to produce real-time content but build a meaningful business out of it, for content creators or advertisers or associated businesses like e-commerce, retail, education, gaming etc.

At Degpeg, we keep on improving our platform consistently to provide amazing live streaming experience to users, content creators and brand advertisers, which can increase engagement, brand outreach, retention rates & revenue generation. We can offer you an inclusive, collaborative atmosphere to develop your skills as part of a global multi-discipline development team with opportunities to be mentored by forward-thinking architects.

As part of product enhancements Degpeg is looking for vendors to support product development activities. Through this document the details of the requirements are outlined for which proposals are invited from vendors. As outlined in the Non-disclosure agreement contents of this document are strictly confidential to the vendor with whom the document is shared and degpeg.


# Features:

* Live video streaming
* On-Demand video play
* Automatically converted the live streaming video to on-demand video once the live stream is completed
* Schedule the upcoming events
* Support live chat, like, share
* Display the list of products with streaming content
* Shows the real time user watch count


# Preview

<p float="left">
<img src="https://github.com/degpeg-media/degpeg-b2c-sdk-android-example/blob/main/app/Dashboard.png" alt="dashboard" width="200" height="400"> 

<img src="https://github.com/degpeg-media/degpeg-b2c-sdk-android-example/blob/main/app/Player.png" alt="player" width="200" height="400"> 
</p>

# SDK initialization and setup

1. Add the JitPack repository to your project level build file

 ```groovy
allprojects {
    repositories {
        maven {
            url "https://jitpack.io"
        }
    }
}
```

2. Add the dependency to your app level build file 

```groovy
dependencies {
    implementation 'com.github.degpeg-media:degpeg-b2c-sdk-android:release_version'
}
```

(latest release_version : 1.0.2)

3. Create the Application class and extends Controller class. Also add the application class into the manifest.xml file.

Create the Application class
```kotlin
class AppController : Controller() {
    override fun onCreate() {
        super.onCreate()
    }
}
```
Add the application class into the manifest.xml file
```xml
<application android:name=".AppController">

</application>
```

4. Initialize SDK
```kotlin
DegpegSDKProvider.init(
    appId = appId,
    secretKey = secretKey,
    publisherId = publisherId,
    providerId = providerId,
    userRole = userRole,
    onSuccess = { },
    onError = {
        runOnUiThread { Toast.makeText(this, it, Toast.LENGTH_SHORT).show() }
    })
```

5. Provide the current user details
```kotlin
DegpegSDKProvider.updateUser(
    User(userName = "Dhaval Patel", userId = "6278c4556cb38a7a9c10df6e")
)
```

# Usage

* Use the SDK as activity
```kotlin
 DegpegSDKProvider.startAsActivity(
    activity = this,
    publisherId = publisherId
)
```

* Use the SDK as fragment
```kotlin
DegpegSDKProvider.useAsFragment(
    supportFragmentManager,
    binding.container.id,
    publisherId = publisherId
)
```
