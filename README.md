# SMS-INTENT
### AIM:
To create and design an android application Send SMS using Intent using Android Studio.
### EQUIPMENTS REQUIRED:
Android Studio(Latest Version)
### ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.
### PROGRAM:
```
DEVELOPED BY:Rajesh K
REGISTER NUMBER:212221220041
```
### activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">

<EditText
    android:id="@+id/number"
    android:layout_width="265dp"
    android:layout_height="47dp"
    android:layout_marginTop="220dp"
    android:ems="10"
    android:inputType="textPersonName"
    android:text=""
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.561"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent" />

<EditText
    android:id="@+id/text"
    android:layout_width="349dp"
    android:layout_height="105dp"
    android:ems="10"
    android:inputType="textPersonName"
    android:text=""
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.451"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintVertical_bias="0.645" />

<Button
    android:id="@+id/send"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="56dp"
    android:backgroundTint="#4CAF50"
    android:text="SEND"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.498"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/text" />

<TextView
    android:id="@+id/textView"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="108dp"
    android:layout_marginBottom="32dp"
    android:text="Phone no :"
    android:textColor="#009688"
    android:textSize="30dp"
    app:layout_constraintBottom_toTopOf="@+id/number"
    app:layout_constraintStart_toStartOf="parent" />

<TextView
    android:id="@+id/textView2"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="28dp"
    android:layout_marginTop="84dp"
    android:text="Message:"
    android:textColor="#89C18B"
    android:textSize="30dp"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/number" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
### MainActivity.java
```
package com.example.smsintent;

import androidx.appcompat.app.AppCompatActivity;

import android.Manifest;
import android.annotation.SuppressLint;
import android.content.pm.PackageManager;
import android.os.Build;
import android.os.Bundle;
import android.telephony.SmsManager;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
private EditText number,message;
private Button send;
@SuppressLint("MissingInflatedId")
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    number = findViewById(R.id.number);
    message = findViewById(R.id.text);
    send = findViewById(R.id.send);

    send.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View view) {
            if (Build.VERSION.SDK_INT>=Build.VERSION_CODES.M){
                if (checkSelfPermission(Manifest.permission.SEND_SMS) == PackageManager.PERMISSION_GRANTED){
                    sendSMS();
                }else {
                    requestPermissions(new String[]{Manifest.permission.SEND_SMS},1);
                }
            }
        }
    });
}
private void sendSMS(){
    String phoneNo = number.getText().toString().trim();
    String SMS = message.getText().toString().trim();

    try{
        SmsManager smsManager = SmsManager.getDefault();
        smsManager.sendTextMessage(phoneNo,null,SMS,null,null);
        Toast.makeText(this,"Message is sent",Toast.LENGTH_SHORT).show();
    } catch (Exception e){
        e.printStackTrace();
        Toast.makeText(this,"Failed to send message",Toast.LENGTH_SHORT).show();
    }
}
}
```
### AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools">
<uses-permission android:name="android.permission.SEND_SMS" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />

<application
    android:allowBackup="true"
    android:dataExtractionRules="@xml/data_extraction_rules"
    android:fullBackupContent="@xml/backup_rules"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:supportsRtl="true"
    android:theme="@style/Theme.Smsintent"
    tools:targetApi="31">
    <activity
        android:name=".MainActivity"
        android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />

            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>

</manifest>
```
### OUTPUT:
![image](https://github.com/HibaRajarajeswari/SMS-INTENT/assets/129970809/837db2fb-0ac0-4a3a-af02-11abce44a045)
![image](https://github.com/HibaRajarajeswari/SMS-INTENT/assets/129970809/2816d9df-32b3-49bd-b251-73a212609ffa)
![image](https://github.com/HibaRajarajeswari/SMS-INTENT/assets/129970809/6e92edb3-5707-4e15-ab8f-9676621a45f9)
![image](https://github.com/HibaRajarajeswari/SMS-INTENT/assets/129970809/4750fa0c-77aa-4188-a804-5a0fe96ff686)
### RESULT:
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
