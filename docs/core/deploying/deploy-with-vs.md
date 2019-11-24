---
title: Deploy .NET Core apps with Visual Studio
description: Learn to deploy a .NET Core app with Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f80b483fedc600a1e1a48d36ce9b7b95c6de9f27
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428893"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="abb72-103">Deploy .NET Core apps with Visual Studio</span><span class="sxs-lookup"><span data-stu-id="abb72-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="abb72-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span><span class="sxs-lookup"><span data-stu-id="abb72-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="abb72-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span><span class="sxs-lookup"><span data-stu-id="abb72-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="abb72-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span><span class="sxs-lookup"><span data-stu-id="abb72-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="abb72-107">Framework-dependent deployment</span><span class="sxs-lookup"><span data-stu-id="abb72-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="abb72-108">Framework-dependent deployment with third-party dependencies</span><span class="sxs-lookup"><span data-stu-id="abb72-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="abb72-109">Self-contained deployment</span><span class="sxs-lookup"><span data-stu-id="abb72-109">Self-contained deployment</span></span>
- <span data-ttu-id="abb72-110">Self-contained deployment with third-party dependencies</span><span class="sxs-lookup"><span data-stu-id="abb72-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="abb72-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="abb72-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="abb72-112">Framework-dependent deployment</span><span class="sxs-lookup"><span data-stu-id="abb72-112">Framework-dependent deployment</span></span>

