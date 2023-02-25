---
date: 2018-11-30
categories: [it, programming]
tags: [Android Studio, Android, Java]
author: Anton Sergienko
author-email: anton.b.sergienko@gmail.com
license: CC BY 4.0
license-url: https://github.com/Harrix/harrix.dev/blob/main/LICENSE.md
url-src: https://github.com/Harrix/harrix.dev-blog-2018/blob/main/color-actionbar-statusbar/color-actionbar-statusbar.md
url: https://harrix.dev/ru/blog/2018/color-actionbar-statusbar/
lang: ru
---

# Изменение цвета строки состояния и StatusBar в Android приложении

Статья о том, как динамически изменять цвет элементов `StatusBar` и `ActionBar`.

Цвет строки состояния можно поменять кодом:

```java
getSupportActionBar().setBackgroundDrawable(
        new ColorDrawable(Color.parseColor(color)));
```

Цвет главной панели `StatusBar` можно поменять через метод:

```java
public void setStatusBarColor(String color) {
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP) {
        Window window = getWindow();
        int statusBarColor = Color.parseColor(color);
        if (statusBarColor == Color.BLACK && window.getNavigationBarColor() == Color.BLACK) {
            window.clearFlags(WindowManager.LayoutParams.FLAG_DRAWS_SYSTEM_BAR_BACKGROUNDS);
        } else {
            window.addFlags(WindowManager.LayoutParams.FLAG_DRAWS_SYSTEM_BAR_BACKGROUNDS);
        }
        window.setStatusBarColor(statusBarColor);
    }
}
```

Пример приложения, в котором при нажатии на кнопку меняется цвет обоих компонентов (без строчки `package`):

```java
import android.graphics.Color;
import android.graphics.drawable.ColorDrawable;
import android.os.Build;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.view.Window;
import android.view.WindowManager;
import android.widget.Button;


public class MainActivity extends AppCompatActivity {

    Button button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        button = (Button) findViewById(R.id.button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String color = "#AA3939";

                setStatusBarColor(color);

                getSupportActionBar().setBackgroundDrawable(
                        new ColorDrawable(Color.parseColor(color)));
            }
        });
    }

    public void setStatusBarColor(String color) {
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP) {
            Window window = getWindow();
            int statusBarColor = Color.parseColor(color);
            if (statusBarColor == Color.BLACK && window.getNavigationBarColor() == Color.BLACK) {
                window.clearFlags(WindowManager.LayoutParams.FLAG_DRAWS_SYSTEM_BAR_BACKGROUNDS);
            } else {
                window.addFlags(WindowManager.LayoutParams.FLAG_DRAWS_SYSTEM_BAR_BACKGROUNDS);
            }
            window.setStatusBarColor(statusBarColor);
        }
    }
}
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingLeft="16dp"
    android:paddingRight="16dp"
    android:orientation="vertical" >

    <Button
        android:id="@+id/button"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Button" />
</LinearLayout>
```

![Запущенное приложение](img\result.png)
