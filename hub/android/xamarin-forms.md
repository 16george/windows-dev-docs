---
title: Create a simple Android app with Xamarin Forms
description: How to get started writing Android apps with Xamarin Forms
author: hickeys 
ms.author: hickeys 
manager: jken
ms.topic: article
keywords: 
ms.localizationpriority: medium
ms.date: 01/24/2020
ms.prod: "xamarin"
ms.technology: "xamarin-forms"
---

# Get started developing for Android using Xamarin Forms

This guide will help you to get started using Xamarin Forms on Windows to create a cross-platform app that will work on Android devices.

In this article, you will create a simple Android app using Xamarin Forms and Visual Studio 2019.

## Requirements

To use this tutorial, you'll need the following:

- Windows 10, version XXXX or higher
- [Visual Studio 2019: Community, Professional, or Enterprise](https://visualstudio.microsoft.com/downloads/)
- The "Mobile development with .NET" workload for Visual Studio 2019

You will also to have an Android phone or configured emulator in which to run your app. See Configuring an Android emulator.

## Create a new Xamarin Forms project

Start Visual Studio. Click File > New > Project to create a new project.

In the new project dialog, select the **Mobile App (Xamarin.Forms)** template and click **Next**.

Name the project **TimeChangerForms** and click **Create**.

In the New Cross Platform App dialog, select **Blank**. In the Platform section, check **Android** and un-check all other boxes. Click **OK**.

Xamarin will create a new solution with two projects: **TimeChangerForms** and **TimeChangerForms.Android.**

## Create a UI with XAML

Expand the **TimeChangerForms** project and open **MainPage.xaml**. The XAML in this file defines the first screen a user will see when opening TimeChanger.

TimeChanger's UI is simple. It displays the current time, and has buttons to adjust the time in increments of one hour. It uses a vertical StackLayout to align the time above the buttons, and a horizontal StackLayout to arrange the buttons side-by-side. The content is centered in the screen by setting the vertical StackLayout's **HorizontalOptions** and **VerticalOptions** to **"CenterAndExpand"**.

Replace the contents of MainPage.xaml with the following code.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:d="http://xamarin.com/schemas/2014/forms/design"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
             mc:Ignorable="d"
             x:Class="TimeChangerForms.MainPage">

    <StackLayout HorizontalOptions="CenterAndExpand"
                 VerticalOptions="CenterAndExpand">
        <Label HorizontalOptions="CenterAndExpand"
               VerticalOptions="CenterAndExpand"
               x:Name="time"
               Text="At runtime, this Label will display the current time.">
        </Label>
        <StackLayout Orientation="Horizontal">
            <Button HorizontalOptions="End"
                    VerticalOptions="End"
                    Text="Up"
                    Clicked="UpButton_Clicked"/>
            <Button HorizontalOptions="Start"
                    VerticalOptions="End"
                    Text="Down"
                    Clicked="DownButton_Clicked"/>
        </StackLayout>
    </StackLayout>
</ContentPage>
```

At this point, the UI is complete. TimeChangerForms, however, will not build because the methods **UpButton_Clicked** and **DownButton_Clicked** are referenced in the XAML but not defined anywhere. Even if the app did run, the current time would not be displayed. In the next section, you will fix these errors and add functionality to your UI.

## ## Add logic code with C#

In the Solution Explorer, right click MainPage.xaml and click **View Code**. This file contains the code behind that will add functionality to the UI.

### Set the current time

Code in this file can reference controls declared in the XAML using the value of the control's **x:Name** attribute. In this case the label that displays the current time is called `time`.

UI controls must be updated on the main thread. Changes made from another thread may not properly update the control as it displays on the screen. Because there is no guarantee this code will always be running on the main thread, use the **BeginInvokeOnMainThread** method to make sure any updates display correctly. Here is the complete UpdateTimeLabel method.

```csharp
private void UpdateTimeLabel(object state = null)
{
    Device.BeginInvokeOnMainThread(() =>
        {
            time.Text = DateTime.Now.ToLongTimeString();
        }
    );
}
```

### Update the current time once every second

At this point, the current time will be accurate for, at most, one second after TimeChangerForms is launched. The label must be periodically updated to keep the time accurate. A **Timer** object will periodically call a callback method that updates the label with the current time.

```csharp
var clockRefresh = new Timer(dueTime: 0, period: 1000, callback: UpdateTimeLabel, state: null);
```

### Add HourOffset

The up and down buttons adjust the time in increments of one hour. Add an **HourOffset** property to track the current adjustment.

```csharp
public int HourOffset { get; private set; }
```

Now update the UpdateTimeLabel method to be aware of the HourOffset property.

```csharp
currentTime.Text = DateTime.Now.AddHours(HourOffset).ToLongTimeString();
```

### Add button Click event handlers

All the up and down buttons need to do is increment or decrement the HourOffset property and call UpdateTimeLabel.

```csharp
private void UpButton_Clicked(object sender, EventArgs e)
{
    HourOffset++;
    UpdateTimeLabel();
}
```

When you're finished, MainPage.xaml.cs should look like this:

```csharp
using System;
using System.ComponentModel;
using System.Threading;
using Xamarin.Forms;

namespace TimeChangerForms
{
    // Learn more about making custom code visible in the Xamarin.Forms previewer
    // by visiting https://aka.ms/xamarinforms-previewer
    [DesignTimeVisible(false)]
    public partial class MainPage : ContentPage
    {
        public int HourOffset { get; private set; }

        public MainPage()
        {
            InitializeComponent();
        }

        protected override void OnAppearing()
        {
            base.OnAppearing();
            var clockRefresh = new Timer(dueTime: 0, period: 1000, callback: UpdateTimeLabel, state: null);
        }

        private void UpdateTimeLabel(object state = null)
        {
            Device.BeginInvokeOnMainThread(() =>
                {
                    time.Text = DateTime.Now.AddHours(HourOffset).ToLongTimeString();
                }
            );
        }

        private void UpButton_Clicked(object sender, EventArgs e)
        {
            HourOffset++;
            UpdateTimeLabel();
        }

        private void DownButton_Clicked(object sender, EventArgs e)
        {
            HourOffset--;
            UpdateTimeLabel();
        }
    }
}
```

## Run the app

To run the app, press **F5** or click Debug > Start Debugging. If you are using an Android emulator, your app will start in the emulator you've configured. Otherwise, it will launch on your phone. **To do.** >> Phone requires some set up here.

## Download the code

**To do.** Download the complete code sample here.

## Related links

**To do.**

- Configure your dev machine to do Android development
- [Create an Android sample app using Xamarin.Android](xamarin-android.md)
- Create an iOS sample app using Xamarin.iOS