<span data-ttu-id="abb72-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span><span class="sxs-lookup"><span data-stu-id="abb72-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="abb72-114">A simple example written in C# illustrates the process.</span><span class="sxs-lookup"><span data-stu-id="abb72-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="abb72-115">Create the project.</span><span class="sxs-lookup"><span data-stu-id="abb72-115">Create the project.</span></span>

   <span data-ttu-id="abb72-116">Select **File** > **New** > **Project**.</span><span class="sxs-lookup"><span data-stu-id="abb72-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="abb72-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span><span class="sxs-lookup"><span data-stu-id="abb72-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="abb72-118">Enter a project name, such as "FDD", in the **Name** text box.</span><span class="sxs-lookup"><span data-stu-id="abb72-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="abb72-119">Select the **OK** button.</span><span class="sxs-lookup"><span data-stu-id="abb72-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="abb72-120">Add the application's source code.</span><span class="sxs-lookup"><span data-stu-id="abb72-120">Add the application's source code.</span></span>

   <span data-ttu-id="abb72-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span><span class="sxs-lookup"><span data-stu-id="abb72-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="abb72-122">It prompts the user to enter text and displays the individual words entered by the user.</span><span class="sxs-lookup"><span data-stu-id="abb72-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="abb72-123">It uses the regular expression `\w+` to separate the words in the input text.</span><span class="sxs-lookup"><span data-stu-id="abb72-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="abb72-124">Create a Debug build of your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="abb72-125">Select **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="abb72-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="abb72-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span><span class="sxs-lookup"><span data-stu-id="abb72-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="abb72-127">Deploy your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-127">Deploy your app.</span></span>

   <span data-ttu-id="abb72-128">After you've debugged and tested the program, create the files to be deployed with your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="abb72-129">To publish from Visual Studio, do the following:</span><span class="sxs-lookup"><span data-stu-id="abb72-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="abb72-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="abb72-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span><span class="sxs-lookup"><span data-stu-id="abb72-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="abb72-132">In the **Publish** tab, select **Publish**.</span><span class="sxs-lookup"><span data-stu-id="abb72-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="abb72-133">Visual Studio writes the files that comprise your application to the local file system.</span><span class="sxs-lookup"><span data-stu-id="abb72-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="abb72-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="abb72-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="abb72-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span><span class="sxs-lookup"><span data-stu-id="abb72-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="abb72-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span><span class="sxs-lookup"><span data-stu-id="abb72-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="abb72-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="abb72-138">The file is useful primarily for debugging exceptions.</span><span class="sxs-lookup"><span data-stu-id="abb72-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="abb72-139">You can choose not to package it with your application's files.</span><span class="sxs-lookup"><span data-stu-id="abb72-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="abb72-140">You should, however, save it in the event that you want to debug the Release build of your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="abb72-141">Deploy the complete set of application files in any way you like.</span><span class="sxs-lookup"><span data-stu-id="abb72-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="abb72-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span><span class="sxs-lookup"><span data-stu-id="abb72-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="abb72-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="abb72-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="abb72-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span><span class="sxs-lookup"><span data-stu-id="abb72-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="abb72-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span><span class="sxs-lookup"><span data-stu-id="abb72-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="abb72-146">Framework-dependent deployment with third-party dependencies</span><span class="sxs-lookup"><span data-stu-id="abb72-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="abb72-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span><span class="sxs-lookup"><span data-stu-id="abb72-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="abb72-148">The following additional steps are required before you can build your app:</span><span class="sxs-lookup"><span data-stu-id="abb72-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="abb72-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span><span class="sxs-lookup"><span data-stu-id="abb72-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="abb72-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span><span class="sxs-lookup"><span data-stu-id="abb72-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="abb72-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span><span class="sxs-lookup"><span data-stu-id="abb72-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="abb72-152">The **Installed** tab lists NuGet packages installed on your system.</span><span class="sxs-lookup"><span data-stu-id="abb72-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="abb72-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span><span class="sxs-lookup"><span data-stu-id="abb72-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="abb72-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span><span class="sxs-lookup"><span data-stu-id="abb72-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="abb72-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span><span class="sxs-lookup"><span data-stu-id="abb72-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="abb72-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span><span class="sxs-lookup"><span data-stu-id="abb72-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="abb72-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span><span class="sxs-lookup"><span data-stu-id="abb72-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="abb72-158">This happens if the third-party dependency itself depends on native code.</span><span class="sxs-lookup"><span data-stu-id="abb72-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="abb72-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="abb72-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="abb72-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span><span class="sxs-lookup"><span data-stu-id="abb72-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="abb72-161">Self-contained deployment without third-party dependencies</span><span class="sxs-lookup"><span data-stu-id="abb72-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="abb72-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span><span class="sxs-lookup"><span data-stu-id="abb72-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="abb72-163">A simple example written in C# illustrates the process.</span><span class="sxs-lookup"><span data-stu-id="abb72-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="abb72-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span><span class="sxs-lookup"><span data-stu-id="abb72-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="abb72-165">Create the project.</span><span class="sxs-lookup"><span data-stu-id="abb72-165">Create the project.</span></span>

   <span data-ttu-id="abb72-166">Select **File** > **New** > **Project**.</span><span class="sxs-lookup"><span data-stu-id="abb72-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="abb72-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span><span class="sxs-lookup"><span data-stu-id="abb72-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="abb72-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span><span class="sxs-lookup"><span data-stu-id="abb72-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="abb72-169">Add the application's source code.</span><span class="sxs-lookup"><span data-stu-id="abb72-169">Add the application's source code.</span></span>

   <span data-ttu-id="abb72-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the auto-generated code with the following code.</span><span class="sxs-lookup"><span data-stu-id="abb72-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="abb72-171">It prompts the user to enter text and displays the individual words entered by the user.</span><span class="sxs-lookup"><span data-stu-id="abb72-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="abb72-172">It uses the regular expression `\w+` to separate the words in the input text.</span><span class="sxs-lookup"><span data-stu-id="abb72-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="abb72-173">Determine whether you want to use globalization invariant mode.</span><span class="sxs-lookup"><span data-stu-id="abb72-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="abb72-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="abb72-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="abb72-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="abb72-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="abb72-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="abb72-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="abb72-177">Then add the following highlighted lines to the file:</span><span class="sxs-lookup"><span data-stu-id="abb72-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. <span data-ttu-id="abb72-178">Create a Debug build of your application.</span><span class="sxs-lookup"><span data-stu-id="abb72-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="abb72-179">Select **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="abb72-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="abb72-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span><span class="sxs-lookup"><span data-stu-id="abb72-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="abb72-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span><span class="sxs-lookup"><span data-stu-id="abb72-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="abb72-182">You still will have to test it on each of your target platforms.</span><span class="sxs-lookup"><span data-stu-id="abb72-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="abb72-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span><span class="sxs-lookup"><span data-stu-id="abb72-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="abb72-184">Once you've finished debugging, you can publish your self-contained deployment:</span><span class="sxs-lookup"><span data-stu-id="abb72-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="abb72-185">Visual Studio 15.6 and earlier</span><span class="sxs-lookup"><span data-stu-id="abb72-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="abb72-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span><span class="sxs-lookup"><span data-stu-id="abb72-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="abb72-187">To publish your app from Visual Studio, do the following:</span><span class="sxs-lookup"><span data-stu-id="abb72-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="abb72-188">Define the platforms that your app will target.</span><span class="sxs-lookup"><span data-stu-id="abb72-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="abb72-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="abb72-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="abb72-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span><span class="sxs-lookup"><span data-stu-id="abb72-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="abb72-191">Note that you also need to add a semicolon to separate the RIDs.</span><span class="sxs-lookup"><span data-stu-id="abb72-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="abb72-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span><span class="sxs-lookup"><span data-stu-id="abb72-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="abb72-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span><span class="sxs-lookup"><span data-stu-id="abb72-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="abb72-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span><span class="sxs-lookup"><span data-stu-id="abb72-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="abb72-195">A complete sample *csproj* file appears later in this section.</span><span class="sxs-lookup"><span data-stu-id="abb72-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="abb72-196">Publish your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-196">Publish your app.</span></span>

   <span data-ttu-id="abb72-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span><span class="sxs-lookup"><span data-stu-id="abb72-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="abb72-198">To publish your app from Visual Studio, do the following:</span><span class="sxs-lookup"><span data-stu-id="abb72-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="abb72-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="abb72-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span><span class="sxs-lookup"><span data-stu-id="abb72-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="abb72-201">In the **Publish** tab, select **Publish**.</span><span class="sxs-lookup"><span data-stu-id="abb72-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="abb72-202">Visual Studio writes the files that comprise your application to the local file system.</span><span class="sxs-lookup"><span data-stu-id="abb72-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="abb72-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="abb72-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="abb72-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span><span class="sxs-lookup"><span data-stu-id="abb72-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="abb72-205">Visual Studio by default writes all published files to a single directory.</span><span class="sxs-lookup"><span data-stu-id="abb72-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="abb72-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span><span class="sxs-lookup"><span data-stu-id="abb72-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="abb72-207">This involves creating a separate publishing profile for each target platform.</span><span class="sxs-lookup"><span data-stu-id="abb72-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="abb72-208">So now rebuild the application for each platform by doing the following:</span><span class="sxs-lookup"><span data-stu-id="abb72-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="abb72-209">Select **Create new profile** in the **Publish** dialog.</span><span class="sxs-lookup"><span data-stu-id="abb72-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="abb72-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="abb72-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="abb72-211">Select **OK**.</span><span class="sxs-lookup"><span data-stu-id="abb72-211">Select **OK**.</span></span>

         1. <span data-ttu-id="abb72-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="abb72-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="abb72-213">If it isn't, select **Settings**.</span><span class="sxs-lookup"><span data-stu-id="abb72-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="abb72-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span><span class="sxs-lookup"><span data-stu-id="abb72-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="abb72-215">Otherwise, select **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="abb72-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="abb72-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span><span class="sxs-lookup"><span data-stu-id="abb72-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="abb72-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span><span class="sxs-lookup"><span data-stu-id="abb72-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="abb72-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="abb72-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="abb72-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="abb72-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="abb72-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="abb72-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="abb72-222">The file is useful primarily for debugging exceptions.</span><span class="sxs-lookup"><span data-stu-id="abb72-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="abb72-223">You can choose not to package it with your application's files.</span><span class="sxs-lookup"><span data-stu-id="abb72-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="abb72-224">You should, however, save it in the event that you want to debug the Release build of your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="abb72-225">Deploy the published files in any way you like.</span><span class="sxs-lookup"><span data-stu-id="abb72-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="abb72-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span><span class="sxs-lookup"><span data-stu-id="abb72-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="abb72-227">The following is the complete *csproj* file for this project.</span><span class="sxs-lookup"><span data-stu-id="abb72-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="abb72-228">Visual Studio 15.7 and later</span><span class="sxs-lookup"><span data-stu-id="abb72-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="abb72-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span><span class="sxs-lookup"><span data-stu-id="abb72-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="abb72-230">This involves creating a separate profile for each target platform.</span><span class="sxs-lookup"><span data-stu-id="abb72-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="abb72-231">For each platform that your application targets, do the following:</span><span class="sxs-lookup"><span data-stu-id="abb72-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="abb72-232">Create a profile for your target platform.</span><span class="sxs-lookup"><span data-stu-id="abb72-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="abb72-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span><span class="sxs-lookup"><span data-stu-id="abb72-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="abb72-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span><span class="sxs-lookup"><span data-stu-id="abb72-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="abb72-235">Then select **New Profile**.</span><span class="sxs-lookup"><span data-stu-id="abb72-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="abb72-236">The **Pick a Publish Target** dialog box opens.</span><span class="sxs-lookup"><span data-stu-id="abb72-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="abb72-237">Select the location where Visual Studio publishes your application.</span><span class="sxs-lookup"><span data-stu-id="abb72-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="abb72-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span><span class="sxs-lookup"><span data-stu-id="abb72-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="abb72-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span><span class="sxs-lookup"><span data-stu-id="abb72-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="abb72-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span><span class="sxs-lookup"><span data-stu-id="abb72-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="abb72-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span><span class="sxs-lookup"><span data-stu-id="abb72-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="abb72-242">Then select the **Create Profile** button to create the profile.</span><span class="sxs-lookup"><span data-stu-id="abb72-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="abb72-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span><span class="sxs-lookup"><span data-stu-id="abb72-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="abb72-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span><span class="sxs-lookup"><span data-stu-id="abb72-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="abb72-245">Select **Self-contained** in the **Deployment Mode** list box.</span><span class="sxs-lookup"><span data-stu-id="abb72-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="abb72-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span><span class="sxs-lookup"><span data-stu-id="abb72-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="abb72-247">Select **Save** to accept your changes and close the dialog.</span><span class="sxs-lookup"><span data-stu-id="abb72-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="abb72-248">Name your profile.</span><span class="sxs-lookup"><span data-stu-id="abb72-248">Name your profile.</span></span>

   1. <span data-ttu-id="abb72-249">Select **Actions** > **Rename Profile** to name your profile.</span><span class="sxs-lookup"><span data-stu-id="abb72-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="abb72-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span><span class="sxs-lookup"><span data-stu-id="abb72-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="abb72-251">Repeat these steps to define any additional target platforms that your application targets.</span><span class="sxs-lookup"><span data-stu-id="abb72-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="abb72-252">You've configured your profiles and are now ready to publish your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="abb72-253">To do this:</span><span class="sxs-lookup"><span data-stu-id="abb72-253">To do this:</span></span>

   1. <span data-ttu-id="abb72-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span><span class="sxs-lookup"><span data-stu-id="abb72-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="abb72-255">Select the profile that you'd like to publish, then select **Publish**.</span><span class="sxs-lookup"><span data-stu-id="abb72-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="abb72-256">Do this for each profile to be published.</span><span class="sxs-lookup"><span data-stu-id="abb72-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="abb72-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="abb72-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="abb72-259">The file is useful primarily for debugging exceptions.</span><span class="sxs-lookup"><span data-stu-id="abb72-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="abb72-260">You can choose not to package it with your application's files.</span><span class="sxs-lookup"><span data-stu-id="abb72-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="abb72-261">You should, however, save it in the event that you want to debug the Release build of your app.</span><span class="sxs-lookup"><span data-stu-id="abb72-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="abb72-262">Deploy the published files in any way you like.</span><span class="sxs-lookup"><span data-stu-id="abb72-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="abb72-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span><span class="sxs-lookup"><span data-stu-id="abb72-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="abb72-264">The following is the complete *csproj* file for this project.</span><span class="sxs-lookup"><span data-stu-id="abb72-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="abb72-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span><span class="sxs-lookup"><span data-stu-id="abb72-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="abb72-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span><span class="sxs-lookup"><span data-stu-id="abb72-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="abb72-267">Self-contained deployment with third-party dependencies</span><span class="sxs-lookup"><span data-stu-id="abb72-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="abb72-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span><span class="sxs-lookup"><span data-stu-id="abb72-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="abb72-269">The following additional steps are required before you can build your app:</span><span class="sxs-lookup"><span data-stu-id="abb72-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="abb72-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span><span class="sxs-lookup"><span data-stu-id="abb72-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="abb72-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span><span class="sxs-lookup"><span data-stu-id="abb72-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="abb72-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span><span class="sxs-lookup"><span data-stu-id="abb72-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="abb72-273">The **Installed** tab lists NuGet packages installed on your system.</span><span class="sxs-lookup"><span data-stu-id="abb72-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="abb72-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span><span class="sxs-lookup"><span data-stu-id="abb72-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="abb72-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span><span class="sxs-lookup"><span data-stu-id="abb72-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="abb72-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span><span class="sxs-lookup"><span data-stu-id="abb72-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="abb72-277">The following is the complete *csproj* file for this project:</span><span class="sxs-lookup"><span data-stu-id="abb72-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="abb72-278">Visual Studio 15.6 and earlier</span><span class="sxs-lookup"><span data-stu-id="abb72-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="abb72-279">Visual Studio 15.7 and later</span><span class="sxs-lookup"><span data-stu-id="abb72-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="abb72-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span><span class="sxs-lookup"><span data-stu-id="abb72-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="abb72-281">Third-party libraries aren't required on the system on which the app is running.</span><span class="sxs-lookup"><span data-stu-id="abb72-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="abb72-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span><span class="sxs-lookup"><span data-stu-id="abb72-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="abb72-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span><span class="sxs-lookup"><span data-stu-id="abb72-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="abb72-284">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abb72-284">See also</span></span>

- [<span data-ttu-id="abb72-285">.NET Core Application Deployment</span><span class="sxs-lookup"><span data-stu-id="abb72-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="abb72-286">.NET Core Runtime IDentifier (RID) catalog</span><span class="sxs-lookup"><span data-stu-id="abb72-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
