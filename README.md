SDK Appaloosa Android
=====================

For android 2.1+

Main features of Appaloosa SDK
------------------------------

* Application auto-update: check if the application is up to date and install the latest version if not
* Application developer-panel: display a screen with information about the device and the application.

Installation
------------

### Maven way

If you use maven or any other tool with dependency management, add the following dependency :

       <dependency>
		<groupId>com.appaloosa-store</groupId>
	        <artifactId>appaloosa-android-sdk</artifactId>
	        <version>1.0</version>
		<type>apklib</type>
	</dependency>

Since the component is not on maven central, you will need to install the dependency first:

    mvn install:install-file -Dfile=<path-to-file> -DgroupId=com.appaloosa-store -DartifactId=appaloosa-sdk -Dversion=1.0.0 -Dpackaging=apklib

### Non Maven way

If you don't use maven, simply import the sdk as a maven android project and set it as a library reference in your project properties.

As the SDK is a maven project, it comes with some library dependency you may already have added in your project before. You will need to remove them to avoid duplicate jar errors.
Here is the list of library dependency :
 - robospice-spring-android (1.4.5)
 - robospice (1.4.5)
 - robospice-cache (1.4.5)
 - commons-lang3 (3.1)
 - commons-io (1.3.2)
 - spring-android-rest-template (1.0.1)
 - spring-android-core (1.0.1)
 - jackson-mapper-asl (1.9.11)
 - jackson-core-asl (1.9.11)
 - support-v4-r7 ==> Warning : If you need to use a newer version (eg: r13), you need to exclude this one.

Usage
-----

### Auto-update

In all cases, you need to configure a service in your AndroidManifest.xml in order to request the Appaloosa server asynchronously:

    <service android:name="com.octo.appaloosasdk.async.AppaloosaSpiceService" android:exported="false" />

You also need the following permisions (network state and internet to request Appaloosa services on internet, external storage to store the apk downloaded):

    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

Then you only need the following line in your code:

     Appaloosa.getInstance().autoUpdate(this, STORE_ID, STORE_TOKEN);
     
STORE_ID and STORE_TOKEN can be found in the Appaloosa console (in settings section).

Follow the settings link

![Settings link](https://raw.github.com/octo-online/appaloosa-android-sdk/master/images/appaloosa-store-settings-link.png)

STORE_ID and STORE_TOKEN are located at the bottom of this page

![store toek and store id](https://raw.github.com/octo-online/appaloosa-android-sdk/master/images/appaloosa-store-token-and-id.png)

If you want to go further, you can watch the sdk-test subproject to have 3 samples.

### Developer panel

The developer panel gives information about the device and the application.

![appaloosa dev panel screenshot](https://raw.github.com/octo-online/appaloosa-android-sdk/dev-panel/images/appaloosa-dev-panel-1.png)

You need to add the following activity in your AndroidManifest.xml :

    <activity android:name="com.octo.appaloosasdk.ui.activity.AppaloosaDevPanelActivity" android:exported="false" />

Then you only need the following line in your code:

    Appaloosa.getInstance().displayDevPanel(this); 

License
-------

  Copyright (C) 2012 Octo Technology (http://www.octo.com)
  
	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at
	
	     http://www.apache.org/licenses/LICENSE-2.0
	
	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
	See the License for the specific language governing permissions and
	limitations under the License.
