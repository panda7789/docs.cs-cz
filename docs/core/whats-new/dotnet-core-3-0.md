---
title: Co je nového v .NET Core 3.0
description: Další informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 6e85c2c3e796ae59a13f944bd4913e4b7316c56a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398809"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="30c4d-103">Co je nového v .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="30c4d-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="30c4d-104">Tento článek popisuje, co je novév rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="30c4d-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="30c4d-105">Jedním z největších vylepšení je podpora desktopových aplikací pro Windows (pouze windows).</span><span class="sxs-lookup"><span data-stu-id="30c4d-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="30c4d-106">Pomocí součásti .NET Core 3.0 SDK windows desktop můžete přenést windows forms a windows presentation foundation (WPF) aplikace.</span><span class="sxs-lookup"><span data-stu-id="30c4d-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="30c4d-107">Aby bylo jasno, součást Plochy systému Windows je podporována a zahrnuta pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="30c4d-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="30c4d-108">Další informace naleznete v části [Plocha systému Windows](#windows-desktop) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="30c4d-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="30c4d-109">.NET Core 3.0 přidává podporu pro C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="30c4d-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="30c4d-110">Důrazně doporučujeme používat [Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější, [Visual Studio pro Mac 8.3](/visualstudio/mac/install-preview) nebo novější nebo [Visual Studio Code](https://code.visualstudio.com/) s **nejnovějším rozšířením C#**.</span><span class="sxs-lookup"><span data-stu-id="30c4d-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="30c4d-111">[Stáhněte si a s rozhraním .NET Core 3.0](https://aka.ms/netcore3download) si můžete začít hned teď v systémech Windows, macOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="30c4d-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="30c4d-112">Další informace o vydání naleznete v [oznámení .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="30c4d-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="30c4d-113">.NET Core RC1 byl považován za připravený na výrobu společností Microsoft a byl plně podporován.</span><span class="sxs-lookup"><span data-stu-id="30c4d-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="30c4d-114">Pokud používáte verzi preview, musíte přejít na verzi RTM, abyste měli trvalou podporu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="30c4d-115">Vylepšení jazyka C# 8.0</span><span class="sxs-lookup"><span data-stu-id="30c4d-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="30c4d-116">C# 8.0 je také součástí této verze, která zahrnuje funkce [reference s možností null,](../../csharp/tutorials/nullable-reference-types.md) [asynchronní datové proudy](../../csharp/tutorials/generate-consume-asynchronous-stream.md)a [další vzorky](../../csharp/tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="30c4d-117">Další informace o funkcích jazyka C# 8.0 naleznete [v tématu Co je nového v c# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="30c4d-118">Pro podporu následujících funkcí rozhraní API, které jsou podrobně popsány, byla přidána vylepšení jazyka:</span><span class="sxs-lookup"><span data-stu-id="30c4d-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="30c4d-119">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="30c4d-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="30c4d-120">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="30c4d-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="30c4d-121">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="30c4d-121">.NET Standard 2.1</span></span>

<span data-ttu-id="30c4d-122">.NET Core 3.0 implementuje **standard .NET 2.1**.</span><span class="sxs-lookup"><span data-stu-id="30c4d-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="30c4d-123">Výchozí `dotnet new classlib` šablona však generuje projekt, který stále cílí **na standard .NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="30c4d-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="30c4d-124">Chcete-li cílit na **rozhraní .NET Standard 2.1**, upravte soubor projektu a změňte `TargetFramework` vlastnost na `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="30c4d-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="30c4d-125">Pokud používáte Visual Studio, potřebujete [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), protože Visual Studio 2017 nepodporuje **rozhraní .NET Standard 2.1** nebo **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="30c4d-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="30c4d-126">Kompilace/nasazení</span><span class="sxs-lookup"><span data-stu-id="30c4d-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="30c4d-127">Výchozí spustitelné soubory</span><span class="sxs-lookup"><span data-stu-id="30c4d-127">Default executables</span></span>

<span data-ttu-id="30c4d-128">Rozhraní .NET Core nyní ve výchozím nastavení vytváří [spustitelné soubory závislé na modulu runtime.](../deploying/index.md#publish-runtime-dependent)</span><span class="sxs-lookup"><span data-stu-id="30c4d-128">.NET Core now builds [runtime-dependent executables](../deploying/index.md#publish-runtime-dependent) by default.</span></span> <span data-ttu-id="30c4d-129">Toto chování je nové pro aplikace, které používají globálně nainstalovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30c4d-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="30c4d-130">Dříve pouze [samostatné nasazení](../deploying/index.md#publish-self-contained) by vytvořit spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="30c4d-130">Previously, only [self-contained deployments](../deploying/index.md#publish-self-contained) would produce an executable.</span></span>

<span data-ttu-id="30c4d-131">Během `dotnet build` `dotnet publish`nebo , je vytvořen spustitelný soubor (označovaný jako **appHost**), který odpovídá prostředí a platformě sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="30c4d-131">During `dotnet build` or `dotnet publish`, an executable (known as the **appHost**) is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="30c4d-132">U těchto spustitelných souborů můžete očekávat stejné věci jako jiné nativní spustitelné soubory, například:</span><span class="sxs-lookup"><span data-stu-id="30c4d-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="30c4d-133">Můžete poklepat na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="30c4d-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="30c4d-134">Aplikaci můžete spustit přímo z příkazového `myapp.exe` řádku, `./myapp` například ve Windows a v Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="30c4d-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="macos-apphost-and-notarization"></a><span data-ttu-id="30c4d-135">aplikace macOSHost a notářská izace</span><span class="sxs-lookup"><span data-stu-id="30c4d-135">macOS appHost and notarization</span></span>

<span data-ttu-id="30c4d-136">*pouze macOS*</span><span class="sxs-lookup"><span data-stu-id="30c4d-136">*macOS only*</span></span>

<span data-ttu-id="30c4d-137">Počínaje notářsky opravovanou sadou .NET Core SDK 3.0 pro macOS je nastavení vytvoření výchozího spustitelného souboru (známého jako appHost) ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="30c4d-137">Starting with the notarized .NET Core SDK 3.0 for macOS, the setting to produce a default executable (known as the appHost) is disabled by default.</span></span> <span data-ttu-id="30c4d-138">Další informace najdete v [tématu macOS Catalina Notarization a dopad na stahování a projekty .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-138">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="30c4d-139">Když je povoleno nastavení appHost, .NET Core generuje nativní Mach-O spustitelný soubor při vytváření nebo publikování.</span><span class="sxs-lookup"><span data-stu-id="30c4d-139">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="30c4d-140">Vaše aplikace běží v kontextu appHost při spuštění ze `dotnet run` zdrojového kódu pomocí příkazu nebo spuštěním spustitelného souboru Mach-O přímo.</span><span class="sxs-lookup"><span data-stu-id="30c4d-140">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="30c4d-141">Bez appHost, jediný způsob, jak uživatel může spustit aplikaci `dotnet <filename.dll>` [závislou na běhu](../deploying/index.md#publish-runtime-dependent) je pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-141">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="30c4d-142">AppHost se vždy vytvoří, když publikujete aplikaci [samostatnou](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="30c4d-142">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="30c4d-143">Můžete buď nakonfigurovat appHost na úrovni projektu, nebo přepnout `dotnet` appHost `-p:UseAppHost` pro konkrétní příkaz s parametrem:</span><span class="sxs-lookup"><span data-stu-id="30c4d-143">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="30c4d-144">Soubor projektu</span><span class="sxs-lookup"><span data-stu-id="30c4d-144">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="30c4d-145">Parametr příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="30c4d-145">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="30c4d-146">Další informace o `UseAppHost` nastavení naleznete v [tématu Vlastnosti MSBuild pro sadu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="30c4d-146">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="30c4d-147">Spustitelné soubory s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="30c4d-147">Single-file executables</span></span>

<span data-ttu-id="30c4d-148">Příkaz `dotnet publish` podporuje balení aplikace do spustitelného souboru pro jeden soubor specifický pro platformu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-148">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="30c4d-149">Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativní), které jsou nutné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="30c4d-149">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="30c4d-150">Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru sestavení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-150">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="30c4d-151">Při opětovném spuštění aplikace je spuštění rychlejší.</span><span class="sxs-lookup"><span data-stu-id="30c4d-151">Startup is faster when the application is run again.</span></span> <span data-ttu-id="30c4d-152">Aplikace nemusí extrahovat sám podruhé, pokud byla použita nová verze.</span><span class="sxs-lookup"><span data-stu-id="30c4d-152">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="30c4d-153">Chcete-li publikovat spustitelný soubor `PublishSingleFile` s jedním souborem, nastavte `dotnet publish` v projektu nebo na příkazovém řádku pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="30c4d-153">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="30c4d-154">-nebo-</span><span class="sxs-lookup"><span data-stu-id="30c4d-154">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="30c4d-155">Další informace o publikování na jednom souboru naleznete v [návrhovém dokumentu sdružených souborů s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-155">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="30c4d-156">Propojení sestavy</span><span class="sxs-lookup"><span data-stu-id="30c4d-156">Assembly linking</span></span>

<span data-ttu-id="30c4d-157">Sada .NET core 3.0 SDK je dodávána s nástrojem, který může zmenšit velikost aplikací analýzou IL a oříznutím nepoužívaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-157">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="30c4d-158">Samostatné aplikace obsahují vše potřebné ke spuštění kódu, aniž by bylo nutné nainstalovat rozhraní .NET do hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="30c4d-158">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="30c4d-159">Mnohokrát však aplikace vyžaduje pouze malou podmnožinu rozhraní pro fungování a jiné nepoužívané knihovny mohou být odebrány.</span><span class="sxs-lookup"><span data-stu-id="30c4d-159">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="30c4d-160">.NET Core nyní obsahuje nastavení, které bude používat nástroj [propojovací program IL](https://github.com/mono/linker) ke skenování IL vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="30c4d-160">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="30c4d-161">Tento nástroj zjistí, jaký kód je vyžadován, a potom ořízne nepoužívané knihovny.</span><span class="sxs-lookup"><span data-stu-id="30c4d-161">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="30c4d-162">Tento nástroj může výrazně snížit velikost nasazení některých aplikací.</span><span class="sxs-lookup"><span data-stu-id="30c4d-162">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="30c4d-163">Chcete-li tento nástroj `<PublishTrimmed>` povolit, přidejte nastavení do projektu a publikujte samostatnou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="30c4d-163">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="30c4d-164">Jako příklad, základní "hello world" nová konzola projekt šablony, která je zahrnuta, při publikování, hity asi 70 MB ve velikosti.</span><span class="sxs-lookup"><span data-stu-id="30c4d-164">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="30c4d-165">Pomocí `<PublishTrimmed>`, tato velikost je snížena na asi 30 MB.</span><span class="sxs-lookup"><span data-stu-id="30c4d-165">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="30c4d-166">Je důležité si uvědomit, že aplikace nebo architektury (včetně ASP.NET Core a WPF), které používají reflexe nebo související dynamické funkce, se často přeruší při oříznutí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-166">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="30c4d-167">K tomuto přerušení dochází, protože propojovací aplikace neví o toto dynamické chování a nelze určit, které typy rozhraní jsou požadovány pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="30c4d-167">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="30c4d-168">Nástroj propojovací nástroj IL lze nakonfigurovat tak, aby byl vědom tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="30c4d-168">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="30c4d-169">Především nezapomeňte aplikaci otestovat po oříznutí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-169">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="30c4d-170">Další informace o nástroji IL Linker naleznete v [dokumentaci](https://aka.ms/dotnet-illink) nebo na adrese [úložiště mono/linker.]( https://github.com/mono/linker)</span><span class="sxs-lookup"><span data-stu-id="30c4d-170">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="30c4d-171">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="30c4d-171">Tiered compilation</span></span>

<span data-ttu-id="30c4d-172">[Vrstvená kompilace](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) je ve výchozím nastavení zapnuta s rozhraním .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="30c4d-172">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="30c4d-173">Tato funkce umožňuje modulu runtime více adaptivně používat kompilátor just-in-time (JIT) k dosažení lepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-173">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="30c4d-174">Hlavní výhodou vrstvené kompilace je poskytnout dva způsoby jitting metody: v nižší kvalitě, ale rychlejší úroveň nebo vyšší kvalita, ale pomalejší úroveň.</span><span class="sxs-lookup"><span data-stu-id="30c4d-174">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="30c4d-175">Kvalita se týká toho, jak dobře je metoda optimalizována.</span><span class="sxs-lookup"><span data-stu-id="30c4d-175">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="30c4d-176">TC pomáhá zlepšit výkon aplikace při průchodu různými fázemi provádění, od spuštění až po ustálený stav.</span><span class="sxs-lookup"><span data-stu-id="30c4d-176">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="30c4d-177">Když je vrstvená kompilace zakázána, každá metoda je zkompilována jedním způsobem, který je zaujatý k výkonu ustáleného stavu oproti výkonu při spuštění.</span><span class="sxs-lookup"><span data-stu-id="30c4d-177">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="30c4d-178">Pokud je povoleno TC, následující chování platí pro kompilaci metody při spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="30c4d-178">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="30c4d-179">Pokud má metoda kód zkompilovaný předem nebo [ReadyToRun](#readytorun-images), použije se předgenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="30c4d-179">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="30c4d-180">V opačném případě je metoda jitted.</span><span class="sxs-lookup"><span data-stu-id="30c4d-180">Otherwise, the method is jitted.</span></span> <span data-ttu-id="30c4d-181">Tyto metody jsou obvykle obecné typy nad typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="30c4d-181">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="30c4d-182">*Quick JIT* vytváří kód nižší kvality (nebo méně optimalizovaný) rychleji.</span><span class="sxs-lookup"><span data-stu-id="30c4d-182">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="30c4d-183">V rozhraní .NET Core 3.0 je rychlý JIT ve výchozím nastavení povolen pro metody, které neobsahují smyčky a jsou upřednostňovány při spuštění.</span><span class="sxs-lookup"><span data-stu-id="30c4d-183">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="30c4d-184">Plně optimalizační JIT vytváří vyšší kvalitu (nebo více optimalizovaný) kód pomaleji.</span><span class="sxs-lookup"><span data-stu-id="30c4d-184">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="30c4d-185">Pro metody, kde by se quick JIT nepoužil (například pokud je metoda přiřazena ) <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>se používá plně optimalizační JIT.</span><span class="sxs-lookup"><span data-stu-id="30c4d-185">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="30c4d-186">Pro často nazývané metody kompilátor just-in-time nakonec vytvoří plně optimalizovaný kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-186">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="30c4d-187">Optimalizovaný kód pak nahradí předkompilogovaný kód pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-187">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="30c4d-188">Kód generovaný quick JIT může běžet pomaleji, přidělit více paměti nebo použít více místa zásobníku.</span><span class="sxs-lookup"><span data-stu-id="30c4d-188">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="30c4d-189">Pokud se jedná o problémy, můžete zakázat Rychlé JIT pomocí této vlastnosti MSBuild v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="30c4d-189">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="30c4d-190">Chcete-li tc zcela zakázat, použijte tuto vlastnost MSBuild v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="30c4d-190">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="30c4d-191">Pokud změníte tato nastavení v souboru projektu, bude pravděpodobně nutné provést čisté sestavení `obj` pro `bin` nové nastavení, které se projeví (odstranit a adresáře a znovu sestavit).</span><span class="sxs-lookup"><span data-stu-id="30c4d-191">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="30c4d-192">Další informace o konfiguraci kompilace za běhu naleznete v [tématu Možnosti konfigurace za běhu pro kompilaci](../run-time-config/compilation.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-192">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="30c4d-193">Obrázky ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="30c4d-193">ReadyToRun images</span></span>

<span data-ttu-id="30c4d-194">Čas spuštění aplikace .NET Core můžete zlepšit kompilací sestavení aplikací ve formátu ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="30c4d-194">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="30c4d-195">R2R je forma kompilace před časem (AOT).</span><span class="sxs-lookup"><span data-stu-id="30c4d-195">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="30c4d-196">Binární soubory R2R zlepšují výkon při spuštění tím, že snižují množství práce, kterou kompilátor za čas (JIT) potřebuje provést při načítání aplikace.</span><span class="sxs-lookup"><span data-stu-id="30c4d-196">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="30c4d-197">Binární soubory obsahují podobný nativní kód ve srovnání s tím, co by JIT vyrábět.</span><span class="sxs-lookup"><span data-stu-id="30c4d-197">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="30c4d-198">Binární soubory R2R jsou však větší, protože obsahují kód zprostředkující jazyk (IL), který je stále potřeba pro některé scénáře a nativní verze stejného kódu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-198">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="30c4d-199">R2R je k dispozici pouze při publikování samostatné aplikace, která se zaměřuje na konkrétní runtime prostředí (RID), jako je Linux x64 nebo Windows x64.</span><span class="sxs-lookup"><span data-stu-id="30c4d-199">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="30c4d-200">Chcete-li zkompilovat projekt jako ReadyToRun, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="30c4d-200">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="30c4d-201">Přidejte `<PublishReadyToRun>` nastavení do projektu:</span><span class="sxs-lookup"><span data-stu-id="30c4d-201">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="30c4d-202">Publikujte samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="30c4d-202">Publish a self-contained app.</span></span> <span data-ttu-id="30c4d-203">Tento příkaz například vytvoří samostatnou aplikaci pro 64bitovou verzi Systému Windows:</span><span class="sxs-lookup"><span data-stu-id="30c4d-203">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="30c4d-204">Omezení mezi platformami a architekturou</span><span class="sxs-lookup"><span data-stu-id="30c4d-204">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="30c4d-205">Kompilátor ReadyToRun aktuálně nepodporuje křížové cílení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-205">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="30c4d-206">Je nutné zkompilovat na daný cíl.</span><span class="sxs-lookup"><span data-stu-id="30c4d-206">You must compile on a given target.</span></span> <span data-ttu-id="30c4d-207">Například pokud chcete R2R obrazy pro Windows x64, je třeba spustit příkaz publikovat v tomto prostředí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-207">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="30c4d-208">Výjimky pro křížové cílení:</span><span class="sxs-lookup"><span data-stu-id="30c4d-208">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="30c4d-209">Windows x64 lze použít ke kompilaci bitových kopií windows ARM32, ARM64 a x86.</span><span class="sxs-lookup"><span data-stu-id="30c4d-209">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="30c4d-210">Windows x86 lze použít ke kompilaci bitových kopií Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="30c4d-210">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="30c4d-211">Linux x64 lze použít ke kompilaci linuxových obrazů ARM32 a ARM64.</span><span class="sxs-lookup"><span data-stu-id="30c4d-211">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="30c4d-212">Doba běhu/sada SDK</span><span class="sxs-lookup"><span data-stu-id="30c4d-212">Runtime/SDK</span></span>

### <a name="major-version-runtime-roll-forward"></a><span data-ttu-id="30c4d-213">Hlavní verze runtime posun vpřed</span><span class="sxs-lookup"><span data-stu-id="30c4d-213">Major-version runtime roll forward</span></span>

<span data-ttu-id="30c4d-214">.NET Core 3.0 zavádí funkci opt-in, která umožňuje vaší aplikaci posunout se dopředu na nejnovější hlavní verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30c4d-214">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="30c4d-215">Kromě toho bylo přidáno nové nastavení, které řídí, jak se v aplikaci použije posun vpřed.</span><span class="sxs-lookup"><span data-stu-id="30c4d-215">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="30c4d-216">To lze nakonfigurovat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="30c4d-216">This can be configured in the following ways:</span></span>

- <span data-ttu-id="30c4d-217">Vlastnost souboru projektu:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="30c4d-217">Project file property: `RollForward`</span></span>
- <span data-ttu-id="30c4d-218">Vlastnost konfiguračního souboru za běhu:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="30c4d-218">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="30c4d-219">Proměnná prostředí:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="30c4d-219">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="30c4d-220">Argument příkazového řádku:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="30c4d-220">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="30c4d-221">Musí být zadána jedna z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="30c4d-221">One of the following values must be specified.</span></span> <span data-ttu-id="30c4d-222">Pokud je nastavení vynecháno, je výchozí **hodnota Minor.**</span><span class="sxs-lookup"><span data-stu-id="30c4d-222">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="30c4d-223">**NejnovějšíOprava**</span><span class="sxs-lookup"><span data-stu-id="30c4d-223">**LatestPatch**</span></span>\
<span data-ttu-id="30c4d-224">Přetočte se vpřed na nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="30c4d-224">Roll forward to the highest patch version.</span></span> <span data-ttu-id="30c4d-225">Tím se zakáže dílčí verze posunout vpřed.</span><span class="sxs-lookup"><span data-stu-id="30c4d-225">This disables minor version roll forward.</span></span>
- <span data-ttu-id="30c4d-226">**Menší**</span><span class="sxs-lookup"><span data-stu-id="30c4d-226">**Minor**</span></span>\
<span data-ttu-id="30c4d-227">Převrátit na nejnižší vyšší dílčí verze, pokud je požadována dílčí verze chybí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-227">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="30c4d-228">Pokud je k dispozici požadovaná dílčí verze, použije se zásada **LatestPatch.**</span><span class="sxs-lookup"><span data-stu-id="30c4d-228">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="30c4d-229">**Hlavní**</span><span class="sxs-lookup"><span data-stu-id="30c4d-229">**Major**</span></span>\
<span data-ttu-id="30c4d-230">Převrátit na nejnižší vyšší hlavní verze a nejnižší dílčí verze, pokud je požadována hlavní verze chybí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-230">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="30c4d-231">Pokud je k dispozici požadovaná hlavní verze, použije se zásada **Vedlejší.**</span><span class="sxs-lookup"><span data-stu-id="30c4d-231">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="30c4d-232">**NejnovějšíMenší**</span><span class="sxs-lookup"><span data-stu-id="30c4d-232">**LatestMinor**</span></span>\
<span data-ttu-id="30c4d-233">Převést vpřed na nejvyšší dílčí verzi, i v případě, že je k dispozici požadovaná dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="30c4d-233">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="30c4d-234">Určeno pro scénáře hostování komponent.</span><span class="sxs-lookup"><span data-stu-id="30c4d-234">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="30c4d-235">**NejnovějšíMajor**</span><span class="sxs-lookup"><span data-stu-id="30c4d-235">**LatestMajor**</span></span>\
<span data-ttu-id="30c4d-236">Převrátit na nejvyšší hlavní a nejvyšší dílčí verze, i když je požadováno hlavní je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="30c4d-236">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="30c4d-237">Určeno pro scénáře hostování komponent.</span><span class="sxs-lookup"><span data-stu-id="30c4d-237">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="30c4d-238">**Zakázat**</span><span class="sxs-lookup"><span data-stu-id="30c4d-238">**Disable**</span></span>\
<span data-ttu-id="30c4d-239">Neotáčej se dopředu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-239">Don't roll forward.</span></span> <span data-ttu-id="30c4d-240">Spojte se pouze se zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-240">Only bind to specified version.</span></span> <span data-ttu-id="30c4d-241">Tato zásada se nedoporučuje pro obecné použití, protože zakáže možnost převést na nejnovější opravy.</span><span class="sxs-lookup"><span data-stu-id="30c4d-241">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="30c4d-242">Tato hodnota je doporučena pouze pro testování.</span><span class="sxs-lookup"><span data-stu-id="30c4d-242">This value is only recommended for testing.</span></span>

<span data-ttu-id="30c4d-243">Kromě nastavení **Zakázat** budou všechna nastavení používat nejvyšší dostupnou verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="30c4d-243">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="30c4d-244">Sestavení závislostí kopií</span><span class="sxs-lookup"><span data-stu-id="30c4d-244">Build copies dependencies</span></span>

<span data-ttu-id="30c4d-245">Příkaz `dotnet build` nyní zkopíruje závislosti NuGet pro vaši aplikaci z mezipaměti NuGet do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-245">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="30c4d-246">Dříve byly závislosti zkopírovány `dotnet publish`pouze jako součást .</span><span class="sxs-lookup"><span data-stu-id="30c4d-246">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="30c4d-247">Existují některé operace, jako je propojení a publikování holicí strojek stránky, které budou stále vyžadovat publikování.</span><span class="sxs-lookup"><span data-stu-id="30c4d-247">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="30c4d-248">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="30c4d-248">Local tools</span></span>

<span data-ttu-id="30c4d-249">.NET Core 3.0 zavádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="30c4d-249">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="30c4d-250">Místní nástroje jsou podobné [globálním nástrojům,](../tools/global-tools.md) ale jsou přidruženy k určitému umístění na disku.</span><span class="sxs-lookup"><span data-stu-id="30c4d-250">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="30c4d-251">Místní nástroje nejsou k dispozici globálně a jsou distribuovány jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="30c4d-251">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="30c4d-252">Pokud jste vyzkoušeli místní nástroje v rozhraní .NET `dotnet tool restore` Core `dotnet tool install`3.0 Preview 1, například spuštění nebo , odstraňte složku mezipaměti místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="30c4d-252">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="30c4d-253">V opačném případě místní nástroje nebudou fungovat na žádné novější verzi.</span><span class="sxs-lookup"><span data-stu-id="30c4d-253">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="30c4d-254">Tato složka je umístěna na adrese:</span><span class="sxs-lookup"><span data-stu-id="30c4d-254">This folder is located at:</span></span>
>
> <span data-ttu-id="30c4d-255">Na macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="30c4d-255">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="30c4d-256">Ve Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="30c4d-256">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="30c4d-257">Místní nástroje spoléhají na `dotnet-tools.json` název souboru manifestu v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="30c4d-257">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="30c4d-258">Tento soubor manifestu definuje nástroje, které mají být k dispozici v této složce a níže.</span><span class="sxs-lookup"><span data-stu-id="30c4d-258">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="30c4d-259">Soubor manifestu můžete distribuovat s kódem, abyste zajistili, že každý, kdo pracuje s vaším kódem, může obnovit a používat stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="30c4d-259">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="30c4d-260">Pro globální i místní nástroje je vyžadována kompatibilní verze runtime.</span><span class="sxs-lookup"><span data-stu-id="30c4d-260">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="30c4d-261">Mnoho nástrojů aktuálně na NuGet.org cíl .NET Core Runtime 2.1.</span><span class="sxs-lookup"><span data-stu-id="30c4d-261">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="30c4d-262">Chcete-li nainstalovat tyto nástroje globálně nebo místně, budete stále muset nainstalovat [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="30c4d-262">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="new-globaljson-options"></a><span data-ttu-id="30c4d-263">Nové možnosti global.json</span><span class="sxs-lookup"><span data-stu-id="30c4d-263">New global.json options</span></span>

<span data-ttu-id="30c4d-264">Soubor *global.json* obsahuje nové možnosti, které poskytují větší flexibilitu při pokusu o definování, která verze sady .NET Core SDK se používá.</span><span class="sxs-lookup"><span data-stu-id="30c4d-264">The *global.json* file has new options that provide more flexibility when you're trying to define which version of the .NET Core SDK is used.</span></span> <span data-ttu-id="30c4d-265">Nové možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="30c4d-265">The new options are:</span></span>

- <span data-ttu-id="30c4d-266">`allowPrerelease`: Označuje, zda by měl překladač sady SDK zvážit předběžné verze při výběru verze sady SDK, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="30c4d-266">`allowPrerelease`: Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>
- <span data-ttu-id="30c4d-267">`rollForward`: Označuje zásady pro předávání vpřed, které se mají použít při výběru verze sady SDK, buď jako záložní, pokud chybí konkrétní verze sady SDK, nebo jako direktivu pro použití vyšší verze.</span><span class="sxs-lookup"><span data-stu-id="30c4d-267">`rollForward`: Indicates the roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span>

<span data-ttu-id="30c4d-268">Další informace o změnách včetně výchozích hodnot, podporovaných hodnot a nových pravidel párování naleznete v [přehledu global.json](../tools/global-json.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-268">For more information about the changes including default values, supported values, and new matching rules, see [global.json overview](../tools/global-json.md).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="30c4d-269">Menší velikosti haldy uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="30c4d-269">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="30c4d-270">Výchozí velikost haldy systému uvolňování paměti byla snížena, což vedlo k tomu, že jádro .NET core používá méně paměti.</span><span class="sxs-lookup"><span data-stu-id="30c4d-270">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="30c4d-271">Tato změna lépe zarovná s rozpočtem přidělení generace 0 s moderními velikostmi mezipaměti procesoru.</span><span class="sxs-lookup"><span data-stu-id="30c4d-271">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="30c4d-272">Podpora velké stránky uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="30c4d-272">Garbage Collection Large Page support</span></span>

<span data-ttu-id="30c4d-273">Velké stránky (označované také jako Obrovské stránky v Linuxu) je funkce, kde je operační systém schopen vytvořit oblasti paměti větší než nativní velikost stránky (často 4K) pro zlepšení výkonu aplikace požadující tyto velké stránky.</span><span class="sxs-lookup"><span data-stu-id="30c4d-273">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="30c4d-274">Systém uvolňování paměti lze nyní nakonfigurovat s nastavením **GCLargePages** jako funkci přihlášení, kterou chcete přidělit velké stránky v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="30c4d-274">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="30c4d-275">& plochy systému Windows COM</span><span class="sxs-lookup"><span data-stu-id="30c4d-275">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="30c4d-276">Instalační služba sady Windows core s rozhraním .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="30c4d-276">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="30c4d-277">Instalační služba MSI pro systém Windows se změnila počínaje rozhraním .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="30c4d-277">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="30c4d-278">Instalační programy sady SDK nyní inovují verze funkce sady SDK na místě.</span><span class="sxs-lookup"><span data-stu-id="30c4d-278">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="30c4d-279">Pásma funkcí jsou definována ve *stovkách* skupin v části *opravy* čísla verze.</span><span class="sxs-lookup"><span data-stu-id="30c4d-279">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="30c4d-280">Například \*\*3.0._ 101_ \*\* a \*\*3.0._ 201_ \*\* jsou verze ve dvou různých pásmech funkcí, zatímco \*\*3.0._ 101_ \*\* a \*\*3.0._ 199_ \*\* jsou ve stejném souboru funkcí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-280">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="30c4d-281">A když .NET Core SDK \*\*3.0._ Je_ \*\* nainstalována sada 101, sada .NET Core SDK \*\*3.0._ 100_ \*\* bude odebráno ze stroje, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="30c4d-281">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="30c4d-282">Když .NET Core SDK \*\*3.0._ 200_ \*\* je nainstalován ve stejném počítači, .NET Core SDK \*\*3.0._ 101_ \*\* nebude odstraněn.</span><span class="sxs-lookup"><span data-stu-id="30c4d-282">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="30c4d-283">Další informace o správu verzí naleznete v [tématu Přehled verzí jádra .NET](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-283">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="30c4d-284">Plocha Windows</span><span class="sxs-lookup"><span data-stu-id="30c4d-284">Windows desktop</span></span>

<span data-ttu-id="30c4d-285">Rozhraní .NET Core 3.0 podporuje desktopové aplikace systému Windows pomocí zařízení Windows Presentation Foundation (WPF) a Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="30c4d-285">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="30c4d-286">Tyto architektury také podporují použití moderních ovládacích prvků a plynulého stylu z knihovny Windows UI XAML Library (WinUI) přes [ostrovy XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="30c4d-286">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="30c4d-287">Součást Plochy systému Windows je součástí sady Windows .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="30c4d-287">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="30c4d-288">Můžete vytvořit novou aplikaci WPF nebo `dotnet` Windows Forms s následujícími příkazy:</span><span class="sxs-lookup"><span data-stu-id="30c4d-288">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="30c4d-289">Visual Studio 2019 přidává nové šablony **projectu** pro .NET Core 3.0 Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="30c4d-289">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="30c4d-290">Další informace o tom, jak přenést existující aplikaci rozhraní .NET Framework, naleznete [v tématu Port WPF projekty](../../desktop-wpf/migration/convert-project-from-net-framework.md) a [port windows forms projekty](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-290">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="30c4d-291">WinForms vysoké DPI</span><span class="sxs-lookup"><span data-stu-id="30c4d-291">WinForms high DPI</span></span>

<span data-ttu-id="30c4d-292">Aplikace .NET Core Windows Forms mohou <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>nastavit režim vysokého dpi s aplikací .</span><span class="sxs-lookup"><span data-stu-id="30c4d-292">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="30c4d-293">Metoda `SetHighDpiMode` nastaví odpovídající režim vysokého DPI, pokud nastavení `App.Manifest` nebylo nastaveno `Application.Run`jinými prostředky, jako je P/Invoke před .</span><span class="sxs-lookup"><span data-stu-id="30c4d-293">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="30c4d-294">Možné `highDpiMode` hodnoty vyjádřené výčtem <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> jsou:</span><span class="sxs-lookup"><span data-stu-id="30c4d-294">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="30c4d-295">Další informace o režimech vysoké hodu DPI naleznete v tématu [Vývoj aplikací pro stolní počítače s vysokým obsahem DPI v systému Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="30c4d-295">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="30c4d-296">Vytvoření komponent modelu COM</span><span class="sxs-lookup"><span data-stu-id="30c4d-296">Create COM components</span></span>

<span data-ttu-id="30c4d-297">V systému Windows nyní můžete vytvářet spravované součásti com callable.</span><span class="sxs-lookup"><span data-stu-id="30c4d-297">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="30c4d-298">Tato funkce je důležité použít .NET Core s com add-in modely a také poskytnout paritu s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30c4d-298">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="30c4d-299">Na rozdíl od rozhraní .NET Framework, kde byl jako server COM použit soubor *mscoree.dll,* přidá rozhraní .NET Core při vytváření komponenty modelu COM do adresáře *bin* nativní spouštěč.</span><span class="sxs-lookup"><span data-stu-id="30c4d-299">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="30c4d-300">Příklad, jak vytvořit komponentu modelu COM a její využití, naleznete v [tématu Com Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="30c4d-300">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="30c4d-301">Nativní interop systému Windows</span><span class="sxs-lookup"><span data-stu-id="30c4d-301">Windows Native Interop</span></span>

<span data-ttu-id="30c4d-302">Systém Windows nabízí bohaté nativní rozhraní API ve formě plochých rozhraní API C, COM a WinRT.</span><span class="sxs-lookup"><span data-stu-id="30c4d-302">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="30c4d-303">Zatímco rozhraní .NET Core podporuje **P/Invoke**, rozhraní .NET Core 3.0 přidává možnost **vytváření rozhraní API COM** a aktivace rozhraní API **WinRT**.</span><span class="sxs-lookup"><span data-stu-id="30c4d-303">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="30c4d-304">Příklad kódu najdete v [tématu Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="30c4d-304">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="30c4d-305">Nasazení MSIX</span><span class="sxs-lookup"><span data-stu-id="30c4d-305">MSIX Deployment</span></span>

<span data-ttu-id="30c4d-306">[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikací systému Windows.</span><span class="sxs-lookup"><span data-stu-id="30c4d-306">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="30c4d-307">Lze jej použít k nasazení desktopových aplikací .NET Core 3.0 do systému Windows 10.</span><span class="sxs-lookup"><span data-stu-id="30c4d-307">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="30c4d-308">[Projekt balení aplikací systému Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), který je k dispozici v sadě Visual Studio 2019, umožňuje vytvářet balíčky MSIX s [samostatnými](../deploying/index.md#publish-self-contained) aplikacemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30c4d-308">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#publish-self-contained) .NET Core applications.</span></span>

<span data-ttu-id="30c4d-309">Soubor projektu .NET Core musí ve vlastnosti zadat podporované moduly `<RuntimeIdentifiers>` runtimes:</span><span class="sxs-lookup"><span data-stu-id="30c4d-309">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="30c4d-310">Vylepšení Linuxu</span><span class="sxs-lookup"><span data-stu-id="30c4d-310">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="30c4d-311">SerialPort pro Linux</span><span class="sxs-lookup"><span data-stu-id="30c4d-311">SerialPort for Linux</span></span>

<span data-ttu-id="30c4d-312">.NET Core 3.0 poskytuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> základní podporu pro linux.</span><span class="sxs-lookup"><span data-stu-id="30c4d-312">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="30c4d-313">Dříve rozhraní .NET Core `SerialPort` podporovalo pouze použití v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="30c4d-313">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="30c4d-314">Další informace o omezené podpoře sériového portu v Linuxu naleznete v tématu [Problém GitHubu #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="30c4d-314">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="30c4d-315">Omezení paměti Dockeru a skupiny</span><span class="sxs-lookup"><span data-stu-id="30c4d-315">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="30c4d-316">Spuštění rozhraní .NET Core 3.0 na Linuxu s Dockerem funguje lépe s limity paměti cgroup.</span><span class="sxs-lookup"><span data-stu-id="30c4d-316">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="30c4d-317">Spuštění kontejneru Dockeru s omezeními paměti, například s `docker run -m`, změní způsob, jakým se chová .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30c4d-317">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="30c4d-318">Výchozí velikost haldy uvolňování paměti :maximum 20 MB nebo 75 % limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="30c4d-318">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="30c4d-319">Explicitní velikost lze nastavit jako absolutní číslo nebo procento limitu skupiny cgroup.</span><span class="sxs-lookup"><span data-stu-id="30c4d-319">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="30c4d-320">Minimální velikost rezervovaného segmentu na haldu GC je 16 MB.</span><span class="sxs-lookup"><span data-stu-id="30c4d-320">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="30c4d-321">Tato velikost snižuje počet hromady, které jsou vytvořeny na počítačích.</span><span class="sxs-lookup"><span data-stu-id="30c4d-321">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="30c4d-322">Podpora GPIO pro Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="30c4d-322">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="30c4d-323">Dva balíčky byly vydány na NuGet, které můžete použít pro programování GPIO:</span><span class="sxs-lookup"><span data-stu-id="30c4d-323">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="30c4d-324">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="30c4d-324">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="30c4d-325">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="30c4d-325">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="30c4d-326">Balíčky GPIO obsahují api pro zařízení *GPIO*, *SPI*, *I2C*a *PWM.*</span><span class="sxs-lookup"><span data-stu-id="30c4d-326">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="30c4d-327">Balíček IoT vazby obsahuje vazby zařízení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-327">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="30c4d-328">Další informace najdete v [tématu zařízení GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="30c4d-328">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="30c4d-329">Podpora pro ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="30c4d-329">ARM64 Linux support</span></span>

<span data-ttu-id="30c4d-330">.NET Core 3.0 přidává podporu pro ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="30c4d-330">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="30c4d-331">Primární případ použití pro ARM64 je aktuálně se scénáři IoT.</span><span class="sxs-lookup"><span data-stu-id="30c4d-331">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="30c4d-332">Další informace naleznete [v tématu .NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="30c4d-332">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="30c4d-333">[Obrázky Dockeru pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-333">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="30c4d-334">**ARM64** Podpora systému Windows ještě není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="30c4d-334">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="30c4d-335">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30c4d-335">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="30c4d-336">TLS 1.3 & OpenSSL 1.1.1 na Linuxu</span><span class="sxs-lookup"><span data-stu-id="30c4d-336">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="30c4d-337">.NET Core nyní využívá [podporu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), když je k dispozici v daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="30c4d-337">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="30c4d-338">S TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="30c4d-338">With TLS 1.3:</span></span>

- <span data-ttu-id="30c4d-339">Doba připojení je vylepšena snížením počtu zpátečních cest mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="30c4d-339">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="30c4d-340">Vylepšené zabezpečení z důvodu odebrání různých zastaralých a nezabezpečených kryptografických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="30c4d-340">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="30c4d-341">Pokud je k dispozici, .NET Core 3.0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**nebo **OpenSSL 1.0.2** v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="30c4d-341">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="30c4d-342">Pokud je k dispozici **OpenSSL 1.1.1,** budou <xref:System.Net.Security.SslStream?displayProperty=nameWithType> oba i <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> typy používat **TLS 1.3** (za předpokladu, že klient i server podporují **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="30c4d-342">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30c4d-343">Windows a macOS zatím nepodporují **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="30c4d-343">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="30c4d-344">.NET Core 3.0 bude podporovat **TLS 1.3** v těchto operačních systémech, jakmile bude podpora k dispozici.</span><span class="sxs-lookup"><span data-stu-id="30c4d-344">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="30c4d-345">Následující příklad C# 8.0 ukazuje .NET Core 3.0 na Ubuntu <https://www.cloudflare.com>18.10 připojení k :</span><span class="sxs-lookup"><span data-stu-id="30c4d-345">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="30c4d-346">Kryptografické šifry</span><span class="sxs-lookup"><span data-stu-id="30c4d-346">Cryptography ciphers</span></span>

<span data-ttu-id="30c4d-347">.NET 3.0 přidává podporu pro šifry **AES-GCM** a <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> **AES-CCM,** implementované s a <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> příslušně.</span><span class="sxs-lookup"><span data-stu-id="30c4d-347">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="30c4d-348">Tyto algoritmy jsou oba [ověřené šifrování s algoritmy AEAD (Association Data).](https://en.wikipedia.org/wiki/Authenticated_encryption)</span><span class="sxs-lookup"><span data-stu-id="30c4d-348">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="30c4d-349">Následující kód ukazuje `AesGcm` použití šifry k šifrování a dešifrování náhodných dat.</span><span class="sxs-lookup"><span data-stu-id="30c4d-349">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="30c4d-350">Import a export kryptografického klíče</span><span class="sxs-lookup"><span data-stu-id="30c4d-350">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="30c4d-351">.NET Core 3.0 podporuje import a export asymetrických veřejných a soukromých klíčů ze standardních formátů.</span><span class="sxs-lookup"><span data-stu-id="30c4d-351">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="30c4d-352">Není nutné používat certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="30c4d-352">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="30c4d-353">Všechny typy klíčů, například *RSA*, *DSA*, *ECDsa*a *ECDiffieHellman*, podporují následující formáty:</span><span class="sxs-lookup"><span data-stu-id="30c4d-353">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="30c4d-354">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="30c4d-354">**Public Key**</span></span>
  - <span data-ttu-id="30c4d-355">X.509 PředmětPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="30c4d-355">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="30c4d-356">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="30c4d-356">**Private key**</span></span>
  - <span data-ttu-id="30c4d-357">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="30c4d-357">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="30c4d-358">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="30c4d-358">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="30c4d-359">RsA klíče také podporují:</span><span class="sxs-lookup"><span data-stu-id="30c4d-359">RSA keys also support:</span></span>

- <span data-ttu-id="30c4d-360">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="30c4d-360">**Public Key**</span></span>
  - <span data-ttu-id="30c4d-361">PKCS# 1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="30c4d-361">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="30c4d-362">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="30c4d-362">**Private key**</span></span>
  - <span data-ttu-id="30c4d-363">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="30c4d-363">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="30c4d-364">Metody exportu vytvářejí binární data kódovaná der a metody importu očekávají totéž.</span><span class="sxs-lookup"><span data-stu-id="30c4d-364">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="30c4d-365">Pokud je klíč uložen ve formátu PEM vhodnépro text, volající bude muset base64 dekódovat obsah před voláním metody importu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-365">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="30c4d-366">**PKCS # 8** soubory mohou <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> být kontrolovány s a **PFX / PKCS # 12** soubory mohou být kontrolovány s <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30c4d-366">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="30c4d-367">**PFX/PKCS#12** soubory lze manipulovat <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>s .</span><span class="sxs-lookup"><span data-stu-id="30c4d-367">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="30c4d-368">Změny rozhraní API rozhraní .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="30c4d-368">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="30c4d-369">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="30c4d-369">Ranges and indices</span></span>

<span data-ttu-id="30c4d-370">Nový <xref:System.Index?displayProperty=nameWithType> typ lze použít pro indexování.</span><span class="sxs-lookup"><span data-stu-id="30c4d-370">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="30c4d-371">Můžete vytvořit jeden `int` z, který se počítá od `^` začátku, nebo s prefix operátor (C#), který se počítá od konce:</span><span class="sxs-lookup"><span data-stu-id="30c4d-371">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="30c4d-372">K dispozici je <xref:System.Range?displayProperty=nameWithType> také typ, který `Index` se skládá ze dvou hodnot, jeden pro začátek `x..y` a jeden pro konec a může být zapsán s výrazem rozsahu (C#).</span><span class="sxs-lookup"><span data-stu-id="30c4d-372">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="30c4d-373">Poté můžete indexovat `Range`pomocí , který vytvoří řez:</span><span class="sxs-lookup"><span data-stu-id="30c4d-373">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="30c4d-374">Další informace naleznete v [kurzu rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-374">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="30c4d-375">Asynchronní streamy</span><span class="sxs-lookup"><span data-stu-id="30c4d-375">Async streams</span></span>

<span data-ttu-id="30c4d-376">Typ <xref:System.Collections.Generic.IAsyncEnumerable%601> je nová asynchronní verze <xref:System.Collections.Generic.IEnumerable%601>aplikace .</span><span class="sxs-lookup"><span data-stu-id="30c4d-376">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="30c4d-377">Jazyk umožňuje `await foreach` přejít `IAsyncEnumerable<T>` ke konzumaci jejich `yield return` prvky a použít k nim k výrobě prvků.</span><span class="sxs-lookup"><span data-stu-id="30c4d-377">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="30c4d-378">Následující příklad ukazuje jak výrobu, tak spotřebu asynchronních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="30c4d-378">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="30c4d-379">Příkaz `foreach` je asynchronní `yield return` a sám používá k vytvoření asynchronního datového proudu pro volající.</span><span class="sxs-lookup"><span data-stu-id="30c4d-379">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="30c4d-380">Tento vzor `yield return`(pomocí) je doporučený model pro výrobu asynchronních proudů.</span><span class="sxs-lookup"><span data-stu-id="30c4d-380">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="30c4d-381">Kromě toho, že `await foreach`je možné , můžete také vytvořit asynchronní iterátory, například iterátor, který `IAsyncEnumerable/IAsyncEnumerator` vrací, že můžete i `await` `yield` in.</span><span class="sxs-lookup"><span data-stu-id="30c4d-381">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="30c4d-382">Pro objekty, které je třeba `IAsyncDisposable`vyřadit, můžete použít `Stream` , `Timer`které různé typy BCL implementovat, například a .</span><span class="sxs-lookup"><span data-stu-id="30c4d-382">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="30c4d-383">Další informace naleznete [v kurzu asynchronních datových proudů](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-383">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="30c4d-384">IEEE Plovoucí bod</span><span class="sxs-lookup"><span data-stu-id="30c4d-384">IEEE Floating-point</span></span>

<span data-ttu-id="30c4d-385">Plovoucí desetinná místa API jsou aktualizovány tak, aby v souladu s [IEEE 754-2008 revize](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="30c4d-385">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="30c4d-386">Cílem těchto změn je vystavit všechny **požadované** operace a zajistit, že jsou behaviorálně kompatibilní se specifikací IEEE. Další informace o vylepšeních s plovoucí desetinnou desetinnou desetinnou desetinnou tázání najdete v tématu Vylepšení analýzy plovoucí desetinné a formátování v příspěvku blogu [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)</span><span class="sxs-lookup"><span data-stu-id="30c4d-386">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="30c4d-387">Mezi opravy analýzy a formátování patří:</span><span class="sxs-lookup"><span data-stu-id="30c4d-387">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="30c4d-388">Správně analyzovat a zaoblené vstupy libovolné délky.</span><span class="sxs-lookup"><span data-stu-id="30c4d-388">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="30c4d-389">Správně analyzovat a formátovat záporné nuly.</span><span class="sxs-lookup"><span data-stu-id="30c4d-389">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="30c4d-390">Správně analyzovat `Infinity` `NaN` a provedením kontroly rozlišování velkých `+` a malých písmen a povolení volitelné předcházející, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="30c4d-390">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="30c4d-391">Mezi <xref:System.Math?displayProperty=nameWithType> nová api patří:</span><span class="sxs-lookup"><span data-stu-id="30c4d-391">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="30c4d-392"><xref:System.Math.BitIncrement(System.Double)>A<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="30c4d-392"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="30c4d-393">Odpovídá operacím `nextUp` `nextDown` i IEEE.</span><span class="sxs-lookup"><span data-stu-id="30c4d-393">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="30c4d-394">Vrátí nejmenší číslo s plovoucí desetinnou desetinnou desetinnou, která porovnává větší nebo menší než vstup (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="30c4d-394">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="30c4d-395">Například `Math.BitIncrement(0.0)` vrátí `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="30c4d-395">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="30c4d-396"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>A<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="30c4d-396"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="30c4d-397">Odpovídá `maxNumMag` a `minNumMag` IEEE operace, vrátí hodnotu, která je větší nebo menší velikost dvou vstupů (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="30c4d-397">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="30c4d-398">Například `Math.MaxMagnitude(2.0, -3.0)` vrátí `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="30c4d-398">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="30c4d-399">Odpovídá operaci `logB` IEEE, která vrací integrální hodnotu, vrátí integrální base-2 protokolu vstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="30c4d-399">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="30c4d-400">Tato metoda je skutečně `floor(log2(x))`stejná jako , ale provádí se s minimální chybou zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-400">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="30c4d-401">Odpovídá operaci `scaleB` IEEE, která přebírá integrální `x * pow(2, n)`hodnotu, vrátí efektivně , ale provádí se s minimální chybou zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-401">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="30c4d-402">Odpovídá operaci `log2` IEEE, vrátí logaritmus base-2.</span><span class="sxs-lookup"><span data-stu-id="30c4d-402">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="30c4d-403">Minimalizuje chybu zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-403">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="30c4d-404">Odpovídá operaci `fma` IEEE, provede tavené násobení přidat.</span><span class="sxs-lookup"><span data-stu-id="30c4d-404">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="30c4d-405">To znamená, `(x * y) + z` že provádí jako jednu operaci, čímž minimalizuje chybu zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-405">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="30c4d-406">Příkladem je `FusedMultiplyAdd(1e308, 2.0, -1e308)`, `1e308`který vrátí .</span><span class="sxs-lookup"><span data-stu-id="30c4d-406">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="30c4d-407">Pravidelné `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="30c4d-407">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="30c4d-408">Odpovídá operaci `copySign` IEEE, vrátí hodnotu `x`, ale se `y`znaménkem .</span><span class="sxs-lookup"><span data-stu-id="30c4d-408">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="30c4d-409">Vnitřní objekty závislé na platformě .NET</span><span class="sxs-lookup"><span data-stu-id="30c4d-409">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="30c4d-410">Byla přidána api, která umožňují přístup k určitým pokynům procesoru orientovaným na perf, jako jsou **například instrukční** sady **SIMD** nebo Bit Manipulation.</span><span class="sxs-lookup"><span data-stu-id="30c4d-410">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="30c4d-411">Tyto pokyny mohou pomoci dosáhnout významné zlepšení výkonu v určitých scénářích, jako je například zpracování dat efektivně paralelně.</span><span class="sxs-lookup"><span data-stu-id="30c4d-411">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="30c4d-412">V případě potřeby začaly knihovny .NET používat tyto pokyny ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="30c4d-412">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="30c4d-413">Další informace naleznete v tématu [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-413">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="30c4d-414">Vylepšená rozhraní API základní verze rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="30c4d-414">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="30c4d-415">Počínaje rozhraním .NET Core 3.0 nyní rozhraní API verze s rozhraním .NET Core vrátí informace, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="30c4d-415">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="30c4d-416">Například:</span><span class="sxs-lookup"><span data-stu-id="30c4d-416">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="30c4d-417">Prolomení změn.</span><span class="sxs-lookup"><span data-stu-id="30c4d-417">Breaking change.</span></span> <span data-ttu-id="30c4d-418">Toto je technicky narušující změna, protože schéma správy verzí se změnilo.</span><span class="sxs-lookup"><span data-stu-id="30c4d-418">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="30c4d-419">Rychlá integrovaná podpora JSON</span><span class="sxs-lookup"><span data-stu-id="30c4d-419">Fast built-in JSON support</span></span>

<span data-ttu-id="30c4d-420">Uživatelé .NET se do značné míry spoléhali na [Newtonsoft.Json](https://www.newtonsoft.com/json) a další populární knihovny JSON, které jsou i nadále dobrou volbou.</span><span class="sxs-lookup"><span data-stu-id="30c4d-420">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="30c4d-421">`Newtonsoft.Json`používá řetězce .NET jako svůj základní datový typ, který je UTF-16 pod kapotou.</span><span class="sxs-lookup"><span data-stu-id="30c4d-421">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="30c4d-422">Nová integrovaná podpora JSON je vysoce výkonná, s nízkou alokací a pracuje s textem JSON kódovánu UTF-8.</span><span class="sxs-lookup"><span data-stu-id="30c4d-422">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="30c4d-423">Další informace o <xref:System.Text.Json> oboru názvů a typech naleznete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="30c4d-423">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="30c4d-424">Serializace JSON v rozhraní .NET - přehled</span><span class="sxs-lookup"><span data-stu-id="30c4d-424">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="30c4d-425">[Serializace a deserializace zařízení JSON v rozhraní .NET](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="30c4d-425">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="30c4d-426">Jak migrovat z Newtonsoft.Json na System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="30c4d-426">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="30c4d-427">Podpora HTTP/2</span><span class="sxs-lookup"><span data-stu-id="30c4d-427">HTTP/2 support</span></span>

<span data-ttu-id="30c4d-428">Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> podporuje protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="30c4d-428">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="30c4d-429">Pokud je povolenprotokol HTTP/2, je verze protokolu HTTP vyjednána prostřednictvím protokolu TLS/ALPN a protokol HTTP/2 se používá, pokud se server rozhodne ji použít.</span><span class="sxs-lookup"><span data-stu-id="30c4d-429">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="30c4d-430">Výchozí protokol zůstává HTTP/1.1, ale HTTP/2 lze povolit dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="30c4d-430">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="30c4d-431">Nejprve můžete nastavit zprávu požadavku HTTP tak, aby používala protokol HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="30c4d-431">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="30c4d-432">Za druhé, <xref:System.Net.Http.HttpClient> můžete změnit použít HTTP/2 ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="30c4d-432">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="30c4d-433">Mnohokrát při vývoji aplikace, chcete použít nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="30c4d-433">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="30c4d-434">Pokud víte, že cílový koncový bod bude používat protokol HTTP/2, můžete zapnout nešifrovaná připojení pro protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="30c4d-434">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="30c4d-435">Můžete ji zapnout nastavením `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` proměnné `1` prostředí na nebo povolením v kontextu aplikace:</span><span class="sxs-lookup"><span data-stu-id="30c4d-435">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="30c4d-436">Další kroky</span><span class="sxs-lookup"><span data-stu-id="30c4d-436">Next steps</span></span>

- [<span data-ttu-id="30c4d-437">Zkontrolujte narušující změny mezi .NET Core 2.2 a 3.0.</span><span class="sxs-lookup"><span data-stu-id="30c4d-437">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="30c4d-438">Projděte si nejnovější změny v rozhraní .NET Core 3.0 pro aplikace pro Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="30c4d-438">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)
