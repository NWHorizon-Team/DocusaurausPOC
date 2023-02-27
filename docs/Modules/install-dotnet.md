---
title: Install .NET on Windows
description: Learn about the different ways you can install .NET and which versions of Windows support .NET.
---

- [Install on Windows](https://learn.microsoft.com/en-us/dotnet/core/install/windows)
- [Install on macOS](https://learn.microsoft.com/en-us/dotnet/core/install/macos)
- [Install on Linux](https://learn.microsoft.com/en-us/dotnet/core/install/linux)

In this article, you'll learn how to install .NET on Windows. .NET is made up of the runtime and the SDK. The runtime is used to run a .NET app and may or may not be included with the app. The SDK is used to create .NET apps and libraries. The .NET runtime is always installed with the SDK.

The latest version of .NET is 7.

There are two types of supported releases, Long Term Support (LTS) releases or Standard Term Support (STS). The quality of all releases is the same. The only difference is the length of support. LTS releases get free support and patches for 3 years. STS releases get free support and patches for 18 months. For more information, see [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

The following table lists the support status of each version of .NET (and .NET Core):

| ✔️ Supported | ❌ Unsupported |
| ----------- | ------------- |
| 7 (STS)     | 5             |
| 6 (LTS)     | 3.1           |
|             | 3.0           |
|             | 2.1           |
|             | 2.0           |
|             | 1.1           |
|             | 1.0           |

[](https://example.com/_generated_background_page.html#install-with-windows-package-manager-winget)

## Install with Windows Package Manager (winget)

You can install and manage .NET through the Windows Package Manager service, using the **winget** tool. For more information about how to install and use **winget**, see [Use the winget tool](https://example.com/en-us/windows/package-manager/winget/).

If you're installing .NET system-wide, install with administrative privileges.

[](https://example.com/_generated_background_page.html#install-the-sdk)

### Install the SDK

The .NET SDK allows you to develop apps with .NET. If you install the .NET SDK, you don't need to install the corresponding runtimes. To install the .NET SDK, run the following command:

```shell
winget install Microsoft.DotNet.SDK.7
```

[](https://example.com/_generated_background_page.html#install-the-runtime)

### Install the runtime

For Windows, there are three .NET runtimes you can install. You should install both the .NET Desktop Runtime and the ASP.NET Core Runtime to ensure that you're compatible with all types of .NET apps.

- .NET Desktop Runtime

    This runtime includes the base .NET runtime, and supports Windows Presentation Foundation (WPF) and Windows Forms apps that are built with .NET. This isn't the same as .NET Framework, which comes with Windows.

    ```
    winget install Microsoft.DotNet.DesktopRuntime.7
    ```

- ASP.NET Core Runtime

    This runtime includes the base .NET runtime, and runs web server apps. The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime. The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET. In your terminal, run the following commands:

    ```
    winget install Microsoft.DotNet.AspNetCore.7
    ```

- .NET Runtime

    This is the base runtime, and contains just the components needed to run a console app. Typically, you'd install the other runtimes.

    ```
    winget install Microsoft.DotNet.Runtime.7
    ```

You can install preview versions of the runtimes by substituting the version number, such as `6`, with the word `Preview`. The following example installs the preview release of the .NET Desktop Runtime:

```
winget install Microsoft.DotNet.DesktopRuntime.Preview
```

[](https://example.com/_generated_background_page.html#install-alongside-visual-studio-code)

## Install alongside Visual Studio Code

Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop. Visual Studio Code is available for Windows, macOS, and Linux.

While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.

1. [Download and install Visual Studio Code](https://code.visualstudio.com/Download).
2. [Download and install the .NET SDK](https://dotnet.microsoft.com/download/dotnet).
3. [Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

[](https://example.com/_generated_background_page.html#install-with-windows-installer)

## Install with Windows Installer

The [download page](https://dotnet.microsoft.com/download/dotnet) for .NET provides Windows Installer executables.

When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:

```
dotnet-sdk-7.0.100-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:

- `/install`  
    Installs .NET.

- `/quiet`  
    Prevents any UI and prompts from displaying.

- `/norestart`  
    Suppresses any attempts to restart.

```
dotnet-sdk-7.0.100-win-x64.exe /install /quiet /norestart
```

For more information, see [Standard Installer Command-Line Options](https://example.com/en-us/windows/win32/msi/standard-installer-command-line-options).

Tip

The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required. Any other value is generally an error code.

[](https://example.com/_generated_background_page.html#install-with-powershell-automation)

## Install with PowerShell automation

The [dotnet-install scripts](https://example.com/tools/dotnet-install-script) are used for CI automation and non-admin installs of the runtime. You can download the script from the [dotnet-install script reference page](https://example.com/tools/dotnet-install-script).

The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET 6. You can choose a specific release by specifying the `Channel` switch. Include the `Runtime` switch to install a runtime. Otherwise, the script installs the SDK.

The following command installs the ASP.NET Core runtime for maximum compatability. The ASP.NET Core runtime also includes the standard .NET runtime.

```
dotnet-install.ps1 -Channel 7.0 -Runtime aspnetcore
```

Install the SDK by omitting the `-Runtime` switch. The `-Channel` switch is set in this example to `STS`, which installs the latest Standard Term Support version (.NET 7).

```
dotnet-install.ps1 -Channel STS
```

[](https://example.com/_generated_background_page.html#install-with-visual-studio)

## Install with Visual Studio

If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.

| .NET SDK version | Visual Studio version                      |
| ---------------- | ------------------------------------------ |
| 7                | Visual Studio 2022 version 17.4 or higher. |
| 6                | Visual Studio 2022 version 17.0 or higher. |
| 5                | Visual Studio 2019 version 16.8 or higher. |
| 3.1              | Visual Studio 2019 version 16.4 or higher. |
| 3.0              | Visual Studio 2019 version 16.3 or higher. |
| 2.2              | Visual Studio 2017 version 15.9 or higher. |
| 2.1              | Visual Studio 2017 version 15.7 or higher. |

If you already have Visual Studio installed, you can check your version with the following steps.

1. Open Visual Studio.
2. Select **Help** > **About Microsoft Visual Studio**.
3. Read the version number from the **About** dialog.

Visual Studio can install the latest .NET SDK and runtime.

[](https://example.com/_generated_background_page.html#select-a-workload)

### Select a workload

When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:

- The **.NET Core cross-platform development** workload in the **Other Toolsets** section.
- The **ASP.NET and web development** workload in the **Web & Cloud** section.
- The **Azure development** workload in the **Web & Cloud** section.
- The **.NET desktop development** workload in the **Desktop & Mobile** section.

[![Windows Visual Studio 2019 with .NET Core workload](https://example.com/media/install-sdk/windows-install-visual-studio-2019.png)](https://example.com/media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

[](https://example.com/_generated_background_page.html#supported-releases)

## Supported releases

The following table is a list of currently supported .NET releases and the versions of Windows they're supported on. These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

Windows 10 versions end-of-service dates are segmented by edition. Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table. Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.

Tip

A `+` symbol represents the minimum version.

| Operating System                                                                                                                     | .NET 7 | .NET 6 |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------ | ------ |
| Windows 11                                                                                                                           | ✔️      | ✔️      |
| Windows Server 2022                                                                                                                  | ✔️      | ✔️      |
| Windows Server, Version 1903 or later                                                                                                | ✔️      | ✔️      |
| Windows 10, Version 1607 or later                                                                                                    | ✔️      | ✔️      |
| Windows 8.1                                                                                                                          | ❌      | ✔️      |
| Windows 7 SP1 [ESU](https://example.com/en-us/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq) | ❌      | ✔️      |
| Windows Server 2019                                                                                                                  |
Windows Server 2016  
Windows Server 2012 R2  
Windows Server 2012 | ✔️ |  |
| Windows Server Core 2012 R2 | ✔️ | ✔️ |
| Windows Server Core 2012 | ✔️ | ✔️ |
| Nano Server, Version 1809+ | ✔️ | ✔️ |
| Nano Server, Version 1803 | ❌ | ❌ |

For more information about .NET 7 supported operating systems, distributions, and lifecycle policy, see [.NET 7 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/7.0/supported-os.md).

[](https://example.com/_generated_background_page.html#unsupported-releases)

## Unsupported releases

The following versions of .NET are ❌ no longer supported:

- .NET 5
- .NET Core 3.1
- .NET Core 3.0
- .NET Core 2.2
- .NET Core 2.1
- .NET Core 2.0

[](https://example.com/_generated_background_page.html#runtime-information)

## Runtime information

The runtime is used to run apps created with .NET. When an app author publishes an app, they can include the runtime with their app. If they don't include the runtime, it's up to the user to install the runtime.

There are three different runtimes you can install on Windows:

- _ASP.NET Core runtime_  
    Runs ASP.NET Core apps. Includes the .NET runtime.

- _Desktop runtime_  
    Runs .NET WPF and Windows Forms desktop apps for Windows. Includes the .NET runtime.

- _.NET runtime_  
    This runtime is the simplest runtime and doesn't include any other runtime. It's highly recommended that you install both _ASP.NET Core runtime_ and _Desktop runtime_ for the best compatibility with .NET apps.

[](https://example.com/_generated_background_page.html#sdk-information)

## SDK information

The SDK is used to build and publish .NET apps and libraries. Installing the SDK includes all three [runtimes](https://example.com/_generated_background_page.html#runtime-information): ASP.NET Core, Desktop, and .NET.

[](https://example.com/_generated_background_page.html#arm-based-windows-pcs)

## Arm-based Windows PCs

The following sections describe things you should consider when installing .NET on an Arm-based Windows PC.

[](https://example.com/_generated_background_page.html#whats-supported)

### What's supported

The following table describes which versions of .NET are supported on an Arm-based Windows PC:

| .NET Version | Architecture | SDK | Runtime | [Path conflict](https://example.com/_generated_background_page.html#path-conflicts) |
| ------------ | ------------ | --- | ------- | ----------------------------------------------------------------------------------- |
| 7            | Arm64        | Yes | Yes     | No                                                                                  |
| 7            | x64          | Yes | Yes     | No                                                                                  |
| 6            | Arm64        | Yes | Yes     | No                                                                                  |
| 6            | x64          | Yes | Yes     | No                                                                                  |
| 5            | Arm64        | Yes | Yes     | [Yes](https://example.com/_generated_background_page.html#path-conflicts)           |
| 5            | x64          | No  | Yes     | [Yes](https://example.com/_generated_background_page.html#path-conflicts)           |

Starting with .NET 6, the x64 and Arm64 versions of the .NET SDK exist independently from each other. If a new version is released, each architecture install needs to be upgraded.

[](https://example.com/_generated_background_page.html#path-differences)

### Path differences

On an Arm-based Windows PC, all Arm64 versions of .NET are installed to the normal _C:\\Program Files\\dotnet\\_ folder. However, when you install the **x64** version of .NET 6 SDK or .NET 7 SDK, it's installed to the _C:\\Program Files\\dotnet\\x64\\_ folder.

[](https://example.com/_generated_background_page.html#path-conflicts)

### Path conflicts

Starting with .NET 6, the **x64** .NET SDK installs to its own directory, as described in the previous section. This allows the Arm64 and x64 versions of the .NET SDK to exist on the same machine. However, any **x64** SDK prior to 6 isn't supported and installs to the same location as the Arm64 version, the _C:\\Program Files\\dotnet\\_ folder. If you want to install an unsupported x64 SDK, you'll need to first uninstall the Arm64 version. The opposite is also true, you'll need to uninstall the unsupported x64 SDK to install the Arm64 version.

[](https://example.com/_generated_background_page.html#path-variables)

### Path variables

Environment variables that add .NET to system path, such as the `PATH` variable, may need to be changed if you have both the x64 and Arm64 versions of the .NET SDK installed. Additionally, some tools rely on the `DOTNET_ROOT` environment variable, which would also need to be updated to point to the appropriate .NET SDK installation folder.

[](https://example.com/_generated_background_page.html#dependencies)

## Dependencies

- [.NET 7](https://example.com/_generated_background_page.html#tabpanel_1_net70)
- [.NET 6](https://example.com/_generated_background_page.html#tabpanel_1_net60)

The following Windows versions are supported with .NET 7:

Note

A `+` symbol represents the minimum version.

| OS                  | Version     | Architectures   |
| ------------------- | ----------- | --------------- |
| Windows 11          | 21H2+       | x64, Arm64      |
| Windows 10 Client   | 1607+       | x64, x86, Arm64 |
| Windows Client      | 7 SP1+, 8.1 | x64, x86        |
| Windows Server      | 2012+       | x64, x86        |
| Windows Server Core | 2012+       | x64, x86        |
| Nano Server         | 1809+       | x64             |

For more information about .NET 7 supported operating systems, distributions, and lifecycle policy, see [.NET 7 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/7.0/supported-os.md).

The following Windows versions are supported with .NET 6:

Note

A `+` symbol represents the minimum version.

| OS                  | Version     | Architectures   |
| ------------------- | ----------- | --------------- |
| Windows 11          | 21H2+       | x64, Arm64      |
| Windows 10 Client   | 1607+       | x64, x86, Arm64 |
| Windows Client      | 7 SP1+, 8.1 | x64, x86        |
| Windows Server      | 2012+       | x64, x86        |
| Windows Server Core | 2012+       | x64, x86        |
| Nano Server         | 1809+       | x64             |

For more information about .NET 6 supported operating systems, distributions, and lifecycle policy, see [.NET 6 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/6.0/supported-os.md).

[](https://example.com/_generated_background_page.html#offline-install-for-windows-7)

### Offline install for Windows 7

Important

This section only applies to .NET Core 2.1.

When doing an offline install for .NET Core 2.1 on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.

The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK. The following command is used to install the certificate before running the .NET Core 2.1 installer:

```
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

Be sure to review the dependencies required for [Windows 7 below](https://example.com/_generated_background_page.html#additional-deps).

[](https://example.com/_generated_background_page.html#additional-deps)

### Windows 7 / 8.1 / Server 2012

More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:

The previous requirements are also required if you receive an error related to either of the following dlls:

- _api-ms-win-crt-runtime-l1-1-0.dll_
- _api-ms-win-cor-timezone-l1-1-0.dll_
- _hostfxr.dll_

[](https://example.com/_generated_background_page.html#docker)

## Docker

Containers provide a lightweight way to isolate your application from the rest of the host system. Containers on the same machine share just the kernel and use resources given to your application.

.NET can run in a Docker container. Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet). Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.

Microsoft provides images that are tailored for specific scenarios. For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.

For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](https://example.com/docker/introduction) and [Samples](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md).

[](https://example.com/_generated_background_page.html#troubleshooting)

## Troubleshooting

After installing the .NET SDK, you may run into problems trying to run .NET CLI commands. This section collects those common problems and provides solutions.

- [It was not possible to find any installed .NET Core SDKs](https://example.com/_generated_background_page.html#it-was-not-possible-to-find-any-installed-net-core-sdks)

[](https://example.com/_generated_background_page.html#it-was-not-possible-to-find-any-installed-net-core-sdks)

### It was not possible to find any installed .NET Core SDKs

Most likely you've installed both the x86 (32-bit) and x64 (64-bit) versions of the .NET SDK. This is causing a conflict because when you run the `dotnet` command it's resolving to the x86 version when it should resolve to the x64 version. This is usually fixed by adjusting the `%PATH%` variable to resolve the x64 version first.

1. Verify that you have both versions installed by running the `where.exe dotnet` command. If you do, you should see an entry for both the _Program Files\\_ and _Program Files (x86)\\_ folders. If the _Program Files (x86)\\_ folder is first as indicated by the following example, it's incorrect and you should continue on to the next step.

    ```
    > where.exe dotnet
    C:\Program Files (x86)\dotnet\dotnet.exe  
    C:\Program Files\dotnet\dotnet.exe
    ```

    If it's correct and the _Program Files\\_ is first, you don't have the problem this section is discussing and you should create a [.NET help request issue on GitHub](https://github.com/dotnet/core/issues/new?assignees=&labels=&template=01_bug_report.md&title=)

2. Press the Windows button and type "Edit the system environment variables" into search. Select **Edit the system environment variables**.

    ![Windows start menu with edit environment variable](https://example.com/media/windows/start-menu.png)

3. The **System Properties** window opens up to the **Advanced Tab**. Select **Environment Variables**.

    ![The Windows system properties panel open.](https://example.com/media/windows/system-props.png)

4. On the **Environment Variables** window, under the **System variables** group, select the _Path_\* row and then select the **Edit** button.

    ![The environment variables window with user and system variables.](https://example.com/media/windows/list-vars.png)

5. Use the **Move Up** and **Move Down** buttons to move the **C:\\Program Files\\dotnet\\** entry above **C:\\Program Files (x86)\\dotnet\\**.

    ![The environment variables list for the system.](https://example.com/media/windows/edit-vars.png)

[](https://example.com/_generated_background_page.html#next-steps)

## Next steps

- [How to check if .NET is already installed](https://example.com/how-to-detect-installed-versions?pivots=os-windows).
- [Tutorial: Hello World tutorial](https://example.com/tutorials/with-visual-studio).
- [Tutorial: Create a new app with Visual Studio Code](https://example.com/tutorials/with-visual-studio-code).
- [Tutorial: Containerize a .NET Core app](https://example.com/docker/build-container).

___

## Recommended content

- ### [Remove the .NET runtime and SDK - .NET](https://example.com/en-us/dotnet/core/install/remove-runtime-sdk-versions?source=recommendations)

    This article describes how to determine which versions of the .NET Runtime and SDK are currently installed, and then, how to remove them on Windows, Mac, and Linux.

- ### [Check installed .NET versions on Windows, Linux, and macOS - .NET](https://example.com/en-us/dotnet/core/install/how-to-detect-installed-versions?source=recommendations)

    Learn how to list which versions of .NET are installed on your computer. This includes the .NET runtime and SDK.

- ### [Uninstall Tool - .NET](https://example.com/en-us/dotnet/core/additional-tools/uninstall-tool?source=recommendations)

    An overview of the .NET Uninstall Tool, a guided tool that enables the controlled clean-up of .NET SDKs and runtimes.

- ### [dotnet-install scripts - .NET CLI](https://example.com/en-us/dotnet/core/tools/dotnet-install-script?source=recommendations)

    Learn about the dotnet-install scripts to install the .NET SDK and the shared runtime.

- ### [Select which .NET version to use - .NET](https://example.com/en-us/dotnet/core/versions/selection?source=recommendations)

    Learn how .NET automatically finds and chooses runtime versions for your program. Additionally, this article teaches you how to force a specific version.

- ### [dotnet sdk check command - .NET CLI](https://example.com/en-us/dotnet/core/tools/dotnet-sdk-check?source=recommendations)

    The 'dotnet sdk check' command tells you what is the latest available version of the .NET SDK and .NET Runtime.

- ### [Troubleshoot app launch failures](https://example.com/en-us/dotnet/core/runtime-discovery/troubleshoot-app-launch?source=recommendations)

    Learn about common reasons for app launch failures and possible solutions.

- ### [dotnet command - .NET CLI](https://example.com/en-us/dotnet/core/tools/dotnet?source=recommendations)

    Learn about the dotnet command (the generic driver for the .NET CLI) and its usage.

## Feedback

Submit and view feedback for

___

## Additional resources

- [Install with Windows Package Manager (winget)](https://example.com/_generated_background_page.html#install-with-windows-package-manager-winget)
- [Install alongside Visual Studio Code](https://example.com/_generated_background_page.html#install-alongside-visual-studio-code)
- [Install with Windows Installer](https://example.com/_generated_background_page.html#install-with-windows-installer)
- [Install with PowerShell automation](https://example.com/_generated_background_page.html#install-with-powershell-automation)
- [Install with Visual Studio](https://example.com/_generated_background_page.html#install-with-visual-studio)
- [Supported releases](https://example.com/_generated_background_page.html#supported-releases)
- [Unsupported releases](https://example.com/_generated_background_page.html#unsupported-releases)
- [Runtime information](https://example.com/_generated_background_page.html#runtime-information)
- [SDK information](https://example.com/_generated_background_page.html#sdk-information)
- [Arm-based Windows PCs](https://example.com/_generated_background_page.html#arm-based-windows-pcs)
- [Dependencies](https://example.com/_generated_background_page.html#dependencies)
- [Docker](https://example.com/_generated_background_page.html#docker)
- [Troubleshooting](https://example.com/_generated_background_page.html#troubleshooting)
- [Next steps](https://example.com/_generated_background_page.html#next-steps)
