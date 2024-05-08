# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
Step 1: Create a New Project in Android Studio

Step 2: Working with the activity_main.xml File

Step 3: Working with the MainActivity File

Step 4: Working with the activity_main2.xml File

Step 5: Working with the MainActivity2 File


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by:Bala Sathiesh CS
Registeration Number :212222040022
*/
```
## MainActivity.java
```
package com.example.explicitintent;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    private EditText editTextNumber;
    private Button buttonFactorial;
    private Button buttonExplicit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editTextNumber = findViewById(R.id.editTextNumber);
        buttonFactorial = findViewById(R.id.buttonFactorial);
        buttonExplicit = findViewById(R.id.buttonExplicit);

        buttonFactorial.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculateFactorial();
            }
        });

        buttonExplicit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                openSecondActivity();
            }
        });
    }

    private void calculateFactorial() {
        int number = Integer.parseInt(editTextNumber.getText().toString());
        int factorial = 1;
        for (int i = 1; i <= number; i++) {
            factorial *= i;
        }
        openSecondActivityWithFactorial(factorial);
    }

    private void openSecondActivityWithFactorial(int factorial) {
        Intent intent = new Intent(this, SecondActivity.class);
        intent.putExtra("factorial", factorial);
        startActivity(intent);
    }

    private void openSecondActivity() {
        Intent intent = new Intent(this, SecondActivity.class);
        startActivity(intent);
    }
}
```
## SecondActivity.java
```
package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

import android.widget.TextView;

public class SecondActivity extends AppCompatActivity {

    private TextView textViewResult;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        textViewResult = findViewById(R.id.textViewResult);

        Bundle extras = getIntent().getExtras();
        if (extras != null && extras.containsKey("factorial")) {
            int factorial = extras.getInt("factorial");
            textViewResult.setText("Factorial: " + factorial);
        } else {
            textViewResult.setText("Factorial not calculated");
        }
    }
}
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editTextNumber"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="Enter a number"
        android:inputType="number"/>

    <Button
        android:id="@+id/buttonFactorial"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Calculate Factorial"
        app:icon="@android:drawable/star_big_on" />

    <Button
        android:id="@+id/buttonExplicit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Explicit Intent"/>

</LinearLayout>
```
## acitvity_second.xml
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:backgroundTint="@color/design_default_color_error"
    android:padding="16dp"
    tools:context=".SecondActivity">

    <TextView
        android:id="@+id/textViewResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:textSize="20sp" />

</RelativeLayout>
```
## OUTPUT
![Explicitintent1](https://github.com/BalaSathiesh/ExplicitIntent-MAD/assets/128462891/d42cfddf-8bd6-440b-9a22-687a52e92581)
![Explicitintent2](https://github.com/BalaSathiesh/ExplicitIntent-MAD/assets/128462891/7d62f49f-a953-4733-8181-6592dd4299e8)
![Explicitintent3](https://github.com/BalaSathiesh/ExplicitIntent-MAD/assets/128462891/1b346825-0472-46d2-83b3-1591a7024221)
![Explicitintent4](https://github.com/BalaSathiesh/ExplicitIntent-MAD/assets/128462891/0d06f10f-558e-489c-bdc3-3532e451ce90)




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


