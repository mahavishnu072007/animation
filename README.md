# Ex.No: 6 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:
1. Design the UI: Create the layout with an ImageView and action buttons (Move, Blink, Fade, Rotate, Zoom, Slide, Stop).
2. Define Animations: Create animation XML files in res/anim/ defining property transformations (alpha, rotate, translate, scale).
3. Initialize Views: Link the UI components to Java objects in  MainActivity.java using findViewById().
4. Execute Animation: On clicking an animation button, load the XML animation via AnimationUtils and start it on the ImageView.
5. Stop Animation: On clicking the Stop button, clear all active transformations from the ImageView using clearAnimation().


## PROGRAM:
```
/*
Program to display animation operation”.
Developed by: MAHA VISHNU S
Registeration Number : 212225220059
*/
```
## Mainactivity.java
```
package com.example.animation;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare variables for ImageView and Buttons
    private ImageView imageView;
    private Button blink, rotate, fade, move, slide, zoom, stop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize ImageView and Buttons using their IDs
        imageView = findViewById(R.id.imageview);
        blink = findViewById(R.id.blink);
        rotate = findViewById(R.id.rotate);
        fade = findViewById(R.id.fade);
        move = findViewById(R.id.move);
        slide = findViewById(R.id.slide);
        zoom = findViewById(R.id.zoom);
        stop = findViewById(R.id.stop);

        // Set up click listeners for each button to start corresponding animations
        createAnimation(blink, R.anim.blink);
        createAnimation(rotate, R.anim.rotate);
        createAnimation(fade, R.anim.fade);
        createAnimation(move, R.anim.move);
        createAnimation(slide, R.anim.slide);
        createAnimation(zoom, R.anim.zoom);

        // Set up click listener for stop button to clear any ongoing animation
        stop.setOnClickListener(v -> imageView.clearAnimation());
    }

    // Function to set up an animation for a given view and animation resource ID
    private void createAnimation(View view, int animResId) {
        view.setOnClickListener(v -> {
            imageView.clearAnimation();
            // Load the animation from the specified resource ID
            Animation animation = AnimationUtils.loadAnimation(MainActivity.this, animResId);
            // Start the animation on the ImageView
            imageView.startAnimation(animation);
        });
    }
}

```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/background"
    android:fillViewport="true"
    tools:context=".MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="20dp"
        android:gravity="center_horizontal">

        <!-- Header -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:gravity="center"
            android:paddingTop="12dp"
            android:paddingBottom="16dp">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:letterSpacing="0.02"
                android:text="@string/app_title"
                android:textColor="@color/text_primary"
                android:textSize="24sp"
                android:textStyle="bold" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@string/app_subtitle"
                android:textSize="13sp"
                android:textColor="@color/text_secondary"
                android:layout_marginTop="4dp" />
        </LinearLayout>

        <!-- Animation Display Stage -->
        <com.google.android.material.card.MaterialCardView
            android:layout_width="220dp"
            android:layout_height="220dp"
            android:layout_marginTop="10dp"
            android:layout_marginBottom="24dp"
            app:cardCornerRadius="24dp"
            app:cardElevation="6dp"
            app:cardBackgroundColor="@color/card_bg"
            app:strokeWidth="1.5dp"
            app:strokeColor="@color/card_stroke">

            <FrameLayout
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:padding="20dp">

                <ImageView
                    android:id="@+id/imageview"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:contentDescription="@string/app_name"
                    android:scaleType="fitCenter"
                    android:src="@drawable/luffy" />
            </FrameLayout>
        </com.google.android.material.card.MaterialCardView>

        <!-- Animation Control Buttons Row 1 -->
        <LinearLayout
            android:id="@+id/linear1"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:weightSum="3"
            android:layout_marginBottom="12dp">

            <com.google.android.material.button.MaterialButton
                android:id="@+id/blink"
                android:layout_width="0dp"
                android:layout_height="54dp"
                android:layout_margin="6dp"
                android:layout_weight="1"
                android:text="@string/blink"
                android:textSize="12sp"
                android:textStyle="bold"
                android:textColor="@color/white"
                app:backgroundTint="@color/btn_blink_bg"
                app:cornerRadius="14dp"
                app:elevation="2dp" />

            <com.google.android.material.button.MaterialButton
                android:id="@+id/rotate"
                android:layout_width="0dp"
                android:layout_height="54dp"
                android:layout_margin="6dp"
                android:layout_weight="1"
                android:text="@string/clockwise"
                android:textSize="12sp"
                android:textStyle="bold"
                android:textColor="@color/white"
                app:backgroundTint="@color/btn_rotate_bg"
                app:cornerRadius="14dp"
                app:elevation="2dp" />

            <com.google.android.material.button.MaterialButton
                android:id="@+id/fade"
                android:layout_width="0dp"
                android:layout_height="54dp"
                android:layout_margin="6dp"
                android:layout_weight="1"
                android:text="@string/fade"
                android:textSize="12sp"
                android:textStyle="bold"
                android:textColor="@color/white"
                app:backgroundTint="@color/btn_fade_bg"
                app:cornerRadius="14dp"
                app:elevation="2dp" />
        </LinearLayout>

        <!-- Animation Control Buttons Row 2 -->
        <LinearLayout
            android:id="@+id/linear2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:weightSum="3"
            android:layout_marginBottom="20dp">

            <com.google.android.material.button.MaterialButton
                android:id="@+id/move"
                android:layout_width="0dp"
                android:layout_height="54dp"
                android:layout_margin="6dp"
                android:layout_weight="1"
                android:text="@string/move"
                android:textSize="12sp"
                android:textStyle="bold"
                android:textColor="@color/white"
                app:backgroundTint="@color/btn_move_bg"
                app:cornerRadius="14dp"
                app:elevation="2dp" />

            <com.google.android.material.button.MaterialButton
                android:id="@+id/slide"
                android:layout_width="0dp"
                android:layout_height="54dp"
                android:layout_margin="6dp"
                android:layout_weight="1"
                android:text="@string/slide"
                android:textSize="12sp"
                android:textStyle="bold"
                android:textColor="@color/white"
                app:backgroundTint="@color/btn_slide_bg"
                app:cornerRadius="14dp"
                app:elevation="2dp" />

            <com.google.android.material.button.MaterialButton
                android:id="@+id/zoom"
                android:layout_width="0dp"
                android:layout_height="54dp"
                android:layout_margin="6dp"
                android:layout_weight="1"
                android:text="@string/zoom"
                android:textSize="12sp"
                android:textStyle="bold"
                android:textColor="@color/white"
                app:backgroundTint="@color/btn_zoom_bg"
                app:cornerRadius="14dp"
                app:elevation="2dp" />
        </LinearLayout>

        <!-- Stop Animation Button -->
        <com.google.android.material.button.MaterialButton
            android:id="@+id/stop"
            style="@style/Widget.Material3.Button.OutlinedButton"
            android:layout_width="match_parent"
            android:layout_height="54dp"
            android:layout_marginStart="6dp"
            android:layout_marginEnd="6dp"
            android:text="@string/stop_animation"
            android:textSize="14sp"
            android:textStyle="bold"
            android:textColor="@color/btn_stop_bg"
            app:strokeColor="@color/btn_stop_bg"
            app:strokeWidth="1.5dp"
            app:cornerRadius="14dp" />

    </LinearLayout>
