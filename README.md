```<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Student Grade Calculator"
        android:textSize="25sp"
        android:textStyle="bold"
        android:layout_gravity="center"
        android:layout_marginBottom="20dp"/>

    <EditText
        android:id="@+id/marks"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Marks"
        android:inputType="number"/>

    <Button
        android:id="@+id/calculate"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Calculate Grade"
        android:layout_marginTop="15dp"/>

    <TextView
        android:id="@+id/result"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="22sp"
        android:gravity="center"
        android:layout_marginTop="20dp"/>

</LinearLayout>

main.java

package com.example.h;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText marks;
    Button calculate;
    TextView result;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        marks = findViewById(R.id.marks);
        calculate = findViewById(R.id.calculate);
        result = findViewById(R.id.result);

        calculate.setOnClickListener(v -> {

            int m = Integer.parseInt(marks.getText().toString());

            if (m >= 90)
                result.setText("Grade: A+");
            else if (m >= 80)
                result.setText("Grade: A");
            else if (m >= 70)
                result.setText("Grade: B");
            else if (m >= 60)
                result.setText("Grade: C");
            else if (m >= 50)
                result.setText("Grade: D");
            else
                result.setText("Grade: F");
        });
    }
}
```

---
---
---
---


```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp"
    android:gravity="center">

    <EditText
        android:id="@+id/password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Password"
        android:inputType="textPassword" />

    <CheckBox
        android:id="@+id/showPassword"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Show Password" />

</LinearLayout>

java:
package com.example.h;

import android.app.Activity;
import android.os.Bundle;
import android.text.method.PasswordTransformationMethod;
import android.text.method.HideReturnsTransformationMethod;
import android.widget.CheckBox;
import android.widget.EditText;

public class MainActivity extends Activity {

    EditText password;
    CheckBox showPassword;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        password = findViewById(R.id.password);
        showPassword = findViewById(R.id.showPassword);

        showPassword.setOnCheckedChangeListener((button, checked) -> {
            if (checked) {
                password.setTransformationMethod(
                        HideReturnsTransformationMethod.getInstance());
            } else {
                password.setTransformationMethod(
                        PasswordTransformationMethod.getInstance());
            }

            password.setSelection(password.getText().length());
        });
    }
}
```
---
---
---


