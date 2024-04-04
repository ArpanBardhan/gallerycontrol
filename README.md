# Ex.No:8 To create a gallery control using android studio to display images or photos.


## AIM:

To create a gallery control using android studio to display images or photos.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
Prepare Images: Gather the images you want to display in the gallery and store them in the res/drawable folder of your Android project.

Design Layout: Create the layout for the main activity (activity_main.xml). Include a Gallery widget to display the images and an ImageView to show the selected image.

Set up Adapter: Develop a custom adapter class (CustomizedGalleryAdapter.java) that extends BaseAdapter. Override necessary methods like getCount() and getView() to handle the gallery items and their display.

Initialize Gallery: In the main activity (MainActivity.java), initialize the Gallery widget and set its adapter to the custom adapter you created.

Handle Item Selection: Implement functionality to respond when the user selects an image from the gallery. Update the ImageView with the selected image accordingly.


## PROGRAM:
```
/*
Program to print the text “GalleryControl”.
Developed by: ARPAN BARDHAN
Registeration Number : 212222040013
*/
```

## ACTIVITY_MAIN.XML
```XML
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#fff"
    android:orientation="vertical"
    tools:context=".MainActivity"
    android:id="@+id/main">

    <!-- create a ImageView and Gallery -->
    <ImageView
        android:id="@+id/imageView"
        android:layout_width="fill_parent"
        android:layout_height="200dp"
        android:scaleType="fitXY" />

    <!-- By using android:spacing we can give spacing between images
        android:animationDuration="3000" -> for animation running -->
    <Gallery
        android:id="@+id/languagesGallery"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="100dp"
        android:animationDuration="2000"
        android:padding="10dp"
        android:spacing="5dp"
        android:unselectedAlpha="50" />
</LinearLayout>
```

## MAIN_ACTIVITY.JAVA
```JAVA
package com.example.galleryview;

import android.os.Bundle;
import android.widget.Gallery;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Gallery simpleGallery;

    // CustomizedGalleryAdapter is a java/kotlin
    // class which extends BaseAdapter
    // and implement the override methods.
    CustomizedGalleryAdapter customGalleryAdapter;
    ImageView selectedImageView;

    // To show the selected language, we need this
    // array of images, here taken 10 different kind of
    // most popular programming languages
    int[] images = {
            R.drawable.circle,
            R.drawable.dice,
            R.drawable.genie,
            R.drawable.pumpkin,
            R.drawable.rocket,
            R.drawable.circle,
            R.drawable.dice,
            R.drawable.genie,
            R.drawable.pumpkin,
            R.drawable.rocket
    };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Our layout is activity_main
        // get the reference of Gallery. As we are showing
        // languages it is named as languagesGallery
        // meaningful names will be good for easier understanding
        simpleGallery = (Gallery) findViewById(R.id.languagesGallery);

        // get the reference of ImageView
        selectedImageView = (ImageView) findViewById(R.id.imageView);

        // initialize the adapter
        customGalleryAdapter = new CustomizedGalleryAdapter(getApplicationContext(), images);

        // set the adapter for gallery
        simpleGallery.setAdapter(customGalleryAdapter);

        // Let us do item click of gallery and image can be identified by its position
        simpleGallery.setOnItemClickListener((parent, view, position, id) -> {
            // Whichever image is clicked, that is set in the selectedImageView
            // position will indicate the location of image
            selectedImageView.setImageResource(images[position]);
        });
    }
}
```
## CustomizedGalleryAdapter.JAVA
```JAVA
package com.example.galleryview;

import android.content.Context;
import android.view.View;
import android.view.ViewGroup;
import android.widget.BaseAdapter;
import android.widget.Gallery;
import android.widget.ImageView;

public class CustomizedGalleryAdapter extends BaseAdapter {

    private final Context context;
    private final int[] images;

    public CustomizedGalleryAdapter(Context c, int[] images) {
        context = c;
        this.images = images;
    }

    // returns the number of images, in our example it is 10
    public int getCount() {
        return images.length;
    }

    // returns the Item of an item, i.e. for our example we can get the image
    public Object getItem(int position) {
        return position;
    }

    // returns the ID of an item
    public long getItemId(int position) {
        return position;
    }

    // returns an ImageView view
    public View getView(int position, View convertView, ViewGroup parent) {
        // position argument will indicate the location of image
        // create a ImageView programmatically
        ImageView imageView = new ImageView(context);

        // set image in ImageView
        imageView.setImageResource(images[position]);

        // set ImageView param
        imageView.setLayoutParams(new Gallery.LayoutParams(200, 200));
        return imageView;
    }
}
```
## OUTPUT
![Screenshot (456)](https://github.com/ArpanBardhan/gallerycontrol/assets/119405037/c538075c-2b94-445a-b309-b90cc6477eea)
![Screenshot (457)](https://github.com/ArpanBardhan/gallerycontrol/assets/119405037/53082b47-b441-448b-aed4-1e9816b2e48f)
![Screenshot (458)](https://github.com/ArpanBardhan/gallerycontrol/assets/119405037/5e619fd7-5e98-40ec-ae06-d24c15e0fba9)

## RESULT
Thus a Simple Android Application to create a gallery control using android studio to display images or photos is developed and executed successfully.

