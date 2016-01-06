# CollapsingToolbarLayoutExample
A very simple example on how to use a collapsing toolbar in Android. I've tried to make it as painless as possible.


#Example

First create this layout:

```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.design.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true">

    <android.support.design.widget.AppBarLayout
        android:id="@+id/appbar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:fitsSystemWindows="true"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar">

        <android.support.design.widget.CollapsingToolbarLayout
            android:id="@+id/collapsing_toolbar"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:fitsSystemWindows="true"
            app:contentScrim="?attr/colorPrimary"
            app:expandedTitleMarginBottom="32dp"
            app:expandedTitleMarginEnd="64dp"
            app:expandedTitleMarginStart="48dp"
            app:layout_scrollFlags="scroll|exitUntilCollapsed">

            <ImageView
                android:id="@+id/header"
                android:layout_width="match_parent"
                android:layout_height="192dp"
                android:background="@color/colorPrimary"
                android:fitsSystemWindows="true"
                android:scaleType="centerCrop"
                app:layout_collapseMode="parallax" />

            <android.support.v7.widget.Toolbar
                android:id="@+id/anim_toolbar"
                android:layout_width="match_parent"
                android:layout_height="?attr/actionBarSize"
                app:layout_collapseMode="pin"
                app:popupTheme="@style/ThemeOverlay.AppCompat.Light">

                <TextView
                    android:id="@+id/toolbar_title"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:fontFamily="sans-serif-light"
                    android:gravity="center"
                    android:singleLine="true"
                    android:textColor="@android:color/white"
                    android:textSize="18sp" />
            </android.support.v7.widget.Toolbar>
        </android.support.design.widget.CollapsingToolbarLayout>
    </android.support.design.widget.AppBarLayout>

    <android.support.v4.widget.NestedScrollView
        android:id="@+id/scroll"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:clipToPadding="false"
        app:layout_behavior="@string/appbar_scrolling_view_behavior">

        <include layout="@layout/content_layout" />

    </android.support.v4.widget.NestedScrollView>
</android.support.design.widget.CoordinatorLayout>

```

at the point where it says:

```xml
<include layout="@layout/content_layout" />
```

replace that layout with one of your own, either inline, or if you wish, with an external layout file (my recommendation)

also make sure to set android to use a no action bar theme in your styles.xml or wherever you would prefer to set your theme:

```xml
    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
```

and that should be enough hopefully! it's a difficult view to wrangle with you need to make sure things are set up just so.

