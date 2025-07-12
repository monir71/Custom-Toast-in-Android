MainActivity.java File:

```
package com.example.customtoastexample;

import android.annotation.SuppressLint;
import android.os.Bundle;
import android.view.Gravity;
import android.view.View;
import android.view.ViewGroup;
import android.widget.TextView;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        Toast toast = new Toast(getApplicationContext());
        View view;
        view = getLayoutInflater().inflate(R.layout.custom_toast_layout, (ViewGroup) findViewById(R.id.custom_toast_view));
        toast.setView(view);
        toast.setDuration(Toast.LENGTH_LONG);
        toast.setGravity(Gravity.CENTER, 0, 0);
        //toast.setText("Something went wrong! Please contact the Administrator for details. Thanks for your patience.");
        TextView toast_text = view.findViewById(R.id.custom_toast_txt);
        toast_text.setText("Something went wrong!\nPlease contact the Administrator for details.\nThanks for your patience.");
        toast.show();

        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });
    }
}
```
