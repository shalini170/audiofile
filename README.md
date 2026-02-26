# Ex.No:3 Develop a simple application to play and control the audio file in android studio.


## AIM:

To develop a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as audiofile and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml and create start,pause and stop button.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to play and control the audio file”.
Developed by: shalini venkatesulu
Registeration Number : 212223220104
*/
```

### MainActivity.java
```java
package com.example.simpleaudioplayer;

import androidx.appcompat.app.AppCompatActivity;
import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private MediaPlayer mediaPlayer;
    private Button btnPlay, btnPause, btnStop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize buttons
        btnPlay = findViewById(R.id.btnPlay);
        btnPause = findViewById(R.id.btnPause);
        btnStop = findViewById(R.id.btnStop);

        // Create MediaPlayer
        mediaPlayer = MediaPlayer.create(this, R.raw.audio);
        
        // If using assets folder instead, use:
        // mediaPlayer = new MediaPlayer();
        // try {
        //     mediaPlayer.setDataSource("file:///android_asset/audio.mp3");
        //     mediaPlayer.prepare();
        // } catch (Exception e) {
        //     e.printStackTrace();
        // }

        // PLAY Button
        btnPlay.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null && !mediaPlayer.isPlaying()) {
                    mediaPlayer.start();
                    showToast("Playing audio...");
                }
            }
        });

        // PAUSE Button
        btnPause.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null && mediaPlayer.isPlaying()) {
                    mediaPlayer.pause();
                    showToast("Audio paused");
                }
            }
        });

        // STOP Button
        btnStop.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (mediaPlayer != null) {
                    if (mediaPlayer.isPlaying()) {
                        mediaPlayer.stop();
                    }
                    mediaPlayer.reset();
                    try {
                        mediaPlayer = MediaPlayer.create(MainActivity.this, R.raw.audio);
                    } catch (Exception e) {
                        e.printStackTrace();
                    }
                    showToast("Audio stopped");
                }
            }
        });
    }

    private void showToast(String message) {
        Toast.makeText(this, message, Toast.LENGTH_SHORT).show();
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        if (mediaPlayer != null) {
            mediaPlayer.release();
        }
    }
}
```
### activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Simple Audio Player"
        android:textSize="20sp"
        android:layout_marginBottom="30dp"/>

    <Button
        android:id="@+id/btnPlay"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PLAY"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnPause"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PAUSE"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnStop"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="STOP"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

</LinearLayout>
```


## OUTPUT
### Play
<img width="2878" height="1786" alt="image" src="https://github.com/user-attachments/assets/d34b9e5f-b059-4220-bd67-22b8a19f67e9" />

## Pause
<img width="2879" height="1799" alt="image" src="https://github.com/user-attachments/assets/a7a05e84-5565-409f-94da-1a2eb34e43d1" />

## Stop
<img width="2879" height="1799" alt="image" src="https://github.com/user-attachments/assets/780c9885-8bc9-4b2c-9c05-7d131c3775be" />


## RESULT
   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.
