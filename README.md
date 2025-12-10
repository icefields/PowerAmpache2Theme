# Power Ampache 2 Theme
**Instructions:**<br>
Add the submodule at the root level of your app:<br>
`git submodule add git@github.com:icefields/PowerAmpache2Theme.git PowerAmpache2Theme`

In the app where the theme is included, edit:<br>
`gradle/libs.versions.toml`<br>
add on top:<br>
`material3 = "1.3.2"` (change the version to the latest)<br>
under libraries add:<br>
`compose-material3 = { module = "androidx.compose.material3:material3", version.ref = "material3" }`<br>
under plugins add (or replace if already present with a different name):<br>
`kotlin-compose = { id = "org.jetbrains.kotlin.plugin.compose", version.ref = "kotlin" }`<br>
<br>
Edit `settings.gradle`, add:<br>
`include(":PowerAmpache2Theme")`<br>
<br>
Edit top level `build.gradle.kts`<br>
add, or replace if present with a different name:<br>
`alias(libs.plugins.kotlin.compose) apply false`<br>
<br>

Edit `app/build.gradle.kts`<br>
under plugins add:<br>
`alias(libs.plugins.kotlin.compose)`<br>
under dependencies add:<br>
`implementation(project(":PowerAmpache2Theme"))`<br>
<br>
In the main activity, or wherever the the compose ui is initialized:<br>
```
PowerAmpache2Theme(
    darkTheme = isDarkTheme, 
    dynamicColor = isDynamicColour
) {
    MainScreen()
}
```
<br>
Material3 dependency and theme declaration might also be needed on the presentation layer of your app:

```
implementation(libs.compose.material3)
```
<br>`themes.xml` : <br>

```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="Theme.PowerAmpache2" parent="Theme.Material3.DayNight.NoActionBar" />
```

<br>`manifest.xml`, add in `<application>` <br>

`android:theme="@style/Theme.PowerAmpache2"`
