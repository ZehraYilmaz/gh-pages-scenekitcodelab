---
title: "Integration Preparations"
description: 4
---

Scene Kit works only depending on the device, without connecting to HUAWEI AppGallery Connect.

1. Open Android Studio, go to **File** > **Open**, and select the directory where the **SceneKitDemo** sample code has been decompressed.

   <div style="padding: 5px">
           <img style="width: 100.00px ; padding: 5px" src="https://raw.githubusercontent.com/ZehraYilmaz/gh-pages-scenekitcodelab/gh-pages/assets/scenekit_codelab_doc_ss_1.png">
           <img style="width: 100.00px ; padding: 5px" src="https://raw.githubusercontent.com/ZehraYilmaz/gh-pages-scenekitcodelab/gh-pages/assets/scenekit_codelab_doc_ss_2.png">
   </div>

2. Make sure that the Maven repository address, dependency package, permission, and obfuscation script are correctly configured. These items have been configured in the **SceneKitDemo** sample code. Modify them as needed in your own project.

   Configure the Maven repository address in the project-level **build.gradle** file.

   <pre><div id="copy-button17" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>buildscript {
       repositories {
           ...
           maven { url 'https://developer.huawei.com/repo/' }
       }
       ...
   }
   allprojects {
       repositories {
           ...
           maven { url 'https://developer.huawei.com/repo/' }
       }
   }<span class="pln">
   </span></code></pre>

   Configure the dependency package in the app-level **build.gradle** file.

   <pre><div id="copy-button18" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>dependency {
       ...
       implementation 'com.huawei.scenekit:sdk:{version}'
   }<span class="pln">
   </span></code></pre>

   The SDK of Scene Kit is used above. You can also use the Full-SDK as follows:

   <pre><div id="copy-button19" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>dependency {
       ...
       implementation 'com.huawei.scenekit:full-sdk:{version}'
   }<span class="pln">
   </span></code></pre>

   <aside class="special">
   	<p><strong>Note:</strong> 
    <p>Replace {version} with the latest version number, currently 5.0.2.302.</p>
    <p>implementation 'com.huawei.scenekit:sdk:5.0.2.302'</p>
    <p>implementation 'com.huawei.scenekit:full-sdk:5.0.2.302'</p></p>
   </aside> 

3. In the **app/proguard-rules.pro** file, make necessary obfuscation configurations.

   <pre><div id="copy-button20" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>-ignorewarnings
   -keepattributes *Annotation*
   -keepattributes Exceptions
   -keepattributes InnerClasses
   -keepattributes Signature
   -keepattributes SourceFile,LineNumberTable
   -keep class com.hianalytics.android.**{*;}
   -keep class com.huawei.updatesdk.**{*;}
   -keep class com.huawei.hms.**{*;}<span class="pln">
   </span></code></pre>
