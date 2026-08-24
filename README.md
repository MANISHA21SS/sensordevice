# Ex.No:4 Develop a simple application to display the avaliable sensor in android mobile devices using Sensor Manager in android studio.


## AIM:

To develop a sensor application to use the sensor manager class to identify and get the list of available sensors on a device. in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Giraffe)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as Sensor and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display avaliable sensor in android mobile devices.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the avaliable sensor in android mobile devices”.
Developed by: Manisha selvakumari.S.S.
Registeration Number : 212223220055
*/
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Available Sensors"
        android:textSize="24sp"
        android:textStyle="bold"
        android:layout_marginBottom="16dp" />

    <ListView
        android:id="@+id/listViewSensors"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</LinearLayout>
```
## Activity_main.java
```

package com.example.sensorlist;

import android.content.Context;
import android.hardware.Sensor;
import android.hardware.SensorManager;
import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import androidx.appcompat.app.AppCompatActivity;
import java.util.ArrayList;
import java.util.List;
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        ListView listViewSensors = findViewById(R.id.listViewSensors);
        // Get the SensorManager service
        SensorManager sensorManager = (SensorManager) getSystemService(Context.SENSOR_SERVICE);
        // Get the list of all available sensors
        List<Sensor> sensorList =
                sensorManager.getSensorList(Sensor.TYPE_ALL);
        // Prepare data for the ListView
        ArrayList<String> sensorNames = new ArrayList<>();
        for (Sensor sensor : sensorList) {
            String sensorInfo = sensor.getName() + " - " +
                    getSensorTypeName(sensor.getType());
            sensorNames.add(sensorInfo);
        }
        // If no sensors found (should not happen on real device)
        if (sensorNames.isEmpty()) {
            sensorNames.add("No sensors found");
        }
        // Display the list using ArrayAdapter
        ArrayAdapter<String> adapter = new ArrayAdapter<>(
                this,
                android.R.layout.simple_list_item_1,
                sensorNames
        );
        listViewSensors.setAdapter(adapter);
    }
    // Helper method to get a readable sensor type name
    private String getSensorTypeName(int sensorType) {
        switch (sensorType) {
            case Sensor.TYPE_ACCELEROMETER: return "Accelerometer";
            case Sensor.TYPE_AMBIENT_TEMPERATURE: return "Ambient Temperature";
            case Sensor.TYPE_GAME_ROTATION_VECTOR: return "Game Rotation Vector";
            case Sensor.TYPE_GYROSCOPE: return "Gyroscope";
            case Sensor.TYPE_LIGHT: return "Light";
            case Sensor.TYPE_MAGNETIC_FIELD: return "Magnetic Field";
            case Sensor.TYPE_PRESSURE: return "Pressure";
            case Sensor.TYPE_PROXIMITY: return "Proximity";
            case Sensor.TYPE_RELATIVE_HUMIDITY: return "Relative Humidity";
            case Sensor.TYPE_ROTATION_VECTOR: return "Rotation Vector";
            case Sensor.TYPE_STEP_COUNTER: return "Step Counter";
            case Sensor.TYPE_STEP_DETECTOR: return "Step Detector";
            case Sensor.TYPE_GRAVITY: return "Gravity";
            case Sensor.TYPE_LINEAR_ACCELERATION: return "Linear Acceleration";
            case Sensor.TYPE_ORIENTATION: return "Orientation (deprecated)";
            default: return "Sensor type " + sensorType;
        }
    }
}


```
## OUTPUT

<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/707c9ca5-5925-4ec5-8cbd-1d32e39a638a" />



## RESULT
Thus a Simple Android Application to display the avaliable sensor in android mobile devices using Sensor Manager in Android Studio is developed and executed successfully.
