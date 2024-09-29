# Ex.No:5 Create Your Own Content Providers to get Contacts details.

# AIM:
To create your own content providers to get contacts details using Android Studio.

# EQUIPMENTS REQUIRED:
Android Studio(Latest Version)

# ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “contentprovider″ and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.

# PROGRAM:

/*
Program to print the contact name and phone number using content providers.
Developed by: SRI RANJANI PRIYA
Registeration Number : 212222220049
*/

### Mainactivity.java:
```
package com.example.ex5;
import android.support.v7.app.AppCompatActivity;
import android.database.Cursor;
import android.os.Bundle;
import android.provider.ContactsContract;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {

    private TextView textViewContacts;
    int count=0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button buttonLoadContacts = findViewById(R.id.button);

        buttonLoadContacts.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                loadContacts();
            }
        });
    }

    private void loadContacts() {
        StringBuilder stringBuilder = new StringBuilder();

        Cursor cursor = getContentResolver().query(ContactsContract.CommonDataKinds.Phone.CONTENT_URI,
                null, null, null, null);

        if (cursor != null && cursor.getCount() > 0) {
            int nameIndex = cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME_PRIMARY);
            int phoneIndex = cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER);

            while (cursor.moveToNext()) {
                String name = nameIndex != -1 ? cursor.getString(nameIndex) : "No Name";
                String phoneNumber = phoneIndex != -1 ? cursor.getString(phoneIndex) : "No Phone Number";

                stringBuilder.append("Name: ").append(name).append("\n").append("Phone: ").append(phoneNumber).append("\n\n");
                count = count+1;
            }
            cursor.close();
            textViewContacts.setText(stringBuilder.toString());
            Log.i("Content Provider Demo",stringBuilder.toString());
        } else {
            Toast.makeText(this, "No contacts found", Toast.LENGTH_SHORT).show();
        }

        System.out.println("Total Count of Contacts: "+count);}
}
```
### Activitymain.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Load Contacts"
        android:layout_centerHorizontal="true"
        android:backgroundTint="#2196F3"
        android:layout_marginTop="50dp"/>


</RelativeLayout>
```
### AndroidMainfest.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.example.ex5">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Ex5"
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
# OUTPUT
![369689253-5297af8e-4314-4631-8fbd-d16376d524b9](https://github.com/user-attachments/assets/bd0aada5-9b79-4d29-8914-bf9d7711e8b9)

https://private-user-images.githubusercontent.com/119643315/369689262-6bac9f90-3065-49f5-807a-8b6fff8d6ffd.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mjc2MjAzMDQsIm5iZiI6MTcyNzYyMDAwNCwicGF0aCI6Ii8xMTk2NDMzMTUvMzY5Njg5MjYyLTZiYWM5ZjkwLTMwNjUtNDlmNS04MDdhLThiNmZmZjhkNmZmZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwOTI5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDkyOVQxNDI2NDRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00M2VjYWE4ZjJiODYzOTZhMWU0MWRmODFhZmYyMzIwNmJjYzI3ODgwOTJjZTgxMGRmNDdmOGM3Y2VmZWE3OThlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.CXgWSYyn1BU0E8_CMIIU34v9-9mfi34We6TGrfecCpE

# RESULT
Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.
