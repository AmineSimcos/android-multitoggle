
# MultiToggleButton
### A simple Android multi toggle button

# Installation
[ ![Download](https://api.bintray.com/packages/shabankamel/android/multitogglebutton/images/download.svg) ](https://bintray.com/shabankamel/android/multitogglebutton/_latestVersion)
```groovy
dependencies {
    implementation 'com.sha.kamel:multitogglebutton:1.4.0@aar'
}
repositories { 
maven { url "https://dl.bintray.com/shabankamel/android" } 
}
```
# Usage

Add a button to layout:
```xml
  <com.sha.kamel.multitogglebutton.MultiToggleButton  
  android:id="@+id/mtb"  
  android:layout_width="match_parent"  
  android:layout_height="wrap_content"  
  android:layout_marginTop="10dip"  
  mtb:labels="@array/dogs_array"  
  mtb:mtbScrollable="true"  
  mtb:mtbRoundedCorners="true"  
  mtb:mtbPressedColor="@color/orange_pressed"  
  mtb:mtbUnpressedColor="@color/orange"  
  mtb:mtbColorPressedText="@color/white"  
  mtb:mtbColorUnpressedText="@color/white"  
  mtb:mtbCornerRadius="8dp"  
  />
```
## Listen to item selection
```java
 mtb.setOnItemSelectedListener((toggleButton, item, index, label, selected) -> {  
   String msg = "Number " +  
            index +   
            " is " +   
            (selected ? "selected" : "deselected") +  
            ", Label: " + label +   
            ", Selected items: " +  
            selectedItemsMsg(toggleButton);  
  toast(msg);  
});

private String selectedItemsMsg(ToggleButton toggleButton) {  
  Selected selected = toggleButton.getSelected();  
  String msg;  
 if (selected.isAnySelected()){  
        if (selected.isSingleItem())  
            msg = "One item selected: " + selected.getSingleItemPosition();  
 else  msg = Stream.of(selected.getSelectedPositions())  
                    .map(String::valueOf)  
                    .reduce((p1, p2) ->  p1 + ", " + p2)  
                    .get();  
  
  }  
    else msg = "No items selected";  
 return msg;  
}
```
## Colors
You can select any desired color for different states.
```java
mtb.setColorRes(R.color.mtb_green, R.color.mtb_gray);
```
There're many methods to set colors. Take a look at `ToggleButton`

## Rounded corners
you can set corners rounded:
```java
mtb.setRoundedCorners();
```

## Corners Radius
You can set a default radius of `18dp` :
```java
mtb.setCornerRadius(20);
```


##### Note:
if you set corner radius with `setCornerRadius`, no need to call `setRoundedCorners`.

## Multiple Choice
```java
mtb.multipleChoice(true)
```

## Max items to select
you can set the maximum items allowed to be selected
```java
.maxSelectedItems(2, max -> toast("Can't select more than " + max + " items."));
```
#### Note:
if you call `maxSelectedItems`, no need to set `multipleChoice(true)`.

# Attributes:
| Attribute name                    | Description                                                   |
| ----------------|------------------------|
|   labels |  Labels of each items in button
|   mtbPressedColor | Color of pressed button
|   mtbUnpressedColor  | Color of unpressed button
|   mtbColorPressedText | Color of text for pressed button
|   mtbColorUnpressedText | Color of text for un pressed button
|   mtbCornerRadius | Corner radius
|   mtbRoundedCorners | If true, the corners will be rounded. If corner radius is not set a default radius 18 will be set.
|   mtbMultipleChoice | multiple items choice. The default is false.
|   mtbScrollable | If true, items will be scrollable if it's out of screen bounds. The default is false
|   mtbSelectFirstItem | If true, first item will be selected. The default is true.
|   mtbTextAllCaps | All text caps.The default is true.


### See 'app' module for the full code.

# License

## Apache license 2.0
