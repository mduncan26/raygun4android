# Raygun4Android

The world's best Android crash reporter.

## Installation

### With Maven

To your pom.xml, add:

```xml
<dependency>
    <groupId>com.mindscapehq.android</groupId>
    <artifactId>raygun4android</artifactId>
    <version>1.0.0</version>
</dependency>
```

In your IDE, build your project (or run `mvn compile`), then see the configuration section below.

## With Ant, other build tools, or manually

Download the JAR and place it in a /lib folder in your project. Add it to your project's classpath, then see below.

## Configuration & Usage

1. In your **AndroidManifest.xml**, make sure you have granted Internet permissions: `<uses-permission android:name="android.permission.INTERNET" />` (beneath the **manifest** element)

2. Inside the **application** element, add:

```xml
<meta-data android:name="com.mindscapehq.android.raygun4android.apikey"
                   android:value="PASTE_YOUR_API_KEY_HERE" />
```

3. In a central location, call `RaygunClient.Init()`, passing in your activity's context.

4. When an exception occurs, such as in a catch block, call RaygunClient.Send(), passing in the Throwable. This will send it to the Raygun service, where it will be viewable in the dashboard.

## Documentation

The following method overloads are available for initializing RaygunClient:

* RaygunClient.Init(Context context)

* RaygunClient.Init(String version, Context context)

* RaygunClient.Init (Context context, String apiKey)

* RaygunClient.Init (Context context, String apiKey, String version)

The following methods are available for sending; pick one depending on how much extra data you'd like to send:

* RaygunClient.Send(Throwable throwable)

* RaygunClient.Send(Throwable throwable, AbstractList tags)

* RaygunClient.Send(Throwable throwable, AbstractList tags, Map userCustomData)

These build a RaygunMessage for you then send it. If you'd like to build a message manually you can use:

* RaygunClient.Post(RaygunMessage raygunMessage)

Note that this will require certain fields to be present - documentation is available at http://raygun.io/raygun-providers/rest-json-api

### Frequently Asked Questions

* Environment Data

	A selection of enironment data will be attached and available in the Environment tab in the dashboard, and more in the Raw tab. This data is gathered from android.os.Build - if you wish to see more data you can add them on the userCustomData object.

### Contributing

Clone this repository, then run `mvn install` to grab the dependencies and install the library to your local Maven repo. Runs with Android 2.2 (API level 8) and JDK 1.6


## Changelog

Version 0.0.1: Initial release with basic functionality.