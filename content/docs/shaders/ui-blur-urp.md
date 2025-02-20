---
title: "UI Blur - URP"
---

## **Introduction**

Welcome to the **UI BLUR - URP Shader** documentation. This guide will help you understand how to integrate and utilize the UI Blur shader within Unity's Universal Render Pipeline (URP) to create stunning blur effects on UI elements and 3D objects.

## **Overview**

The UI BLUR - URP shader is designed to provide blur effects for both UI elements and 3D/2D objects within your Unity project. It includes:

-   `ui_blur_mat`: A material for blurring UI elements and 3D/2D objects.

-   `ui_blur_mat_transparent`: A material specifically for blurring 3D/2D objects.

-   `UI Blur Controller` script: A utility to control the blur amount dynamically.

## **Setting Up the Shader (For** `ui_blur_mat`**)**

### Enabling Opaque Texture

For the `ui_blur_mat` material to work correctly, you need to enable the **Opaque Texture** property in the Render Pipeline Asset.

1.  Open your URP settings.

2.  Set **Opaque Texture** to TRUE.

### Configuring Opaque Downsampling

It is recommended to configure **Opaque Downsampling** to `4x Box` for optimal performance.

1.  In URP settings, find the **Opaque Downsampling** option.

2.  Set it to `4x Box`.

![](shaders/images/image1.png)

## **Working with UI Blur Materials**

### ui\_blur\_mat

This material works for both UI elements and gameobjects in the scene.

1.  Ensure the **Opaque Texture** property is enabled.

2.  Apply the `ui_blur_mat` to your UI element or gameobject.

Make sure you turn off the `Is Transparent` option in `UI Blur Controller`.

### ui\_blur\_mat\_transparent

This material works specifically for gameobjects in the scene.

1.  Create a second camera in the scene derived from the MainCamera.

2.  Turn off the **UI** option in the **Culling Mask** for the second camera.

3.  Apply the `ui_blur_mat_transparent` to your gameobject.

Make sure you turn on the `Is Transparent` option in `UI Blur Controller` and `Blur Camera` property is set.

![](shaders/images/image2.png)

## **Using the UI Blur Controller Script**

The `UI Blur Controller` script allows you to dynamically control the blur amount.

1.  Attach the `UI Blur Controller` script to the UI element or gameobject.

2.  Use the `BlurAmount` attribute to adjust the blur amount as needed.

![](shaders/images/image3.png)

## **Shapes and Customization**

The package includes two shapes: a circle and a square. You can also use your own custom shapes.

1.  Import your custom shape into the project.

2.  Apply the `ui_blur_mat` or `ui_blur_mat_transparent` material to your custom shape.

![](shaders/images/mw1920_blur_squere_tex.png) ![](shaders/images/mw1920_blur_circle_tex.png)

## **<span class="mark" data-color="3">New Feature:</span> Drag-and-Drop UI Element Blurring**

The new feature allows you to select specific UI elements that will be affected by blur for the `ui_blur_mat` material using a drag-and-drop interface. Here’s how to use it:

1.  In the **UI Blur Controller** inspector, you'll see a **Foldout** labeled **"UI Elements"**.

2.  Drag and drop UI elements from the hierarchy into this list.

3.  Next to each added element, there is an option to **Include Children**.

    -   If checked, all child objects will also be blurred.

    -   If unchecked, only the parent object will be affected by the blur.

4.  A cross `(X)` button next to each UI element allows you to remove it from the list.

![](shaders/images/image4.png)


<video autoplay muted loop controls class="w-full max-w-3xl mx-auto" width="100%">
  <source src="/shaders/drag_drop_feature.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


## **FAQ**

#### **Can I use this shader with the Built-in Render Pipeline?**

No, this shader is designed specifically for the Universal Render Pipeline (URP).

#### **How do I control the blur amount dynamically?**

Use the `UI Blur Controller` script attached to the UI element or gameobject.