</ScrollView>

```
## blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500"
        android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```
## rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />

    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />

</set>
```
## fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <alpha
        android:fromAlpha="1.0"
        android:toAlpha="0.1"
        android:duration="1000"
        android:repeatCount="1"
        android:repeatMode="reverse" />
</set>

```
## move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <translate
        android:fromXDelta="-25%p"
        android:toXDelta="25%p"
        android:fromYDelta="0%p"
        android:toYDelta="0%p"
        android:duration="1000"
        android:repeatCount="1"
        android:repeatMode="reverse" />
</set>

```
## slide.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <translate
        android:fromYDelta="-100%p"
        android:toYDelta="0%p"
        android:duration="800" />
</set>

```
## zoom.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >

    <scale
        android:interpolator="@android:anim/linear_interpolator"
        android:duration = "1000"
        android:fromXScale = "1"
        android:fromYScale = "1"
        android:pivotX = "50%"
        android:pivotY = "50%"
        android:toXScale = "2"
        android:toYScale = "2"/>
</set>
```
## strings.xml
```
<resources>
    <string name="app_name">AnimLab Studio</string>
    <string name="app_title">Animation Studio</string>
    <string name="app_subtitle">Select an operation to animate the view</string>
    <string name="blink">BLINK</string>
    <string name="clockwise">ROTATE</string>
    <string name="fade">FADE</string>
    <string name="move">MOVE</string>
    <string name="slide">SLIDE</string>
    <string name="zoom">ZOOM</string>
    <string name="stop_animation">STOP ANIMATION</string>
    <string name="course_rating">Course Rating</string>
    <string name="course_name">Course Name</string>
</resources>
```


## OUTPUT
## 1. activity_main.xml
<img width="1917" height="1078" alt="Screenshot 2026-11-18 104914" src="https://github.com/user-attachments/assets/65672409-cef5-4242-8a8d-bfa40de9e15c" />

## 2. Blink
<img width="1917" height="1078" alt="Screenshot 2026-11-18 104944" src="https://github.com/user-attachments/assets/8038bc1f-9789-4167-ab77-fa34a314110a" />

## 3. Rotate
<img width="1917" height="1075" alt="Screenshot 2026-11-18 105002" src="https://github.com/user-attachments/assets/f7d249a3-aedd-4a9d-b876-da84b39b318a" />

## 4. Fade
<img width="1917" height="1078" alt="Screenshot 2026-11-18 105030" src="https://github.com/user-attachments/assets/059e4e2e-e51d-444d-9c3c-c1b940c62f7d" />

## 5. Move
<img width="1917" height="1078" alt="Screenshot 2026-11-18 105040" src="https://github.com/user-attachments/assets/5cab4efb-c366-4c57-88c8-fba4f5a9c1fe" />

## 6. slide
<img width="1917" height="1078" alt="Screenshot 2026-11-18 105051" src="https://github.com/user-attachments/assets/5957d612-c202-4e17-9a7a-3a022f56feea" />

## 7. zoom
<img width="1917" height="1078" alt="Screenshot 2026-11-18 105059" src="https://github.com/user-attachments/assets/ee302227-4c2e-4a2a-b2e4-6541d0ed9df1" />




## RESULT

The Android application for ImageView animations was successfully implemented, tested, and uploaded to the GitHub repository along with source code and UI output screenshots. All six animation operations (Move, Blink, Fade, Rotate, Zoom, and Slide) execute smoothly on the ImageView upon user interaction, with full support to clear animations via the Stop button.
