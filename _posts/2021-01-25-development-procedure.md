---
title: "Development Procedure"
description: 15
---

The following steps will show you how to use **FaceView** and **ARView**

<aside class="special">
	<p><strong>Note:</strong> 
    <p>All materials must be stored in the <strong>assets</strong> directory.</p>
 <p>Assets can be created using 3D building tools. Following extensions are supported in FaceView and ARView: </p>
    <li>.glb</li>
    <li>.gltf</li>
 <p>You can convert your .obj or .max files to supported files easily by using online converters.</p></p>
</aside> 

### FaceView

1. Create a FaceViewActivity that inherits from Activity.

   <pre><div id="copy-button21" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>class FaceViewActivity : Activity(), OnSelectedListener {
   }<span class="pln">
   </span></code></pre>

2. Add a FaceView to the layout.

   <pre><div id="copy-button1" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
   <com.huawei.hms.scene.sdk.FaceView
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:id="@+id/faceView"
       app:sdk_type="AR_ENGINE">
   </com.huawei.hms.scene.sdk.FaceView>
   <span class="pln">
   </span></code></pre>

3. Override the **onSelected** method in **FaceViewActivity** to place selected mask to the face.

   <pre><div id="copy-button2" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>faceView.clearResource()
   // Load materials.
   val index: Int = faceView.loadAsset("FaceView/${item.path}.glb", LandmarkType.TIP_OF_NOSE)
   // (Optional) Set the initial status.
   faceView.setInitialPose(index, position, scale, rotation)}});<span class="pln">
   </span></code></pre>

4. Override the **onPause** method of **FaceViewActivity** and call the **onPause** method of the FaceView.

   <pre><div id="copy-button3" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>override fun onPause() {
       super.onPause()
       faceView.onPause()
   }<span class="pln">
   </span></code></pre>

5. Override the **onResume** method of **FaceViewActivity** and call the **onResume** method of the FaceView.

   <pre><div id="copy-button4" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>override fun onResume() {
       super.onResume()
       faceView.onResume()
   }<span class="pln">
   </span></code></pre>

6. Override the **onDestroy** method of **FaceViewActivity** and call the **destroy** method of the FaceView.

   <pre><div id="copy-button5" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>override fun onDestroy() {
       super.onDestroy()
       faceView.destroy()
   }<span class="pln">
   </span></code></pre>

### ARView

1. Create an **ARViewActivity** that inherits from **Activity**.

   <pre><div id="copy-button6" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>class ARViewActivity : Activity(), OnSelectedListener {
   }<span class="pln">
   </span></code></pre>

2. Add an **ARView** to the layout.

   <pre><div id="copy-button7" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><com.huawei.hms.scene.sdk.ARView
       android:id="@+id/arView"
       android:layout_width="match_parent"
       android:layout_height="match_parent">
   </com.huawei.hms.scene.sdk.ARView>
   <span class="pln">
   </span></code></pre>

   <aside class="special">
   	<p><strong>Note:</strong> 
       <p>To achieve expected ARView experience, your app should not support screen orientation change or split-screen mode; thus, add the following configuration in the AndroidManifest.xml file:</p></aside>
   <pre><div id="copy-button8" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>android:screenOrientation="portrait"
   android:resizeableActivity="false"<span class="pln"></span></code></pre>

3. Override the **onCreate** method in **ARViewActivity** to call **setUI** method. In **setUI** method enable plane display.

   <pre><div id="copy-button9" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//Before choosing a furniture enablePlaneDisplay and move the phone to find the plane
   arView.enablePlaneDisplay(true)
   Toast.makeText(
       this,
       "Please move the mobile phone slowly to find the plane",
       Toast.LENGTH_LONG
   ).show()<span class="pln"></span></code></pre>

4. Override the **onSelected** method in **ARViewActivity** to place selected furniture to the plane.

   <pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>// Clear the resources loaded in the ARView.
   arView.clearResource()
   // Load the asset
   arView.loadAsset("ARView/${item.path}.glb")
   // (Optional) Set the initial status.
   arView.setInitialPose(scale, null)<span class="pln"></span></code></pre>

5. Override the **onPause** method of **ARViewActivity** and call the **onPause** method of the ARView.

   <pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>override fun onPause() {
       super.onPause()
       arView.onPause()
   }<span class="pln"></span></code></pre>

6. Override the **onResume** method of **ARViewActivity** and call the **onResume** method of the ARView.

   <pre><div id="copy-button12" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>override fun onResume() {
       super.onResume()
       arView.onResume()
   }<span class="pln"></span></code></pre>

7. Override the **onDestroy** method of **ARViewActivity** and call the **destroy** method of the ARView.

   <pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>override fun onDestroy() {
       super.onDestroy()
       arView.destroy()
   }<span class="pln"></span></code></pre>

### **Customizing 3D Materials**

1. When **FaceView** loads a material through the **loadAsset()** method, use **Landmark** to specify a marker position for applying a 3D cartoon.

   <pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>val index: Int = faceView.loadAsset("FaceView/${item.path}.glb", LandmarkType.TIP_OF_NOSE)<span class="pln"></span></code></pre>

   <aside class="special">
   <p><strong>Note:</strong></p>
   <p>The marker position can be any of the five positions, including nose tip, left or right eye, and left or right corner of the mouse</p></aside>

2. Set the initial status of the loaded material.

   - In an **ARView**, you can set the initial rotation angles and scaling coefficients of a     material.

     <pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>val scale = floatArrayOf(0.4f, 0.4f, 0.4f)
     val rotation = floatArrayOf(-1.0f, 0.0f, 1.0f, 0.0f)<span class="pln"></span></code></pre>

   - In a **FaceView**, you can set the initial position, rotation angles, and scaling coefficients of a material.

     <pre><div id="copy-button16" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>val position = floatArrayOf(0.0f, 0.0f, 0.0f)
     val rotation = floatArrayOf(1.0f, 0.0f, 0.0f, 0.0f)
     val scale = floatArrayOf(0.45f, 0.45f, 0.45f)<span class="pln"></span></code></pre>
