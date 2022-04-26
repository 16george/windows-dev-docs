---
description:  A glossary of terms related to Windows application development.
title: Windows developer glossary
ms.topic: article
ms.date: 04/22/2022
ms.author: mikben
author: MatchaMatch
ms.localizationpriority: medium
ms.collection: windows11
---

# Windows developer glossary

The following glossary of terms is meant to promote a common vocabulary among Windows developers.

#### App lifecycle management (ALM)
Describes the management of your application's execution state: not running, running in background, running in foreground, suspended, and so on. See [Windows 10 universal Windows platform (UWP) app lifecycle](/windows/uwp/launch-resume/app-lifecycle).

#### Application model
Often referred to as “app model”. The combination of deployment, isolation, lifecycle, and presentation components that are unique to a given application development technology. For example: Windows App SDK / WinUI 3 apps run on the Win32 app model, while UWP / WinUI 2 run on the UWP app model.

#### Application packaging
Describes the manner in which your application is packaged before being distributed and installed by users. Applications can be MSIX-packaged, unpackaged, or sparsely packaged.

#### Bootstrapper
A redistributable component providing an API to find and load the Windows App SDK framework package for the calling process. In a sparse-packaged or unpackaged app, you can opt to load the Windows App SDK framework package explicitly by calling Bootstrapper APIs such as [MddBootstrapInitialize](/windows/windows-app-sdk/api/win32/mddbootstrap/nf-mddbootstrap-mddbootstrapinitialize). Also see [Reference the Windows App SDK framework package at run time](/windows/apps/windows-app-sdk/reference-framework-package-run-time).

#### C++/WinRT
C++/WinRT is a standard C++17 language projection for Windows Runtime (WinRT) APIs, implemented as a header-file-based library, and designed to provide you with first-class access to modern Windows APIs. [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/).

