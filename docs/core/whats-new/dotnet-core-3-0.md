---
title: Co je nového v .NET Core 3.0
description: Přečtěte si o nových funkcích, které najdete v .NET Core 3,0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 06/14/2019
ms.openlocfilehash: b1dd243d754bfc3b682c084820547f6b7846f0ea
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484663"
---
# <a name="whats-new-in-net-core-30-preview-6"></a><span data-ttu-id="3edee-103">Co je nového v .NET Core 3,0 (Preview 6)</span><span class="sxs-lookup"><span data-stu-id="3edee-103">What's new in .NET Core 3.0 (Preview 6)</span></span>

<span data-ttu-id="3edee-104">Tento článek popisuje, co je v .NET Core 3,0 (v Preview 6) novinkou.</span><span class="sxs-lookup"><span data-stu-id="3edee-104">This article describes what is new in .NET Core 3.0 (through preview 6).</span></span> <span data-ttu-id="3edee-105">Jedním z největších vylepšení je podpora desktopových aplikací pro Windows (jenom Windows).</span><span class="sxs-lookup"><span data-stu-id="3edee-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="3edee-106">Pomocí aplikace .NET Core 3,0 SDK desktopové plochy systému Windows můžete přenést model Windows Forms aplikace a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3edee-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="3edee-107">Aby bylo jasné, že je komponenta Desktop systému Windows podporována a je součástí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3edee-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="3edee-108">Další informace najdete v části [Windows Desktop](#windows-desktop) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="3edee-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="3edee-109">.NET Core 3,0 přidává podporu pro C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="3edee-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="3edee-110">Důrazně doporučujeme použít [nejnovější verzi sady Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview)nebo Visual Studio Code s rozšířením OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="3edee-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="3edee-111">[Stáhněte si a začněte používat .NET Core 3,0 Preview 6](https://aka.ms/netcore3download) hned teď v systémech Windows, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="3edee-111">[Download and get started with .NET Core 3.0 Preview 6](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="3edee-112">Další informace o jednotlivých vydaných verzích Preview najdete v následujících oznámeních:</span><span class="sxs-lookup"><span data-stu-id="3edee-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="3edee-113">Oznámení .NET Core 3,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="3edee-113">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="3edee-114">Oznámení .NET Core 3,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="3edee-114">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="3edee-115">Oznámení .NET Core 3,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="3edee-115">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="3edee-116">Oznámení .NET Core 3,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="3edee-116">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="3edee-117">Oznámení .NET Core 3,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="3edee-117">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="3edee-118">Oznámení .NET Core 3,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="3edee-118">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="3edee-119">.NET Core SDK Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="3edee-119">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="3edee-120">Instalační program MSI pro Windows se od verze .NET Core 3,0 změnil.</span><span class="sxs-lookup"><span data-stu-id="3edee-120">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="3edee-121">Instalační programy sady SDK teď upgradují verze sady SDK, které jsou na místě.</span><span class="sxs-lookup"><span data-stu-id="3edee-121">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="3edee-122">Pásma funkcí jsou definována ve *stovkách* v oddílu *patch* tohoto čísla verze.</span><span class="sxs-lookup"><span data-stu-id="3edee-122">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="3edee-123">Například **3,0. _101_**  a **3,0. _201_**  jsou verze ve dvou různých pruzích funkcí během **3,0. _101_**  a **3,0. _199_**  jsou ve stejném pásmu funkcí.</span><span class="sxs-lookup"><span data-stu-id="3edee-123">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="3edee-124">A při .NET Core SDK **3,0. _101_**  je nainstalováno, .NET Core SDK **3,0. _100_**  se odebere z počítače, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="3edee-124">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="3edee-125">Při .NET Core SDK **3,0. _200_**  je nainstalována na stejném počítači .NET Core SDK **3,0. _101_**  nebude odebráno.</span><span class="sxs-lookup"><span data-stu-id="3edee-125">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="3edee-126">Další informace o tom, jak se správou verzí, najdete v tématu Přehled toho, [jak je verze .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="3edee-126">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="3edee-127">C#8,0 Preview</span><span class="sxs-lookup"><span data-stu-id="3edee-127">C# 8.0 preview</span></span>

<span data-ttu-id="3edee-128">.NET Core 3,0 podporuje C# 8 Preview.</span><span class="sxs-lookup"><span data-stu-id="3edee-128">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="3edee-129">Další informace o C# funkcích 8,0 najdete v tématu [co je nového v C# 8,0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="3edee-129">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="3edee-130">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="3edee-130">.NET Standard 2.1</span></span>

<span data-ttu-id="3edee-131">I když .NET Core 3,0 podporuje **.NET Standard 2,1**, výchozí `dotnet new classlib` šablona vygeneruje projekt, který cílí na **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="3edee-131">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="3edee-132">Chcete-li cílit na **.NET Standard 2,1**, upravte soubor projektu a `TargetFramework` změňte vlastnost `netstandard2.1`na:</span><span class="sxs-lookup"><span data-stu-id="3edee-132">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="3edee-133">Pokud používáte Visual Studio, budete potřebovat [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), protože Visual Studio 2017 nepodporuje **.NET Standard 2,1** nebo **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="3edee-133">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="3edee-134">Vylepšená rozhraní API verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="3edee-134">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="3edee-135">Počínaje rozhraním .NET Core 3,0 verze rozhraní API poskytovaná pomocí .NET Core nyní vrátí očekávané informace.</span><span class="sxs-lookup"><span data-stu-id="3edee-135">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="3edee-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3edee-136">For example:</span></span>

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
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="3edee-137">Zásadní změna.</span><span class="sxs-lookup"><span data-stu-id="3edee-137">Breaking change.</span></span> <span data-ttu-id="3edee-138">To je technicky zásadní změna, protože se změnilo schéma správy verzí.</span><span class="sxs-lookup"><span data-stu-id="3edee-138">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="3edee-139">Vnitřní objekty závislé na platformě .NET</span><span class="sxs-lookup"><span data-stu-id="3edee-139">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="3edee-140">Byla přidána rozhraní API, která umožňují přístup k určitým pokynům pro procesor orientovaným na výkon, jako jsou **SIMD** nebo sady instrukcí pro **manipulaci** .</span><span class="sxs-lookup"><span data-stu-id="3edee-140">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="3edee-141">Tyto pokyny vám pomůžou dosáhnout výrazného zlepšení výkonu v některých scénářích, jako je efektivní zpracování dat paralelně.</span><span class="sxs-lookup"><span data-stu-id="3edee-141">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="3edee-142">V případě potřeby se pomocí těchto pokynů Vylepšete knihovny .NET, aby se zlepšil výkon.</span><span class="sxs-lookup"><span data-stu-id="3edee-142">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="3edee-143">Další informace najdete v tématu věnovaném [vnitřním procesorům platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="3edee-143">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="3edee-144">Výchozí spustitelné soubory</span><span class="sxs-lookup"><span data-stu-id="3edee-144">Default executables</span></span>

<span data-ttu-id="3edee-145">.NET Core teď ve výchozím nastavení vytváří [spustitelné soubory závislé na rozhraní](../deploying/index.md#framework-dependent-executables-fde) .</span><span class="sxs-lookup"><span data-stu-id="3edee-145">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="3edee-146">Toto chování je nové u aplikací, které používají globálně nainstalovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3edee-146">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="3edee-147">Dříve mohli pouze [samostatně nasazená nasazení](../deploying/index.md#self-contained-deployments-scd) vyvolat spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3edee-147">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="3edee-148">Během `dotnet build` nebo`dotnet publish`se vytvoří spustitelný soubor, který odpovídá prostředí a platformě používané sady SDK.</span><span class="sxs-lookup"><span data-stu-id="3edee-148">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="3edee-149">Pomocí těchto spustitelných souborů můžete očekávat stejné věci jako jiné nativní spustitelné soubory, jako například:</span><span class="sxs-lookup"><span data-stu-id="3edee-149">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="3edee-150">Můžete dvakrát kliknout na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3edee-150">You can double-click on the executable.</span></span>
* <span data-ttu-id="3edee-151">Aplikaci můžete spustit z příkazového řádku přímo, například `myapp.exe` ve Windows, a `./myapp` v systémech Linux a MacOS.</span><span class="sxs-lookup"><span data-stu-id="3edee-151">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="3edee-152">Spustitelné soubory s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="3edee-152">Single-file executables</span></span>

<span data-ttu-id="3edee-153">`dotnet publish` Příkaz podporuje balení vaší aplikace do spustitelného souboru specifického pro jednotlivé platformy.</span><span class="sxs-lookup"><span data-stu-id="3edee-153">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="3edee-154">Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativních), které jsou nutné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3edee-154">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="3edee-155">Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru buildu.</span><span class="sxs-lookup"><span data-stu-id="3edee-155">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="3edee-156">Spuštění je rychlejší, když aplikaci znovu spustíte.</span><span class="sxs-lookup"><span data-stu-id="3edee-156">Startup is faster when the application is run again.</span></span> <span data-ttu-id="3edee-157">Pokud se nepoužila nová verze, aplikace se už nebude muset extrahovat druhou dobu.</span><span class="sxs-lookup"><span data-stu-id="3edee-157">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="3edee-158">Chcete-li publikovat soubor s jedním souborem, nastavte `PublishSingleFile` v projektu nebo na příkazovém řádku `dotnet publish` pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="3edee-158">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="3edee-159">-nebo-</span><span class="sxs-lookup"><span data-stu-id="3edee-159">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="3edee-160">Další informace o publikování v jednom souboru najdete v [dokumentu návrhu sady prostředků s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="3edee-160">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="3edee-161">Propojení sestavení</span><span class="sxs-lookup"><span data-stu-id="3edee-161">Assembly linking</span></span>

<span data-ttu-id="3edee-162">Sada .NET Core 3,0 SDK je dodávána s nástrojem, který umožňuje zmenšit velikost aplikací analýzou IL a oříznutím nepoužívaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="3edee-162">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="3edee-163">Samostatné aplikace zahrnují vše potřebné ke spuštění kódu, aniž by bylo nutné nainstalovat rozhraní .NET do hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="3edee-163">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="3edee-164">Ale hodně, kolikrát aplikace jenom vyžaduje malou podmnožinu rozhraní, a další nepoužívané knihovny by se daly odebrat.</span><span class="sxs-lookup"><span data-stu-id="3edee-164">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="3edee-165">Rozhraní .NET Core nyní obsahuje nastavení, které bude používat nástroj [linkeru Il](https://github.com/mono/linker) ke kontrole Il vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3edee-165">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="3edee-166">Tento nástroj zjistí, jaký kód je požadován, a poté ořízne nepoužívané knihovny.</span><span class="sxs-lookup"><span data-stu-id="3edee-166">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="3edee-167">Tento nástroj může významně snížit velikost nasazení některých aplikací.</span><span class="sxs-lookup"><span data-stu-id="3edee-167">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="3edee-168">Chcete-li tento nástroj povolit, `<PublishTrimmed>` přidejte do projektu nastavení a publikujte samostatně uzavřenou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="3edee-168">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="3edee-169">Příklad: základní šablona projektu "Hello World", která je součástí, je-li publikována, má velikost přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="3edee-169">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="3edee-170">Pomocí `<PublishTrimmed>`této velikosti se velikost zmenší na přibližně 30 MB.</span><span class="sxs-lookup"><span data-stu-id="3edee-170">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="3edee-171">Je důležité vzít v úvahu, že aplikace nebo architektury (včetně ASP.NET Core a WPF), které používají reflexi nebo související dynamické funkce, budou často přerušit při oříznutí.</span><span class="sxs-lookup"><span data-stu-id="3edee-171">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="3edee-172">K tomuto zlomku dochází, protože linker neví o tomto dynamickém chování a nemůže určit, které typy rozhraní jsou pro reflexi vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="3edee-172">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="3edee-173">Nástroj linkeru IL se dá nakonfigurovat tak, aby se na tento scénář dozvěděl.</span><span class="sxs-lookup"><span data-stu-id="3edee-173">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="3edee-174">Nad všemi ostatními nezapomeňte aplikaci otestovat po jejím oříznutí.</span><span class="sxs-lookup"><span data-stu-id="3edee-174">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="3edee-175">Další informace o nástroji linkeru IL naleznete v [dokumentaci](https://aka.ms/dotnet-illink) nebo v úložišti [mono/linker]( https://github.com/mono/linker) .</span><span class="sxs-lookup"><span data-stu-id="3edee-175">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="3edee-176">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="3edee-176">Tiered compilation</span></span>

<span data-ttu-id="3edee-177">[Vrstvená kompilace](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) je ve výchozím nastavení zapnuté pomocí .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3edee-177">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="3edee-178">Tato funkce umožňuje modulu runtime pružně použít kompilátor JIT (just-in-time) a získat tak lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="3edee-178">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="3edee-179">Hlavní výhodou TC je povolit (znovu) jitting metody s pomalejším, ale rychlejším vytvářením kódu nebo vyšší kvality, ale pomalejší vytváření kódu.</span><span class="sxs-lookup"><span data-stu-id="3edee-179">The main benefit of TC is to enable (re-)jitting methods with slower-but-faster to produce code or higher-quality-but-slower to produce code.</span></span> <span data-ttu-id="3edee-180">To pomáhá zvýšit výkon aplikace, protože projde různými fázemi provádění, od spuštění po ustáleném stavu.</span><span class="sxs-lookup"><span data-stu-id="3edee-180">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="3edee-181">To se liší od přístupu bez použití TC, kde je každá metoda zkompilována jedním způsobem (stejně jako vysoká úroveň kvality), která je pro výkon při spuštění posunuta na ustálený stav.</span><span class="sxs-lookup"><span data-stu-id="3edee-181">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="3edee-182">Chcete-li povolit rychlou JIT (zpracovaných kompilátorem JIT kód vrstvy 0), použijte toto nastavení v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="3edee-182">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="3edee-183">Chcete-li úplně zakázat použití TC, použijte toto nastavení v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="3edee-183">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="3edee-184">ReadyToRun image</span><span class="sxs-lookup"><span data-stu-id="3edee-184">ReadyToRun images</span></span>

<span data-ttu-id="3edee-185">Můžete zlepšit čas spuštění aplikace .NET Core kompilováním sestavení aplikace jako formátu ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="3edee-185">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="3edee-186">R2R je forma kompilace v čase před zahájením (AOT).</span><span class="sxs-lookup"><span data-stu-id="3edee-186">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="3edee-187">R2R binární soubory zlepšují výkon při spuštění tím, že snižují množství práce, které kompilátor JIT (just-in-time) potřebuje k tomu, aby se vaše aplikace načítají.</span><span class="sxs-lookup"><span data-stu-id="3edee-187">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="3edee-188">Binární soubory obsahují podobný nativní kód v porovnání s tím, co by kompilátor JIT vytvořil.</span><span class="sxs-lookup"><span data-stu-id="3edee-188">The binaries contain similar native code compared to what the JIT would produce.</span></span>

<span data-ttu-id="3edee-189">Binární soubory R2R jsou větší, protože obsahují kód jazyka IL (Intermediate Language), který je stále potřeba pro některé scénáře, a nativní verzi stejného kódu.</span><span class="sxs-lookup"><span data-stu-id="3edee-189">R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="3edee-190">R2R je k dispozici jenom v případě, že publikujete samostatnou aplikaci, která cílí na konkrétní běhové prostředí (RID), jako je Linux x64 nebo Windows x64.</span><span class="sxs-lookup"><span data-stu-id="3edee-190">R2R is only available when you publish a self-contained app that targets a specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="3edee-191">Pokud chcete svou aplikaci zkompilovat jako R2R, přidejte `<PublishReadyToRun>` nastavení:</span><span class="sxs-lookup"><span data-stu-id="3edee-191">To compile your app as R2R, add the `<PublishReadyToRun>` setting:</span></span>

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

<span data-ttu-id="3edee-192">Publikujte samostatně uzavřenou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3edee-192">Publish a self-contained app.</span></span> <span data-ttu-id="3edee-193">Tento příkaz například vytvoří samostatnou aplikaci pro 64 verzi Windows:</span><span class="sxs-lookup"><span data-stu-id="3edee-193">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="3edee-194">Omezení pro různé platformy a architektury</span><span class="sxs-lookup"><span data-stu-id="3edee-194">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="3edee-195">Kompilátor ReadyToRun v současné době nepodporuje cílení na více platforem.</span><span class="sxs-lookup"><span data-stu-id="3edee-195">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="3edee-196">Je nutné kompilovat na daném cíli.</span><span class="sxs-lookup"><span data-stu-id="3edee-196">You must compile on a given target.</span></span> <span data-ttu-id="3edee-197">Například pokud chcete image R2R pro Windows x64, musíte v tomto prostředí spustit příkaz publikovat.</span><span class="sxs-lookup"><span data-stu-id="3edee-197">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="3edee-198">Výjimky pro cílení na více platforem:</span><span class="sxs-lookup"><span data-stu-id="3edee-198">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="3edee-199">Systém Windows x64 lze použít ke kompilaci imagí Windows ARM32, ARM64 a x86.</span><span class="sxs-lookup"><span data-stu-id="3edee-199">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="3edee-200">K kompilování imagí Windows ARM32 lze použít systém Windows x86.</span><span class="sxs-lookup"><span data-stu-id="3edee-200">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="3edee-201">Linux x64 lze použít ke kompilaci imagí ARM32 a ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="3edee-201">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="3edee-202">Sestavení kopíruje závislosti</span><span class="sxs-lookup"><span data-stu-id="3edee-202">Build copies dependencies</span></span>

<span data-ttu-id="3edee-203">`dotnet build` Příkaz nyní kopíruje závislosti NuGet pro vaši aplikaci z mezipaměti NuGet do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="3edee-203">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="3edee-204">Dříve se závislosti zkopírovaly jenom jako součást `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="3edee-204">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="3edee-205">Existují některé operace, jako je propojování a publikování stránek Razor, které budou nadále vyžadovat publikování.</span><span class="sxs-lookup"><span data-stu-id="3edee-205">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="3edee-206">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="3edee-206">Local tools</span></span>

<span data-ttu-id="3edee-207">.NET Core 3,0 zavádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="3edee-207">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="3edee-208">Místní nástroje jsou podobné [globálním nástrojům](../tools/global-tools.md) , ale jsou přidruženy k určitému umístění na disku.</span><span class="sxs-lookup"><span data-stu-id="3edee-208">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="3edee-209">Místní nástroje nejsou globálně dostupné a distribuují se jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="3edee-209">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="3edee-210">Pokud jste si vyzkoušeli místní nástroje v rozhraní .NET Core 3,0 Preview 1 `dotnet tool restore` , `dotnet tool install`jako je třeba spuštění nebo, odstraňte složku mezipaměti místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="3edee-210">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="3edee-211">V opačném případě místní nástroje nebudou fungovat v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="3edee-211">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="3edee-212">Tato složka je umístěna v umístění:</span><span class="sxs-lookup"><span data-stu-id="3edee-212">This folder is located at:</span></span>
>
> <span data-ttu-id="3edee-213">V macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="3edee-213">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="3edee-214">Ve Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="3edee-214">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="3edee-215">Místní nástroje spoléhají na název `dotnet-tools.json` souboru manifestu v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="3edee-215">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="3edee-216">Tento soubor manifestu definuje nástroje, které jsou k dispozici v této složce a níže.</span><span class="sxs-lookup"><span data-stu-id="3edee-216">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="3edee-217">Můžete distribuovat soubor manifestu s vaším kódem, aby bylo zajištěno, že kdokoli, kdo spolupracuje s vaším kódem, může obnovit a použít stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="3edee-217">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="3edee-218">U globálních i místních nástrojů se vyžaduje kompatibilní verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3edee-218">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="3edee-219">Mnoho nástrojů, které jsou aktuálně na NuGet.org Target pro .NET Core Runtime 2,1.</span><span class="sxs-lookup"><span data-stu-id="3edee-219">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="3edee-220">Pokud chcete tyto nástroje nainstalovat globálně nebo lokálně, budete si muset nainstalovat [modul runtime .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="3edee-220">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="3edee-221">Hlavní verze – posunutí – posun</span><span class="sxs-lookup"><span data-stu-id="3edee-221">Major-version Roll Forward</span></span>

<span data-ttu-id="3edee-222">.NET Core 3,0 zavádí funkci pro výslovný souhlas, která umožňuje aplikaci přejít na nejnovější hlavní verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3edee-222">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="3edee-223">Kromě toho bylo přidáno nové nastavení, které řídí, jak se ve vaší aplikaci aplikuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="3edee-223">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="3edee-224">Dá se nakonfigurovat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="3edee-224">This can be configured in the following ways:</span></span>

- <span data-ttu-id="3edee-225">Vlastnost souboru projektu:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="3edee-225">Project file property: `RollForward`</span></span>
- <span data-ttu-id="3edee-226">Vlastnost konfiguračního souboru modulu runtime:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="3edee-226">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="3edee-227">Proměnná prostředí:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="3edee-227">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="3edee-228">Argument příkazového řádku:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="3edee-228">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="3edee-229">Je nutné zadat jednu z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="3edee-229">One of the following values must be specified.</span></span> <span data-ttu-id="3edee-230">Pokud je nastavení vynecháno, je  výchozí hodnota podverze.</span><span class="sxs-lookup"><span data-stu-id="3edee-230">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="3edee-231">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="3edee-231">**LatestPatch**</span></span>\
<span data-ttu-id="3edee-232">Vraťte se k nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="3edee-232">Roll forward to the highest patch version.</span></span> <span data-ttu-id="3edee-233">Tím se zakáže dílčí verze s posunem.</span><span class="sxs-lookup"><span data-stu-id="3edee-233">This disables minor version roll forward.</span></span>
- <span data-ttu-id="3edee-234">**Moll**</span><span class="sxs-lookup"><span data-stu-id="3edee-234">**Minor**</span></span>\
<span data-ttu-id="3edee-235">V případě, že chybí požadovaná dílčí verze, převeďte nahoru na nejnižší nižší verzi.</span><span class="sxs-lookup"><span data-stu-id="3edee-235">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="3edee-236">Pokud je k dispozici požadovaná dílčí verze, použije se zásada **LatestPatch** .</span><span class="sxs-lookup"><span data-stu-id="3edee-236">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="3edee-237">**Nejdůležitější**</span><span class="sxs-lookup"><span data-stu-id="3edee-237">**Major**</span></span>\
<span data-ttu-id="3edee-238">Pokud chybí požadovaná hlavní verze, převeďte ji nahoru na nejnižší nejvyšší hlavní verzi a nejnižší podverzi.</span><span class="sxs-lookup"><span data-stu-id="3edee-238">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="3edee-239">Pokud je k dispozici požadovaná hlavní verze, použije se **vedlejší** zásada.</span><span class="sxs-lookup"><span data-stu-id="3edee-239">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="3edee-240">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="3edee-240">**LatestMinor**</span></span>\
<span data-ttu-id="3edee-241">Převeďte do nejvyšší dílčí verze, i když je k dispozici požadovaná dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="3edee-241">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="3edee-242">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="3edee-242">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="3edee-243">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="3edee-243">**LatestMajor**</span></span>\
<span data-ttu-id="3edee-244">Převeďte do nejvyšší hlavní a nejvyšší dílčí verze, a to i v případě, že je k dispozici požadovaná hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="3edee-244">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="3edee-245">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="3edee-245">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="3edee-246">**Dezaktivovat**</span><span class="sxs-lookup"><span data-stu-id="3edee-246">**Disable**</span></span>\
<span data-ttu-id="3edee-247">Nezadávejte vše.</span><span class="sxs-lookup"><span data-stu-id="3edee-247">Don't roll forward.</span></span> <span data-ttu-id="3edee-248">Vytvoří se jenom vazba na určenou verzi.</span><span class="sxs-lookup"><span data-stu-id="3edee-248">Only bind to specified version.</span></span> <span data-ttu-id="3edee-249">Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám.</span><span class="sxs-lookup"><span data-stu-id="3edee-249">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="3edee-250">Tato hodnota se doporučuje jenom pro testování.</span><span class="sxs-lookup"><span data-stu-id="3edee-250">This value is only recommended for testing.</span></span>

<span data-ttu-id="3edee-251">Kromě nastavení **Zakázat** bude pro všechna nastavení použita nejvyšší dostupná verze opravy.</span><span class="sxs-lookup"><span data-stu-id="3edee-251">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="3edee-252">Plocha Windows</span><span class="sxs-lookup"><span data-stu-id="3edee-252">Windows desktop</span></span>

<span data-ttu-id="3edee-253">.NET Core 3,0 podporuje desktopové aplikace Windows pomocí Windows Presentation Foundation (WPF) a model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3edee-253">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="3edee-254">Tyto architektury také podporují použití moderních ovládacích prvků a Fluent stylování z knihovny XAML uživatelského rozhraní systému Windows (WinUI) přes [ostrovy XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="3edee-254">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="3edee-255">Součást Desktop systému Windows je součástí sady Windows .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="3edee-255">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="3edee-256">Novou aplikaci WPF nebo model Windows Forms můžete vytvořit pomocí následujících `dotnet` příkazů:</span><span class="sxs-lookup"><span data-stu-id="3edee-256">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="3edee-257">Visual Studio 2019 přidává **nové šablony projektů** pro .net Core 3,0 model Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="3edee-257">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="3edee-258">Další informace o tom, jak přenést existující aplikaci .NET Framework, naleznete v tématu [port WPF Projects](../porting/wpf.md) and [port model Windows Forms Projects](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="3edee-258">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="3edee-259">Komponenty s podporou modelu COM – Desktop Windows</span><span class="sxs-lookup"><span data-stu-id="3edee-259">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="3edee-260">Ve Windows teď můžete vytvářet spravované komponenty, které lze volat v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3edee-260">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="3edee-261">Tato možnost je zásadní pro použití .NET Core s modely doplňku COM a také k zajištění parity s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3edee-261">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="3edee-262">Na rozdíl od .NET Framework, kde se *Knihovna Mscoree. dll* použila jako server com, .NET Core při sestavování komponenty com přidá nativní spouštěcí knihovnu DLL do adresáře *bin* .</span><span class="sxs-lookup"><span data-stu-id="3edee-262">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="3edee-263">Příklad vytvoření komponenty modelu COM a její využití naleznete v [ukázce modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="3edee-263">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="3edee-264">Nasazení MSIX – Desktop Windows</span><span class="sxs-lookup"><span data-stu-id="3edee-264">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="3edee-265">[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3edee-265">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="3edee-266">Dá se použít k nasazení desktopových aplikací .NET Core 3,0 do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3edee-266">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="3edee-267">[Projekt pro balení aplikace pro systém Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), který je k dispozici v aplikaci Visual Studio 2019, umožňuje vytvářet balíčky MSIX pomocí aplikací .NET Core s využitím [vlastních součástí](../deploying/index.md#self-contained-deployments-scd) .</span><span class="sxs-lookup"><span data-stu-id="3edee-267">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="3edee-268">Soubor projektu .NET Core musí určovat podporované běhové moduly ve `<RuntimeIdentifiers>` vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="3edee-268">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="3edee-269">HighDPI WinForms</span><span class="sxs-lookup"><span data-stu-id="3edee-269">WinForms HighDPI</span></span>

<span data-ttu-id="3edee-270">Aplikace .NET Core model Windows Forms můžou nastavit režim s vysokým <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>rozlišením DPI pomocí.</span><span class="sxs-lookup"><span data-stu-id="3edee-270">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3edee-271">Metoda nastaví odpovídající režim vysoké úrovně dpi, pokud nastavení nebylo nastaveno jiným způsobem, jako `App.Manifest` je `Application.Run`nebo P/Invoke. `SetHighDpiMode`</span><span class="sxs-lookup"><span data-stu-id="3edee-271">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="3edee-272">Možné `highDpiMode` hodnoty, jak je vyjádřené <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> výčtem:</span><span class="sxs-lookup"><span data-stu-id="3edee-272">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="3edee-273">Další informace o režimech vysokého rozlišení DPI najdete v tématu [vývoj desktopových aplikací s vysokým rozlišením v systému Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="3edee-273">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="3edee-274">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="3edee-274">Ranges and indices</span></span>

<span data-ttu-id="3edee-275">Nový <xref:System.Index?displayProperty=nameWithType> typ lze použít k indexování.</span><span class="sxs-lookup"><span data-stu-id="3edee-275">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="3edee-276">Můžete vytvořit jednu z `int` těchto počtů od začátku nebo s operátorem prefix `^` (C#), který se počítá od konce:</span><span class="sxs-lookup"><span data-stu-id="3edee-276">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="3edee-277">Je zde také <xref:System.Range?displayProperty=nameWithType> typ, který se skládá ze dvou `Index` hodnot, jeden pro začátek a jeden pro konec a `x..y` lze jej zapsat s výrazem rozsahu (C#).</span><span class="sxs-lookup"><span data-stu-id="3edee-277">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="3edee-278">Pak můžete indexovat pomocí `Range`, který vytváří řez:</span><span class="sxs-lookup"><span data-stu-id="3edee-278">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="3edee-279">Další informace najdete v [kurzu rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="3edee-279">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="3edee-280">Asynchronní streamy</span><span class="sxs-lookup"><span data-stu-id="3edee-280">Async streams</span></span>

<span data-ttu-id="3edee-281">Typ je nová asynchronní <xref:System.Collections.Generic.IEnumerable%601>verze. <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="3edee-281">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="3edee-282">Jazyk vám umožní `await foreach` `IAsyncEnumerable<T>` využít jejich prvky a využít `yield return` je k vytváření prvků.</span><span class="sxs-lookup"><span data-stu-id="3edee-282">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="3edee-283">Následující příklad ukazuje produkci a spotřebu asynchronních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="3edee-283">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="3edee-284">Příkaz je asynchronní a sám používá `yield return` k tvorbě asynchronního datového proudu pro volající. `foreach`</span><span class="sxs-lookup"><span data-stu-id="3edee-284">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="3edee-285">Tento vzor (použití `yield return`) je doporučeným modelem pro vytváření asynchronních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="3edee-285">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="3edee-286">Kromě `await foreach`toho je možné také vytvořit asynchronní iterátory, například iterátor, který `IAsyncEnumerable/IAsyncEnumerator` vrátí `yield` , který můžete i `await` v.</span><span class="sxs-lookup"><span data-stu-id="3edee-286">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="3edee-287">Pro objekty, které je třeba uvolnit, můžete použít `IAsyncDisposable`, které BCL různé typy, `Stream` například a `Timer`.</span><span class="sxs-lookup"><span data-stu-id="3edee-287">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="3edee-288">Další informace najdete v [kurzu asynchronní streamy](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="3edee-288">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="3edee-289">Vylepšení standardu IEEE s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="3edee-289">IEEE Floating-point improvements</span></span>

<span data-ttu-id="3edee-290">Rozhraní API s plovoucí desetinnou čárkou se aktualizují tak, aby odpovídalo [revizi IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="3edee-290">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="3edee-291">Cílem těchto změn je vystavit všechny **požadované** operace a zajistit, aby byly vyhovující požadavkům standardu IEEE. Další informace o vylepšeních s plovoucí desetinnou čárkou naleznete v příspěvku na blogu [.NET Core 3,0 v oblasti analýzy a formátování plovoucí desetinné](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) čárky.</span><span class="sxs-lookup"><span data-stu-id="3edee-291">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="3edee-292">Mezi aktualizace pro analýzu a formátování patří:</span><span class="sxs-lookup"><span data-stu-id="3edee-292">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="3edee-293">Správně Analyzujte a zaokrouhlujte vstupy libovolné délky.</span><span class="sxs-lookup"><span data-stu-id="3edee-293">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="3edee-294">Správně Analyzujte a formátujete záporné hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="3edee-294">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="3edee-295">Správně analyzovat `Infinity` a `NaN` provést kontrolu bez rozlišení velkých a malých písmen a povolit volitelnou předchozí `+` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3edee-295">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="3edee-296">Mezi <xref:System.Math?displayProperty=nameWithType> nová rozhraní API patří:</span><span class="sxs-lookup"><span data-stu-id="3edee-296">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="3edee-297"><xref:System.Math.BitIncrement(System.Double)>ani<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="3edee-297"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="3edee-298">Odpovídá operacím `nextDown` IEEE a.`nextUp`</span><span class="sxs-lookup"><span data-stu-id="3edee-298">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="3edee-299">Vrátí nejmenší číslo s plovoucí desetinnou čárkou, které porovná větší nebo menší než vstup (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="3edee-299">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="3edee-300">Například `Math.BitIncrement(0.0)` vrátí `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="3edee-300">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="3edee-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>ani<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="3edee-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="3edee-302">Odpovídá operacím `minNumMag` IEEE a,vracíhodnotu,kterájevětšínebomenšívrozsahudvouvstupů(vuvedenémpořadí).`maxNumMag`</span><span class="sxs-lookup"><span data-stu-id="3edee-302">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="3edee-303">Například `Math.MaxMagnitude(2.0, -3.0)` vrátí `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="3edee-303">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="3edee-304">Odpovídá operaci `logB` IEEE, která vrací celočíselnou hodnotu, vrátí protokol integrálního protokolu Base-2 vstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="3edee-304">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="3edee-305">Tato metoda je prakticky stejná jako `floor(log2(x))`, ale byla provedena s minimální chybou zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="3edee-305">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="3edee-306">Odpovídá operaci `x * pow(2, n)`IEEE, která přebírá celočíselnou hodnotu, vrátí ji efektivně, ale provede minimální chybu zaokrouhlení. `scaleB`</span><span class="sxs-lookup"><span data-stu-id="3edee-306">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="3edee-307">Odpovídá operaci `log2` IEEE, vrátí logaritmus o základu 2.</span><span class="sxs-lookup"><span data-stu-id="3edee-307">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="3edee-308">Minimalizuje chybu zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="3edee-308">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="3edee-309">Odpovídá operaci `fma` IEEE, provádí přidaný násobek.</span><span class="sxs-lookup"><span data-stu-id="3edee-309">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="3edee-310">To znamená `(x * y) + z` , že se jedná o jednu operaci, existuje-li minimalizace chyby zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="3edee-310">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="3edee-311">Příkladem může být `FusedMultiplyAdd(1e308, 2.0, -1e308)` vrácení. `1e308`</span><span class="sxs-lookup"><span data-stu-id="3edee-311">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="3edee-312">Funkce Regular `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="3edee-312">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="3edee-313">Odpovídá operaci `x`IEEE, vrací hodnotu, `y`ale s znaménkem. `copySign`</span><span class="sxs-lookup"><span data-stu-id="3edee-313">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="3edee-314">Rychlá integrovaná podpora JSON</span><span class="sxs-lookup"><span data-stu-id="3edee-314">Fast built-in JSON support</span></span>

<span data-ttu-id="3edee-315">Uživatelé rozhraní .NET mají převážně na [**JSON.NET**](https://www.newtonsoft.com/json) a další oblíbené knihovny JSON, které budou mít i nadále dobré možnosti.</span><span class="sxs-lookup"><span data-stu-id="3edee-315">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="3edee-316">**JSON.NET** používá řetězce .NET jako základní datový typ, který je v digestoři UTF-16.</span><span class="sxs-lookup"><span data-stu-id="3edee-316">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="3edee-317">Nová integrovaná podpora JSON je vysoce výkonná, nízká alokace a založená na `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="3edee-317">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="3edee-318">Do .NET Core 3,0 <xref:System.Text.Json?displayProperty=nameWithType> oboru názvů se přidaly tři nové hlavní typy související s JSON.</span><span class="sxs-lookup"><span data-stu-id="3edee-318">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3edee-319">Tyto typy *ještě* nepodporují serializaci a deserializaci objektu CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="3edee-319">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="3edee-320">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="3edee-320">Utf8JsonReader</span></span>

<span data-ttu-id="3edee-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>je pro text JSON s kódováním UTF-8 s vysokým výkonem k dispozici vysoce výkonné a nízké přidělení, načtený z `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="3edee-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="3edee-322">`Utf8JsonReader` Je základní typ nízké úrovně, který lze použít k sestavení vlastních analyzátorů a deserializace.</span><span class="sxs-lookup"><span data-stu-id="3edee-322">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="3edee-323">Čtení prostřednictvím datové části JSON pomocí nového `Utf8JsonReader` je 2x rychlejší než použití čtecího zařízení z **JSON.NET**.</span><span class="sxs-lookup"><span data-stu-id="3edee-323">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="3edee-324">Nepřiřazuje se, dokud nebudete muset actualize tokeny JSON jako řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="3edee-324">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="3edee-325">Tady je příklad, jak číst pomocí souboru [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) vytvořeného pomocí Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="3edee-325">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="3edee-326">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="3edee-326">Utf8JsonWriter</span></span>

<span data-ttu-id="3edee-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>poskytuje vysoce výkonný a neuložený v mezipaměti, a to jenom pro psaní textu JSON v kódování UTF-8 ze běžných typů .NET, `String`jako `Int32`jsou, `DateTime`a.</span><span class="sxs-lookup"><span data-stu-id="3edee-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="3edee-328">Podobně jako čtenář je modul pro zápis základní typ nízké úrovně, který lze použít k vytvoření vlastních serializátorů.</span><span class="sxs-lookup"><span data-stu-id="3edee-328">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="3edee-329">Zápis datové části JSON pomocí nového `Utf8JsonWriter` je 30-80% rychlejší než použití zapisovače z **JSON.NET** a nepřiřazuje.</span><span class="sxs-lookup"><span data-stu-id="3edee-329">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="3edee-330">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="3edee-330">JsonDocument</span></span>

<span data-ttu-id="3edee-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>je postaven na začátku `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="3edee-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="3edee-332">`JsonDocument` Poskytuje možnost analyzovat data JSON a sestavit model DOM (Document Object Model) (DOM) jen pro čtení, které se dají dotazovat na podporu náhodného přístupu a výčtu.</span><span class="sxs-lookup"><span data-stu-id="3edee-332">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="3edee-333">Prvky JSON, které tvoří data, mohou být přístupné prostřednictvím <xref:System.Text.Json.JsonElement> typu, který je zveřejněn `JsonDocument` jako vlastnost s názvem `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="3edee-333">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="3edee-334">`JsonElement` Obsahuje enumerátory pole a objektu JSON spolu s rozhraními API pro převod textu JSON na běžné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="3edee-334">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="3edee-335">Analýza typické datové části JSON a přístup ke všem jeho členům pomocí `JsonDocument` je 2 – 3x rychlejší než **JSON.NET** s malým přidělením dat, která mají rozumně velikost (to znamená < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="3edee-335">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="3edee-336">Zde je ukázkové použití `JsonDocument` a `JsonElement` , které lze použít jako výchozí bod:</span><span class="sxs-lookup"><span data-stu-id="3edee-336">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

<span data-ttu-id="3edee-337">Tady je příklad C# 8,0 souboru [Launch. JSON](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) vytvořeného pomocí Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="3edee-337">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="3edee-338">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="3edee-338">JsonSerializer</span></span>

<span data-ttu-id="3edee-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType>je postaven na začátku <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter> k poskytnutí rychlé možnosti serializace v nízké paměti při práci s dokumenty a fragmenty JSON.</span><span class="sxs-lookup"><span data-stu-id="3edee-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="3edee-340">Projděte https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md si příklad pro přenos do tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="3edee-340">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md for an example to port to this article</span></span>

<span data-ttu-id="3edee-341">Tady je příklad serializace objektu do formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="3edee-341">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="3edee-342">Zde je příklad deserializace řetězce JSON na objekt.</span><span class="sxs-lookup"><span data-stu-id="3edee-342">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="3edee-343">Můžete použít řetězec JSON vyprodukovaný předchozím příkladem:</span><span class="sxs-lookup"><span data-stu-id="3edee-343">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="3edee-344">Vylepšení spolupráce</span><span class="sxs-lookup"><span data-stu-id="3edee-344">Interop improvements</span></span>

<span data-ttu-id="3edee-345">.NET Core 3,0 vylepšuje nativní interoperabilitu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3edee-345">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="3edee-346">Zadejte: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="3edee-346">Type: NativeLibrary</span></span>

<span data-ttu-id="3edee-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>poskytuje zapouzdření pro načtení nativní knihovny (pomocí stejné logiky zatížení jako .NET Core P/Invoke) a poskytnutí relevantních pomocných funkcí, jako je `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="3edee-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="3edee-348">Příklad kódu naleznete v [ukázce DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="3edee-348">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="3edee-349">Nativní spolupráce Windows</span><span class="sxs-lookup"><span data-stu-id="3edee-349">Windows Native Interop</span></span>

<span data-ttu-id="3edee-350">Systém Windows nabízí bohatě nativní rozhraní API ve formě plochých rozhraní API jazyka C, COM a WinRT.</span><span class="sxs-lookup"><span data-stu-id="3edee-350">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="3edee-351">I když .NET Core podporuje **volání**nespravovaného voláním .net Core 3,0, přidává možnost **vytvořit rozhraní API modelu COM** a **aktivovat rozhraní API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="3edee-351">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="3edee-352">Příklad kódu naleznete v [ukázce v aplikaci Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="3edee-352">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="3edee-353">Podpora HTTP/2</span><span class="sxs-lookup"><span data-stu-id="3edee-353">HTTP/2 support</span></span>

<span data-ttu-id="3edee-354"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typ podporuje protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="3edee-354">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="3edee-355">Pokud je povolený protokol HTTP/2, vyjednává se verze protokolu HTTP prostřednictvím TLS/ALPN a protokol HTTP/2 se použije, pokud se server rozhodne ho použít.</span><span class="sxs-lookup"><span data-stu-id="3edee-355">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="3edee-356">Výchozí protokol zůstává HTTP/1.1, ale protokol HTTP/2 může být povolen dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="3edee-356">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="3edee-357">Nejdřív můžete nastavit zprávu požadavku HTTP na používání HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="3edee-357">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="3edee-358">Za druhé, ve výchozím <xref:System.Net.Http.HttpClient> nastavení se dá změnit na použití HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="3edee-358">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="3edee-359">V mnoha případech, kdy vyvíjíte aplikaci, chcete použít nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="3edee-359">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="3edee-360">Pokud víte, že cílový koncový bod bude používat protokol HTTP/2, můžete zapnout nezašifrovaná připojení pro HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="3edee-360">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="3edee-361">Můžete ji zapnout nastavením `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` proměnné prostředí na `1` nebo povolením v kontextu aplikace:</span><span class="sxs-lookup"><span data-stu-id="3edee-361">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="3edee-362">TLS 1,3 & OpenSSL 1.1.1 v systému Linux</span><span class="sxs-lookup"><span data-stu-id="3edee-362">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="3edee-363">.NET Core teď využívá [podporu TLS 1,3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), pokud je dostupná v daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="3edee-363">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="3edee-364">S protokolem TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="3edee-364">With TLS 1.3:</span></span>

* <span data-ttu-id="3edee-365">Časy připojení se zlepšily s omezenou špičkou odezvy mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="3edee-365">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="3edee-366">Vylepšené zabezpečení kvůli odebrání různých zastaralých a nezabezpečených kryptografických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="3edee-366">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="3edee-367">V případě, že je k dispozici, .NET Core 3,0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**nebo **OpenSSL 1.0.2** v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="3edee-367">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="3edee-368">Pokud je k dispozici služba **OpenSSL 1.1.1** <xref:System.Net.Security.SslStream?displayProperty=nameWithType> , budou v obou <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> typech použity **protokoly TLS 1,3** (za předpokladu, že klient i server podporují protokol **TLS 1,3**).</span><span class="sxs-lookup"><span data-stu-id="3edee-368">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="3edee-369">Windows a macOS ještě nepodporují **TLS 1,3**.</span><span class="sxs-lookup"><span data-stu-id="3edee-369">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="3edee-370">Až bude podpora k dispozici, bude .NET Core 3,0 podporovat **TLS 1,3** v těchto operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="3edee-370">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="3edee-371">Následující C# příklad 8,0 ukazuje rozhraní .net Core 3,0 v Ubuntu 18,10, které <https://www.cloudflare.com>se připojuje k:</span><span class="sxs-lookup"><span data-stu-id="3edee-371">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="3edee-372">Kryptografická šifry</span><span class="sxs-lookup"><span data-stu-id="3edee-372">Cryptography ciphers</span></span>

<span data-ttu-id="3edee-373">.NET 3,0 přidává podporu pro šifry **AES-GCM** a **AES-ccm** , implementovaná <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> v <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> a v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3edee-373">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="3edee-374">Tyto algoritmy jsou jak [ověřené šifrování, tak i algoritmy AEAD (Association data)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="3edee-374">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="3edee-375">Následující kód demonstruje `AesGcm` použití šifry k šifrování a dešifrování náhodných dat.</span><span class="sxs-lookup"><span data-stu-id="3edee-375">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="3edee-376">Import/export kryptografického klíče</span><span class="sxs-lookup"><span data-stu-id="3edee-376">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="3edee-377">.NET Core 3,0 podporuje import a export asymetrických veřejných a privátních klíčů ze standardních formátů.</span><span class="sxs-lookup"><span data-stu-id="3edee-377">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="3edee-378">Nemusíte používat certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="3edee-378">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="3edee-379">Všechny typy klíčů, jako jsou *RSA*, *DSA*, *ECDSA*a *ECDiffieHellman*, podporují následující formáty:</span><span class="sxs-lookup"><span data-stu-id="3edee-379">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="3edee-380">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="3edee-380">**Public Key**</span></span>
  * <span data-ttu-id="3edee-381">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="3edee-381">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="3edee-382">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="3edee-382">**Private key**</span></span>
  * <span data-ttu-id="3edee-383">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="3edee-383">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="3edee-384">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="3edee-384">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="3edee-385">Klíče RSA podporují i:</span><span class="sxs-lookup"><span data-stu-id="3edee-385">RSA keys also support:</span></span>

* <span data-ttu-id="3edee-386">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="3edee-386">**Public Key**</span></span>
  * <span data-ttu-id="3edee-387">RSAPublicKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="3edee-387">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="3edee-388">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="3edee-388">**Private key**</span></span>
  * <span data-ttu-id="3edee-389">RSAPrivateKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="3edee-389">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="3edee-390">Metody exportu vytváří binární data kódovaná v kódování DER a metody importu očekávají stejné.</span><span class="sxs-lookup"><span data-stu-id="3edee-390">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="3edee-391">Pokud je klíč uložený v textovém formátu PEM, volající bude muset před voláním metody import kódování Base64 a dekódovat obsah.</span><span class="sxs-lookup"><span data-stu-id="3edee-391">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="3edee-392">Soubory **PKCS # 8** lze kontrolovat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> souborů a soubory **PFX a PKCS # 12** lze zkontrolovat pomocí. <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3edee-392">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3edee-393">Soubory **PFX/PKCS # 12** se můžou manipulovat s <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3edee-393">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="3edee-394">Portu SerialPort pro Linux</span><span class="sxs-lookup"><span data-stu-id="3edee-394">SerialPort for Linux</span></span>

<span data-ttu-id="3edee-395">.NET Core 3,0 podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="3edee-395">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="3edee-396">Dřív se .NET Core podporuje jenom pomocí `SerialPort` systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3edee-396">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="3edee-397">Omezení paměti Docker a CGROUP</span><span class="sxs-lookup"><span data-stu-id="3edee-397">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="3edee-398">Počínaje verzí Preview 3 je používání .NET Core 3,0 na platformě Linux s nástrojem Docker lépe kompatibilní s cgroupmi omezeními paměti.</span><span class="sxs-lookup"><span data-stu-id="3edee-398">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="3edee-399">Spuštění kontejneru Docker s omezeními paměti, jako je například `docker run -m`s, se změní způsob, jakým se aplikace .NET Core chová.</span><span class="sxs-lookup"><span data-stu-id="3edee-399">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="3edee-400">Výchozí velikost haldy systému uvolňování paměti (GC): maximálně 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3edee-400">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="3edee-401">Explicitní velikost lze nastavit jako absolutní číslo nebo procento limitu CGROUP.</span><span class="sxs-lookup"><span data-stu-id="3edee-401">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="3edee-402">Minimální velikost rezervovaného segmentu na haldě GC je 16 MB.</span><span class="sxs-lookup"><span data-stu-id="3edee-402">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="3edee-403">Tato velikost snižuje počet hald, které jsou vytvořeny na počítačích.</span><span class="sxs-lookup"><span data-stu-id="3edee-403">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="3edee-404">Menší velikosti haldy uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="3edee-404">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="3edee-405">Výchozí velikost haldy systému uvolňování paměti byla snížena z výsledku rozhraní .NET Core s menším množstvím paměti.</span><span class="sxs-lookup"><span data-stu-id="3edee-405">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="3edee-406">Tato změna se lépe zarovnává s rozpočtem přidělení 0. generace s moderními velikostmi mezipaměti procesoru.</span><span class="sxs-lookup"><span data-stu-id="3edee-406">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="3edee-407">Podpora velkokapacitních stránek uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="3edee-407">Garbage Collection Large Page support</span></span>

<span data-ttu-id="3edee-408">Velké stránky (označované také jako velké stránky na platformě Linux) jsou funkce, ve které může operační systém vytvořit oblasti paměti větší než velikost nativní stránky (často 4K), aby se zlepšil výkon aplikace požadující tyto velké stránky.</span><span class="sxs-lookup"><span data-stu-id="3edee-408">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="3edee-409">Systém uvolňování paměti se teď dá nakonfigurovat s nastavením **GCLargePages** jako funkce výslovného souhlasu, která se rozhodne přidělit velké stránky ve Windows.</span><span class="sxs-lookup"><span data-stu-id="3edee-409">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="3edee-410">Podpora GPIO pro maliny PI</span><span class="sxs-lookup"><span data-stu-id="3edee-410">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="3edee-411">Do NuGet byly vydány dva balíčky, které můžete použít pro GPIO programování:</span><span class="sxs-lookup"><span data-stu-id="3edee-411">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="3edee-412">System. Device. GPIO</span><span class="sxs-lookup"><span data-stu-id="3edee-412">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="3edee-413">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="3edee-413">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="3edee-414">Balíčky GPIO obsahují rozhraní API pro zařízení *GPIO*, *SPI*, *I2C*a *PWM* .</span><span class="sxs-lookup"><span data-stu-id="3edee-414">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="3edee-415">Balíček vazeb IoT zahrnuje vazby zařízení.</span><span class="sxs-lookup"><span data-stu-id="3edee-415">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="3edee-416">Další informace najdete v [úložišti GitHubu zařízení](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="3edee-416">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="3edee-417">Podpora ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="3edee-417">ARM64 Linux support</span></span>

<span data-ttu-id="3edee-418">.NET Core 3,0 přidává podporu pro ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="3edee-418">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="3edee-419">Primární případ použití pro ARM64 je aktuálně ve scénářích IoT.</span><span class="sxs-lookup"><span data-stu-id="3edee-419">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="3edee-420">Další informace najdete v tématu [stav .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="3edee-420">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="3edee-421">[Image Docker pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="3edee-421">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="3edee-422">**ARM64** Podpora Windows není ještě dostupná.</span><span class="sxs-lookup"><span data-stu-id="3edee-422">**ARM64** Windows support isn't yet available.</span></span>