#### Dynamic Dependencies
[Dynamic Dependencies](https://github.com/microsoft/WindowsAppSDK/blob/main/specs/dynamicdependencies/DynamicDependencies.md) makes framework packages accessible to all kinds of apps: packaged and unpackaged.

#### Fluent Design
[Fluent Design](https://www.microsoft.com/design/fluent/#/) is a design system that lets you create reusable cross-platform user interfaces. 

#### Hot Reload
An app development feature that allows you to update your application's code and observe your changes while your application runs, eliminating the need to stop, rebuild, and re-run your apps while developing. See [Write and debug running code with Hot Reload](/visualstudio/debugger/hot-reload).

#### Hybrid CRT linkage
A C/C++ runtime library linkage technique that simplifies deployment. Also referred to simply as *Hybrid CRT*. See [Hybrid C/C++ runtime library linkage (hybrid CRT linkage)](/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/migrate-to-windows-app-sdk-ovw#hybrid-cc-runtime-library-linkage-hybrid-crt-linkage).

#### Managed apps
"Managed" refers to the "managed runtime" of .NET, which provides managed services such as garbage collection and security assurances. If you're building an app with .NET, you're building a managed app.

#### Microsoft Foundation Classes (MFC)
You can use Microsoft Foundation Classes (MFC) to create complex user interfaces with multiple controls. You can use MFC to create applications with Office-style user interfaces. See: [MFC desktop applications](/cpp/mfc/mfc-desktop-applications).

#### MSIX (Microsoft Installer package format)
MSIX is a Windows app package format that combines the best features of MSI, .appx, App-V, and ClickOnce to provide a modern and reliable packaging experience. It's a modern application package format that lets you easily deploy your Windows applications. MSIX can be used to package apps built using Windows App SDK, Win32, WPF, or Windows Forms. When you use MSIX to deploy your apps, your app is an "MSIX-packaged" app. MSIX-packaged apps can check for updates and can control when updates are applied. [What is MSIX?](/windows/msix/overview).

#### MSIX-packaged app
Apps that are packaged using MSIX. MSIX-packaged apps give end-users an easy installation, uninstallation, and update experience. These run with package identity, which is needed for certain Windows features (for example, custom context menu extensions). MSIX-packaged apps can be installed through the Microsoft Store or Windows App Installer.

#### Native apps
Traditionally, "native" refers to applications built without using the .NET runtime. In this case, "native" is synonymous with "unmanaged", and can be used to describe apps that manage their own memory and security concerns. Alternatively, some developers use "native" to indicate that an application has been built to run specifically on Windows, calling Windows APIs directly.

#### .NET MAUI
.NET Multi-platform App UI. A cross-platform framework for creating native mobile and desktop apps with C# and XAML. An evolution of `Xamarin.Forms` extended from mobile to desktop scenarios, with UI controls rebuilt from the ground up for performance and extensibility. [What is .NET MAUI?](/dotnet/maui/what-is-maui).

#### Project Reunion
The codename for the Windows App SDK. No longer in use.

#### React Native
[React Native](https://reactnative.dev/) is a development platform from Meta which allows developers to build fully native cross-platform apps using JavaScript, TypeScript, and React. [React Native for Windows](https://aka.ms/reactnative) brings React Native support to the Windows 10 and Windows 11 SDKs, enabling developers to use JavaScript to build native Windows apps for all devices supported by Windows 10 and Windows 11. This includes PCs, tablets, 2-in-1s, Xbox, Mixed reality devices, etc.

#### Sparse packaging
Sparse packaging offers a hybrid between MSIX-packaged and unpackaged. Sparse-packaged apps do use MSIX to package, but they use a non-MSIX installer (like unpackaged apps) and they run with package identity (like MSIX-packaged apps). You can think of sparse-packaged apps as apps with “Bring-Your-Own-Installer" (BYOI).

#### Universal Windows Platform (UWP)
An application development platform and application model that uses Windows Runtime (WinRT) APIs to deliver MSIX-packaged apps. UWP apps run in a sandboxed environment and they inherit the security of the UWP platform. [Learn more about UWP](/windows/uwp/).

#### Unmanaged app
Apps that aren't managed by the .NET runtime. If you're handling your own memory management, you're building an unmanaged app. 

#### Unpackaged app
Apps that don't use MSIX, and are not sparse-packaged. They're typically installed and updated through `.exe`, Squirrel, or `.msi` files. These run without package identity. MSIX-packaged, sparse-packaged, and unpackaged apps can be published to the Microsoft Store.

#### Visual Studio extension (VSIX)
Lets you create, package, and deploy Visual Studio extensions. [Get started with the VSIX Project template](/visualstudio/extensibility/getting-started-with-the-vsix-project-template).

#### WebView2
A control that allows app developers to embed web content (HTML/CSS/JS) in their native apps using the Microsoft Edge (Chromium) rendering engine. You can use WebView2 in WinUI 3, Win32 C++, WPF, and WinForms, and it offers a developer preview for WinUI 2 / UWP support. See [Introduction to Microsoft Edge WebView2](/microsoft-edge/webview2/).

#### Windows API
Refers to the entire set of Windows APIs including Win32 APIs, COM APIs, UWP WinRT APIs, and the WinRT/Win32 APIs that are part of WinAppSDK and WinUI 3.

#### Windows App SDK
A set of new developer components and tools that represent the next evolution in the Windows app development platform. The successor to UWP / WinUI 2 for desktop application development (see [the Windows App SDK Roadmap](https://github.com/microsoft/WindowsAppSDK/blob/main/docs/roadmap.md)). It lifts libraries from the OS into a standalone SDK that you can use to build backwards-compatible desktop apps. See [Overview of app development options](/windows/apps/get-started).

#### Windows Forms
Also known as WinForms. A UI framework for building Windows desktop applications. It is a .NET wrapper over Windows user interface libraries, such as User32 and GDI+. It’s a battle-tested way to create desktop applications using a visual designer within Visual Studio. See [Desktop Guide (Windows Forms .NET)](/dotnet/desktop/winforms/overview/).

#### Windows Presentation Foundation (WPF)
A UI framework for building Windows desktop applications. WPF applications are based on a vector graphics architecture. This enables applications to look great on high DPI monitors, as they can be infinitely scaled. See [What is Windows Presentation Foundation (WPF)?](/visualstudio/designers/getting-started-with-wpf).

#### Windows SDK
The Windows SDK is a collection of headers, libraries, metadata, and tools that allow you to build desktop and UWP Windows apps. The Windows SDK is not the same as the [Windows App SDK](#windows-app-sdk).

#### WinUI
The Windows UI Library (WinUI) is the modern native user interface (UX) framework for both Windows desktop and UWP applications. [Windows UI Library (WinUI)](/windows/apps/winui/). 

#### WinUI 2
Windows UI Library (WinUI) 2 is tightly integrated with Windows 10 and later SDKs, and provides official native Windows UI controls and other user interface elements for UWP applications (and desktop applications using XAML Islands). See [Windows UI Library (WinUI) 2](/windows/apps/winui/winui2/).

#### WinUI 3
The latest and recommended UI framework for Windows desktop apps. This framework is made available through the Windows App SDK, and has been decoupled from the Windows operating system. WinUI 3 uses [Fluent Design](/design/fluent/) to provide a native UX framework for Windows desktop apps. It will feel very familiar if you've worked with WinUI 2. See [Windows UI Library (WinUI) 3](/windows/apps/winui/winui3/).

#### XAML Islands
XAML Islands lets you host WinRT XAML controls in non-UWP desktop (Win32, WinForms, WPF) apps starting in Windows 10, version 1903. [Host WinRT XAML controls in desktop apps (XAML Islands)](/windows/apps/desktop/modernize/xaml-islands).

## Related topics
  - [Windows developer FAQ](windows-developer-faq.yml)
  - [Overview of app development options](/windows/apps/get-started#app-types)