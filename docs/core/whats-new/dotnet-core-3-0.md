---
title: Co je nového v .NET Core 3.0
description: Přečtěte si o nových funkcích, které najdete v .NET Core 3,0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 07/25/2019
ms.openlocfilehash: 477aecec4381f26e505e88f7df38f68a85e8f70d
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012842"
---
# <a name="whats-new-in-net-core-30-preview-7"></a><span data-ttu-id="b674b-103">Co je nového v .NET Core 3,0 (Preview 7)</span><span class="sxs-lookup"><span data-stu-id="b674b-103">What's new in .NET Core 3.0 (Preview 7)</span></span>

<span data-ttu-id="b674b-104">Tento článek popisuje, co je v .NET Core 3,0 (v Preview 7) novinkou.</span><span class="sxs-lookup"><span data-stu-id="b674b-104">This article describes what is new in .NET Core 3.0 (through preview 7).</span></span> <span data-ttu-id="b674b-105">Jedním z největších vylepšení je podpora desktopových aplikací pro Windows (jenom Windows).</span><span class="sxs-lookup"><span data-stu-id="b674b-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="b674b-106">Pomocí aplikace .NET Core 3,0 SDK desktopové plochy systému Windows můžete přenést model Windows Forms aplikace a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="b674b-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="b674b-107">Aby bylo jasné, že je komponenta Desktop systému Windows podporována a je součástí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b674b-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="b674b-108">Další informace najdete v části [Windows Desktop](#windows-desktop) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="b674b-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="b674b-109">.NET Core 3,0 přidává podporu pro C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="b674b-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="b674b-110">Důrazně doporučujeme použít [nejnovější verzi sady Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview)nebo Visual Studio Code s rozšířením OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="b674b-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="b674b-111">[Stáhněte si a začněte používat .NET Core 3,0 Preview 7](https://aka.ms/netcore3download) hned v systémech Windows, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="b674b-111">[Download and get started with .NET Core 3.0 preview 7](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="b674b-112">Další informace o jednotlivých vydaných verzích Preview najdete v následujících oznámeních:</span><span class="sxs-lookup"><span data-stu-id="b674b-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="b674b-113">Oznámení .NET Core 3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="b674b-113">.NET Core 3.0 Preview 7 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)
- [<span data-ttu-id="b674b-114">Oznámení .NET Core 3,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="b674b-114">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="b674b-115">Oznámení .NET Core 3,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="b674b-115">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="b674b-116">Oznámení .NET Core 3,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="b674b-116">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="b674b-117">Oznámení .NET Core 3,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="b674b-117">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="b674b-118">Oznámení .NET Core 3,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="b674b-118">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="b674b-119">Oznámení .NET Core 3,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="b674b-119">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="production-supported-preview"></a><span data-ttu-id="b674b-120">Verze Preview podporovaná v produkci</span><span class="sxs-lookup"><span data-stu-id="b674b-120">Production supported preview</span></span>

<span data-ttu-id="b674b-121">.NET Core Preview 7 se považuje za produkční, které je připravené Microsoftem a je plně podporovaná.</span><span class="sxs-lookup"><span data-stu-id="b674b-121">.NET Core Preview 7 is considered production ready by Microsoft and is fully supported.</span></span> <span data-ttu-id="b674b-122">Počínaje verzí Preview 7 se vydání verzí zaměřuje na polštinu .NET Core 3,0 místo přidávání nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="b674b-122">Starting with preview 7, releases will focus on polishing .NET Core 3.0 instead of adding new features.</span></span> <span data-ttu-id="b674b-123">Další informace o tom, co se změnilo ve verzi Preview 7, najdete v [oznámení verze Preview 7](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/).</span><span class="sxs-lookup"><span data-stu-id="b674b-123">For more information about what has changed in preview 7, see the [preview 7 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/).</span></span>

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="b674b-124">.NET Core SDK Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="b674b-124">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="b674b-125">Instalační program MSI pro Windows se od verze .NET Core 3,0 změnil.</span><span class="sxs-lookup"><span data-stu-id="b674b-125">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="b674b-126">Instalační programy sady SDK teď upgradují verze sady SDK, které jsou na místě.</span><span class="sxs-lookup"><span data-stu-id="b674b-126">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="b674b-127">Pásma funkcí jsou definována ve *stovkách* v oddílu *patch* tohoto čísla verze.</span><span class="sxs-lookup"><span data-stu-id="b674b-127">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="b674b-128">Například **3,0. _101_**  a **3,0. _201_**  jsou verze ve dvou různých pruzích funkcí během **3,0. _101_**  a **3,0. _199_**  jsou ve stejném pásmu funkcí.</span><span class="sxs-lookup"><span data-stu-id="b674b-128">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="b674b-129">A při .NET Core SDK **3,0. _101_**  je nainstalováno, .NET Core SDK **3,0. _100_**  se odebere z počítače, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="b674b-129">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="b674b-130">Při .NET Core SDK **3,0. _200_**  je nainstalována na stejném počítači .NET Core SDK **3,0. _101_**  nebude odebráno.</span><span class="sxs-lookup"><span data-stu-id="b674b-130">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="b674b-131">Další informace o tom, jak se správou verzí, najdete v tématu Přehled toho, [jak je verze .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="b674b-131">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="b674b-132">C#8,0 Preview</span><span class="sxs-lookup"><span data-stu-id="b674b-132">C# 8.0 preview</span></span>

<span data-ttu-id="b674b-133">.NET Core 3,0 podporuje C# 8 Preview.</span><span class="sxs-lookup"><span data-stu-id="b674b-133">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="b674b-134">Další informace o C# funkcích 8,0 najdete v tématu [co je nového v C# 8,0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="b674b-134">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="b674b-135">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="b674b-135">.NET Standard 2.1</span></span>

<span data-ttu-id="b674b-136">I když .NET Core 3,0 podporuje **.NET Standard 2,1**, výchozí `dotnet new classlib` šablona vygeneruje projekt, který cílí na **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="b674b-136">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="b674b-137">Chcete-li cílit na **.NET Standard 2,1**, upravte soubor projektu a `TargetFramework` změňte vlastnost `netstandard2.1`na:</span><span class="sxs-lookup"><span data-stu-id="b674b-137">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="b674b-138">Pokud používáte Visual Studio, budete potřebovat [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), protože Visual Studio 2017 nepodporuje **.NET Standard 2,1** nebo **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="b674b-138">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="b674b-139">Vylepšená rozhraní API verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="b674b-139">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="b674b-140">Počínaje rozhraním .NET Core 3,0 verze rozhraní API poskytovaná pomocí .NET Core nyní vrátí očekávané informace.</span><span class="sxs-lookup"><span data-stu-id="b674b-140">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="b674b-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b674b-141">For example:</span></span>

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
> <span data-ttu-id="b674b-142">Zásadní změna.</span><span class="sxs-lookup"><span data-stu-id="b674b-142">Breaking change.</span></span> <span data-ttu-id="b674b-143">To je technicky zásadní změna, protože se změnilo schéma správy verzí.</span><span class="sxs-lookup"><span data-stu-id="b674b-143">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="b674b-144">Vnitřní objekty závislé na platformě .NET</span><span class="sxs-lookup"><span data-stu-id="b674b-144">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="b674b-145">Byla přidána rozhraní API, která umožňují přístup k určitým pokynům pro procesor orientovaným na výkon, jako jsou **SIMD** nebo sady instrukcí pro **manipulaci** .</span><span class="sxs-lookup"><span data-stu-id="b674b-145">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="b674b-146">Tyto pokyny vám pomůžou dosáhnout výrazného zlepšení výkonu v některých scénářích, jako je efektivní zpracování dat paralelně.</span><span class="sxs-lookup"><span data-stu-id="b674b-146">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="b674b-147">V případě potřeby se pomocí těchto pokynů Vylepšete knihovny .NET, aby se zlepšil výkon.</span><span class="sxs-lookup"><span data-stu-id="b674b-147">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="b674b-148">Další informace najdete v tématu věnovaném [vnitřním procesorům platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="b674b-148">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="b674b-149">Výchozí spustitelné soubory</span><span class="sxs-lookup"><span data-stu-id="b674b-149">Default executables</span></span>

<span data-ttu-id="b674b-150">.NET Core teď ve výchozím nastavení vytváří [spustitelné soubory závislé na rozhraní](../deploying/index.md#framework-dependent-executables-fde) .</span><span class="sxs-lookup"><span data-stu-id="b674b-150">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="b674b-151">Toto chování je nové u aplikací, které používají globálně nainstalovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b674b-151">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="b674b-152">Dříve mohli pouze [samostatně nasazená nasazení](../deploying/index.md#self-contained-deployments-scd) vyvolat spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="b674b-152">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="b674b-153">Během `dotnet build` nebo`dotnet publish`se vytvoří spustitelný soubor, který odpovídá prostředí a platformě používané sady SDK.</span><span class="sxs-lookup"><span data-stu-id="b674b-153">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="b674b-154">Pomocí těchto spustitelných souborů můžete očekávat stejné věci jako jiné nativní spustitelné soubory, jako například:</span><span class="sxs-lookup"><span data-stu-id="b674b-154">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="b674b-155">Můžete dvakrát kliknout na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="b674b-155">You can double-click on the executable.</span></span>
* <span data-ttu-id="b674b-156">Aplikaci můžete spustit z příkazového řádku přímo, například `myapp.exe` ve Windows, a `./myapp` v systémech Linux a MacOS.</span><span class="sxs-lookup"><span data-stu-id="b674b-156">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="b674b-157">Spustitelné soubory s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="b674b-157">Single-file executables</span></span>

<span data-ttu-id="b674b-158">`dotnet publish` Příkaz podporuje balení vaší aplikace do spustitelného souboru specifického pro jednotlivé platformy.</span><span class="sxs-lookup"><span data-stu-id="b674b-158">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="b674b-159">Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativních), které jsou nutné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b674b-159">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="b674b-160">Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru buildu.</span><span class="sxs-lookup"><span data-stu-id="b674b-160">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="b674b-161">Spuštění je rychlejší, když aplikaci znovu spustíte.</span><span class="sxs-lookup"><span data-stu-id="b674b-161">Startup is faster when the application is run again.</span></span> <span data-ttu-id="b674b-162">Pokud se nepoužila nová verze, aplikace se už nebude muset extrahovat druhou dobu.</span><span class="sxs-lookup"><span data-stu-id="b674b-162">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="b674b-163">Chcete-li publikovat soubor s jedním souborem, nastavte `PublishSingleFile` v projektu nebo na příkazovém řádku `dotnet publish` pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="b674b-163">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="b674b-164">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b674b-164">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="b674b-165">Další informace o publikování v jednom souboru najdete v [dokumentu návrhu sady prostředků s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="b674b-165">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="b674b-166">Propojení sestavení</span><span class="sxs-lookup"><span data-stu-id="b674b-166">Assembly linking</span></span>

<span data-ttu-id="b674b-167">Sada .NET Core 3,0 SDK je dodávána s nástrojem, který umožňuje zmenšit velikost aplikací analýzou IL a oříznutím nepoužívaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="b674b-167">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="b674b-168">Samostatné aplikace zahrnují vše potřebné ke spuštění kódu, aniž by bylo nutné nainstalovat rozhraní .NET do hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="b674b-168">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="b674b-169">Ale hodně, kolikrát aplikace jenom vyžaduje malou podmnožinu rozhraní, a další nepoužívané knihovny by se daly odebrat.</span><span class="sxs-lookup"><span data-stu-id="b674b-169">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="b674b-170">Rozhraní .NET Core nyní obsahuje nastavení, které bude používat nástroj [linkeru Il](https://github.com/mono/linker) ke kontrole Il vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b674b-170">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="b674b-171">Tento nástroj zjistí, jaký kód je požadován, a poté ořízne nepoužívané knihovny.</span><span class="sxs-lookup"><span data-stu-id="b674b-171">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="b674b-172">Tento nástroj může významně snížit velikost nasazení některých aplikací.</span><span class="sxs-lookup"><span data-stu-id="b674b-172">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="b674b-173">Chcete-li tento nástroj povolit, `<PublishTrimmed>` přidejte do projektu nastavení a publikujte samostatně uzavřenou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="b674b-173">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="b674b-174">Příklad: základní šablona projektu "Hello World", která je součástí, je-li publikována, má velikost přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="b674b-174">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="b674b-175">Pomocí `<PublishTrimmed>`této velikosti se velikost zmenší na přibližně 30 MB.</span><span class="sxs-lookup"><span data-stu-id="b674b-175">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="b674b-176">Je důležité vzít v úvahu, že aplikace nebo architektury (včetně ASP.NET Core a WPF), které používají reflexi nebo související dynamické funkce, budou často přerušit při oříznutí.</span><span class="sxs-lookup"><span data-stu-id="b674b-176">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="b674b-177">K tomuto zlomku dochází, protože linker neví o tomto dynamickém chování a nemůže určit, které typy rozhraní jsou pro reflexi vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="b674b-177">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="b674b-178">Nástroj linkeru IL se dá nakonfigurovat tak, aby se na tento scénář dozvěděl.</span><span class="sxs-lookup"><span data-stu-id="b674b-178">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="b674b-179">Nad všemi ostatními nezapomeňte aplikaci otestovat po jejím oříznutí.</span><span class="sxs-lookup"><span data-stu-id="b674b-179">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="b674b-180">Další informace o nástroji linkeru IL naleznete v [dokumentaci](https://aka.ms/dotnet-illink) nebo v úložišti [mono/linker]( https://github.com/mono/linker) .</span><span class="sxs-lookup"><span data-stu-id="b674b-180">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="b674b-181">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="b674b-181">Tiered compilation</span></span>

<span data-ttu-id="b674b-182">[Vrstvená kompilace](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) je ve výchozím nastavení zapnuté pomocí .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b674b-182">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="b674b-183">Tato funkce umožňuje modulu runtime pružně použít kompilátor JIT (just-in-time) a získat tak lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="b674b-183">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="b674b-184">Hlavní výhodou TC je povolit (znovu) jitting metody s úrovní nižší kvality, ale rychleji nebo s vyšší kvalitou, ale nižší úrovní.</span><span class="sxs-lookup"><span data-stu-id="b674b-184">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="b674b-185">To pomáhá zvýšit výkon aplikace, protože projde různými fázemi provádění, od spuštění po ustáleném stavu.</span><span class="sxs-lookup"><span data-stu-id="b674b-185">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="b674b-186">To se liší od přístupu bez použití TC, kde je každá metoda zkompilována jedním způsobem (stejně jako vysoká úroveň kvality), která je pro výkon při spuštění posunuta na ustálený stav.</span><span class="sxs-lookup"><span data-stu-id="b674b-186">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="b674b-187">Chcete-li povolit rychlou JIT (zpracovaných kompilátorem JIT kód vrstvy 0), použijte toto nastavení v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="b674b-187">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="b674b-188">Chcete-li úplně zakázat použití TC, použijte toto nastavení v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="b674b-188">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="b674b-189">ReadyToRun image</span><span class="sxs-lookup"><span data-stu-id="b674b-189">ReadyToRun images</span></span>

<span data-ttu-id="b674b-190">Můžete zlepšit čas spuštění aplikace .NET Core kompilováním sestavení aplikace jako formátu ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="b674b-190">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="b674b-191">R2R je forma kompilace v čase před zahájením (AOT).</span><span class="sxs-lookup"><span data-stu-id="b674b-191">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="b674b-192">R2R binární soubory zlepšují výkon při spuštění tím, že snižují množství práce, které kompilátor JIT (just-in-time) potřebuje k tomu, aby se vaše aplikace načítají.</span><span class="sxs-lookup"><span data-stu-id="b674b-192">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="b674b-193">Binární soubory obsahují podobný nativní kód v porovnání s tím, co by kompilátor JIT vytvořil.</span><span class="sxs-lookup"><span data-stu-id="b674b-193">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="b674b-194">R2R binární soubory jsou však větší, protože obsahují kód pro mezilehlé jazyky (IL), který je stále potřeba pro některé scénáře, a nativní verzi stejného kódu.</span><span class="sxs-lookup"><span data-stu-id="b674b-194">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="b674b-195">R2R je k dispozici pouze v případě, že publikujete samostatnou aplikaci, která cílí na konkrétní běhové prostředí (RID), jako je Linux x64 nebo Windows x64.</span><span class="sxs-lookup"><span data-stu-id="b674b-195">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="b674b-196">Chcete-li zkompilovat projekt jako ReadyToRun, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="b674b-196">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="b674b-197">`<PublishReadyToRun>` Přidat nastavení do projektu</span><span class="sxs-lookup"><span data-stu-id="b674b-197">Add the `<PublishReadyToRun>` setting to your project</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="b674b-198">Publikujte samostatně uzavřenou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b674b-198">Publish a self-contained app.</span></span> <span data-ttu-id="b674b-199">Tento příkaz například vytvoří samostatnou aplikaci pro 64 verzi Windows:</span><span class="sxs-lookup"><span data-stu-id="b674b-199">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```console
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="b674b-200">Omezení pro různé platformy a architektury</span><span class="sxs-lookup"><span data-stu-id="b674b-200">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="b674b-201">Kompilátor ReadyToRun v současné době nepodporuje cílení na více platforem.</span><span class="sxs-lookup"><span data-stu-id="b674b-201">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="b674b-202">Je nutné kompilovat na daném cíli.</span><span class="sxs-lookup"><span data-stu-id="b674b-202">You must compile on a given target.</span></span> <span data-ttu-id="b674b-203">Například pokud chcete image R2R pro Windows x64, musíte v tomto prostředí spustit příkaz publikovat.</span><span class="sxs-lookup"><span data-stu-id="b674b-203">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="b674b-204">Výjimky pro cílení na více platforem:</span><span class="sxs-lookup"><span data-stu-id="b674b-204">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="b674b-205">Systém Windows x64 lze použít ke kompilaci imagí Windows ARM32, ARM64 a x86.</span><span class="sxs-lookup"><span data-stu-id="b674b-205">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="b674b-206">K kompilování imagí Windows ARM32 lze použít systém Windows x86.</span><span class="sxs-lookup"><span data-stu-id="b674b-206">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="b674b-207">Linux x64 lze použít ke kompilaci imagí ARM32 a ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="b674b-207">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="b674b-208">Sestavení kopíruje závislosti</span><span class="sxs-lookup"><span data-stu-id="b674b-208">Build copies dependencies</span></span>

<span data-ttu-id="b674b-209">`dotnet build` Příkaz nyní kopíruje závislosti NuGet pro vaši aplikaci z mezipaměti NuGet do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="b674b-209">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="b674b-210">Dříve se závislosti zkopírovaly jenom jako součást `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="b674b-210">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="b674b-211">Existují některé operace, jako je propojování a publikování stránek Razor, které budou nadále vyžadovat publikování.</span><span class="sxs-lookup"><span data-stu-id="b674b-211">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="b674b-212">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="b674b-212">Local tools</span></span>

<span data-ttu-id="b674b-213">.NET Core 3,0 zavádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="b674b-213">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="b674b-214">Místní nástroje jsou podobné [globálním nástrojům](../tools/global-tools.md) , ale jsou přidruženy k určitému umístění na disku.</span><span class="sxs-lookup"><span data-stu-id="b674b-214">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="b674b-215">Místní nástroje nejsou globálně dostupné a distribuují se jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="b674b-215">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="b674b-216">Pokud jste si vyzkoušeli místní nástroje v rozhraní .NET Core 3,0 Preview 1 `dotnet tool restore` , `dotnet tool install`jako je třeba spuštění nebo, odstraňte složku mezipaměti místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="b674b-216">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="b674b-217">V opačném případě místní nástroje nebudou fungovat v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="b674b-217">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="b674b-218">Tato složka je umístěna v umístění:</span><span class="sxs-lookup"><span data-stu-id="b674b-218">This folder is located at:</span></span>
>
> <span data-ttu-id="b674b-219">V macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="b674b-219">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="b674b-220">Ve Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="b674b-220">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="b674b-221">Místní nástroje spoléhají na název `dotnet-tools.json` souboru manifestu v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="b674b-221">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="b674b-222">Tento soubor manifestu definuje nástroje, které jsou k dispozici v této složce a níže.</span><span class="sxs-lookup"><span data-stu-id="b674b-222">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="b674b-223">Můžete distribuovat soubor manifestu s vaším kódem, aby bylo zajištěno, že kdokoli, kdo spolupracuje s vaším kódem, může obnovit a použít stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="b674b-223">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="b674b-224">U globálních i místních nástrojů se vyžaduje kompatibilní verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b674b-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="b674b-225">Mnoho nástrojů, které jsou aktuálně na NuGet.org Target pro .NET Core Runtime 2,1.</span><span class="sxs-lookup"><span data-stu-id="b674b-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="b674b-226">Pokud chcete tyto nástroje nainstalovat globálně nebo lokálně, budete si muset nainstalovat [modul runtime .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="b674b-226">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="b674b-227">Hlavní verze – posunutí – posun</span><span class="sxs-lookup"><span data-stu-id="b674b-227">Major-version Roll Forward</span></span>

<span data-ttu-id="b674b-228">.NET Core 3,0 zavádí funkci pro výslovný souhlas, která umožňuje aplikaci přejít na nejnovější hlavní verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b674b-228">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="b674b-229">Kromě toho bylo přidáno nové nastavení, které řídí, jak se ve vaší aplikaci aplikuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="b674b-229">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="b674b-230">Dá se nakonfigurovat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="b674b-230">This can be configured in the following ways:</span></span>

- <span data-ttu-id="b674b-231">Vlastnost souboru projektu:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="b674b-231">Project file property: `RollForward`</span></span>
- <span data-ttu-id="b674b-232">Vlastnost konfiguračního souboru modulu runtime:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="b674b-232">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="b674b-233">Proměnná prostředí:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="b674b-233">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="b674b-234">Argument příkazového řádku:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="b674b-234">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="b674b-235">Je nutné zadat jednu z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="b674b-235">One of the following values must be specified.</span></span> <span data-ttu-id="b674b-236">Pokud je nastavení vynecháno, je výchozí hodnota podverze.</span><span class="sxs-lookup"><span data-stu-id="b674b-236">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="b674b-237">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="b674b-237">**LatestPatch**</span></span>\
<span data-ttu-id="b674b-238">Vraťte se k nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="b674b-238">Roll forward to the highest patch version.</span></span> <span data-ttu-id="b674b-239">Tím se zakáže dílčí verze s posunem.</span><span class="sxs-lookup"><span data-stu-id="b674b-239">This disables minor version roll forward.</span></span>
- <span data-ttu-id="b674b-240">**Moll**</span><span class="sxs-lookup"><span data-stu-id="b674b-240">**Minor**</span></span>\
<span data-ttu-id="b674b-241">V případě, že chybí požadovaná dílčí verze, převeďte nahoru na nejnižší nižší verzi.</span><span class="sxs-lookup"><span data-stu-id="b674b-241">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="b674b-242">Pokud je k dispozici požadovaná dílčí verze, použije se zásada **LatestPatch** .</span><span class="sxs-lookup"><span data-stu-id="b674b-242">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="b674b-243">**Nejdůležitější**</span><span class="sxs-lookup"><span data-stu-id="b674b-243">**Major**</span></span>\
<span data-ttu-id="b674b-244">Pokud chybí požadovaná hlavní verze, převeďte ji nahoru na nejnižší nejvyšší hlavní verzi a nejnižší podverzi.</span><span class="sxs-lookup"><span data-stu-id="b674b-244">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="b674b-245">Pokud je k dispozici požadovaná hlavní verze, použije se **vedlejší** zásada.</span><span class="sxs-lookup"><span data-stu-id="b674b-245">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="b674b-246">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="b674b-246">**LatestMinor**</span></span>\
<span data-ttu-id="b674b-247">Převeďte do nejvyšší dílčí verze, i když je k dispozici požadovaná dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="b674b-247">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="b674b-248">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="b674b-248">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="b674b-249">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="b674b-249">**LatestMajor**</span></span>\
<span data-ttu-id="b674b-250">Převeďte do nejvyšší hlavní a nejvyšší dílčí verze, a to i v případě, že je k dispozici požadovaná hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="b674b-250">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="b674b-251">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="b674b-251">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="b674b-252">**Dezaktivovat**</span><span class="sxs-lookup"><span data-stu-id="b674b-252">**Disable**</span></span>\
<span data-ttu-id="b674b-253">Nezadávejte vše.</span><span class="sxs-lookup"><span data-stu-id="b674b-253">Don't roll forward.</span></span> <span data-ttu-id="b674b-254">Vytvoří se jenom vazba na určenou verzi.</span><span class="sxs-lookup"><span data-stu-id="b674b-254">Only bind to specified version.</span></span> <span data-ttu-id="b674b-255">Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám.</span><span class="sxs-lookup"><span data-stu-id="b674b-255">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="b674b-256">Tato hodnota se doporučuje jenom pro testování.</span><span class="sxs-lookup"><span data-stu-id="b674b-256">This value is only recommended for testing.</span></span>

<span data-ttu-id="b674b-257">Kromě nastavení **Zakázat** bude pro všechna nastavení použita nejvyšší dostupná verze opravy.</span><span class="sxs-lookup"><span data-stu-id="b674b-257">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="b674b-258">Plocha Windows</span><span class="sxs-lookup"><span data-stu-id="b674b-258">Windows desktop</span></span>

<span data-ttu-id="b674b-259">.NET Core 3,0 podporuje desktopové aplikace Windows pomocí Windows Presentation Foundation (WPF) a model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b674b-259">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="b674b-260">Tyto architektury také podporují použití moderních ovládacích prvků a Fluent stylování z knihovny XAML uživatelského rozhraní systému Windows (WinUI) přes [ostrovy XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="b674b-260">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="b674b-261">Součást Desktop systému Windows je součástí sady Windows .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="b674b-261">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="b674b-262">Novou aplikaci WPF nebo model Windows Forms můžete vytvořit pomocí následujících `dotnet` příkazů:</span><span class="sxs-lookup"><span data-stu-id="b674b-262">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="b674b-263">Visual Studio 2019 přidává **nové šablony projektů** pro .net Core 3,0 model Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="b674b-263">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="b674b-264">Další informace o tom, jak přenést existující aplikaci .NET Framework, naleznete v tématu [port WPF Projects](../porting/wpf.md) and [port model Windows Forms Projects](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="b674b-264">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="b674b-265">Komponenty s podporou modelu COM – Desktop Windows</span><span class="sxs-lookup"><span data-stu-id="b674b-265">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="b674b-266">Ve Windows teď můžete vytvářet spravované komponenty, které lze volat v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b674b-266">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="b674b-267">Tato možnost je zásadní pro použití .NET Core s modely doplňku COM a také k zajištění parity s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b674b-267">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="b674b-268">Na rozdíl od .NET Framework, kde se *Knihovna Mscoree. dll* použila jako server com, .NET Core při sestavování komponenty com přidá nativní spouštěcí knihovnu DLL do adresáře *bin* .</span><span class="sxs-lookup"><span data-stu-id="b674b-268">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="b674b-269">Příklad vytvoření komponenty modelu COM a její využití naleznete v [ukázce modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="b674b-269">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="b674b-270">Nasazení MSIX – Desktop Windows</span><span class="sxs-lookup"><span data-stu-id="b674b-270">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="b674b-271">[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b674b-271">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="b674b-272">Dá se použít k nasazení desktopových aplikací .NET Core 3,0 do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b674b-272">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="b674b-273">[Projekt pro balení aplikace pro systém Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), který je k dispozici v aplikaci Visual Studio 2019, umožňuje vytvářet balíčky MSIX pomocí aplikací .NET Core s využitím [vlastních součástí](../deploying/index.md#self-contained-deployments-scd) .</span><span class="sxs-lookup"><span data-stu-id="b674b-273">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="b674b-274">Soubor projektu .NET Core musí určovat podporované běhové moduly ve `<RuntimeIdentifiers>` vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b674b-274">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="b674b-275">HighDPI WinForms</span><span class="sxs-lookup"><span data-stu-id="b674b-275">WinForms HighDPI</span></span>

<span data-ttu-id="b674b-276">Aplikace .NET Core model Windows Forms můžou nastavit režim s vysokým <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>rozlišením DPI pomocí.</span><span class="sxs-lookup"><span data-stu-id="b674b-276">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b674b-277">Metoda nastaví odpovídající režim vysoké úrovně dpi, pokud nastavení nebylo nastaveno jiným způsobem, jako `App.Manifest` je `Application.Run`nebo P/Invoke. `SetHighDpiMode`</span><span class="sxs-lookup"><span data-stu-id="b674b-277">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="b674b-278">Možné `highDpiMode` hodnoty, jak je vyjádřené <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> výčtem:</span><span class="sxs-lookup"><span data-stu-id="b674b-278">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="b674b-279">Další informace o režimech vysokého rozlišení DPI najdete v tématu [vývoj desktopových aplikací s vysokým rozlišením v systému Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="b674b-279">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="b674b-280">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="b674b-280">Ranges and indices</span></span>

<span data-ttu-id="b674b-281">Nový <xref:System.Index?displayProperty=nameWithType> typ lze použít k indexování.</span><span class="sxs-lookup"><span data-stu-id="b674b-281">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="b674b-282">Můžete vytvořit jednu z `int` těchto počtů od začátku nebo s operátorem prefix `^` (C#), který se počítá od konce:</span><span class="sxs-lookup"><span data-stu-id="b674b-282">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="b674b-283">Je zde také <xref:System.Range?displayProperty=nameWithType> typ, který se skládá ze dvou `Index` hodnot, jeden pro začátek a jeden pro konec a `x..y` lze jej zapsat s výrazem rozsahu (C#).</span><span class="sxs-lookup"><span data-stu-id="b674b-283">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="b674b-284">Pak můžete indexovat pomocí `Range`, který vytváří řez:</span><span class="sxs-lookup"><span data-stu-id="b674b-284">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="b674b-285">Další informace najdete v [kurzu rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="b674b-285">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

## <a name="async-streams"></a><span data-ttu-id="b674b-286">Asynchronní streamy</span><span class="sxs-lookup"><span data-stu-id="b674b-286">Async streams</span></span>

<span data-ttu-id="b674b-287">Typ je nová asynchronní <xref:System.Collections.Generic.IEnumerable%601>verze. <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="b674b-287">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b674b-288">Jazyk vám umožní `await foreach` `IAsyncEnumerable<T>` využít jejich prvky a využít `yield return` je k vytváření prvků.</span><span class="sxs-lookup"><span data-stu-id="b674b-288">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="b674b-289">Následující příklad ukazuje produkci a spotřebu asynchronních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="b674b-289">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="b674b-290">Příkaz je asynchronní a sám používá `yield return` k tvorbě asynchronního datového proudu pro volající. `foreach`</span><span class="sxs-lookup"><span data-stu-id="b674b-290">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="b674b-291">Tento vzor (použití `yield return`) je doporučeným modelem pro vytváření asynchronních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="b674b-291">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="b674b-292">Kromě `await foreach`toho je možné také vytvořit asynchronní iterátory, například iterátor, který `IAsyncEnumerable/IAsyncEnumerator` vrátí `yield` , který můžete i `await` v.</span><span class="sxs-lookup"><span data-stu-id="b674b-292">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="b674b-293">Pro objekty, které je třeba uvolnit, můžete použít `IAsyncDisposable`, které BCL různé typy, `Stream` například a `Timer`.</span><span class="sxs-lookup"><span data-stu-id="b674b-293">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="b674b-294">Další informace najdete v [kurzu asynchronní streamy](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="b674b-294">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="b674b-295">Vylepšení standardu IEEE s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="b674b-295">IEEE Floating-point improvements</span></span>

<span data-ttu-id="b674b-296">Rozhraní API s plovoucí desetinnou čárkou se aktualizují tak, aby odpovídalo [revizi IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="b674b-296">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="b674b-297">Cílem těchto změn je vystavit všechny **požadované** operace a zajistit, aby byly vyhovující požadavkům standardu IEEE. Další informace o vylepšeních s plovoucí desetinnou čárkou naleznete v příspěvku na blogu [.NET Core 3,0 v oblasti analýzy a formátování plovoucí desetinné](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) čárky.</span><span class="sxs-lookup"><span data-stu-id="b674b-297">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="b674b-298">Mezi aktualizace pro analýzu a formátování patří:</span><span class="sxs-lookup"><span data-stu-id="b674b-298">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="b674b-299">Správně Analyzujte a zaokrouhlujte vstupy libovolné délky.</span><span class="sxs-lookup"><span data-stu-id="b674b-299">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="b674b-300">Správně Analyzujte a formátujete záporné hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="b674b-300">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="b674b-301">Správně analyzovat `Infinity` a `NaN` provést kontrolu bez rozlišení velkých a malých písmen a povolit volitelnou předchozí `+` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b674b-301">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="b674b-302">Mezi <xref:System.Math?displayProperty=nameWithType> nová rozhraní API patří:</span><span class="sxs-lookup"><span data-stu-id="b674b-302">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="b674b-303"><xref:System.Math.BitIncrement(System.Double)>ani<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="b674b-303"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="b674b-304">Odpovídá operacím `nextDown` IEEE a.`nextUp`</span><span class="sxs-lookup"><span data-stu-id="b674b-304">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="b674b-305">Vrátí nejmenší číslo s plovoucí desetinnou čárkou, které porovná větší nebo menší než vstup (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="b674b-305">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="b674b-306">Například `Math.BitIncrement(0.0)` vrátí `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="b674b-306">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="b674b-307"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>ani<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="b674b-307"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="b674b-308">Odpovídá operacím `minNumMag` IEEE a,vracíhodnotu,kterájevětšínebomenšívrozsahudvouvstupů(vuvedenémpořadí).`maxNumMag`</span><span class="sxs-lookup"><span data-stu-id="b674b-308">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="b674b-309">Například `Math.MaxMagnitude(2.0, -3.0)` vrátí `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="b674b-309">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="b674b-310">Odpovídá operaci `logB` IEEE, která vrací celočíselnou hodnotu, vrátí protokol integrálního protokolu Base-2 vstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="b674b-310">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="b674b-311">Tato metoda je prakticky stejná jako `floor(log2(x))`, ale byla provedena s minimální chybou zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="b674b-311">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="b674b-312">Odpovídá operaci `x * pow(2, n)`IEEE, která přebírá celočíselnou hodnotu, vrátí ji efektivně, ale provede minimální chybu zaokrouhlení. `scaleB`</span><span class="sxs-lookup"><span data-stu-id="b674b-312">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="b674b-313">Odpovídá operaci `log2` IEEE, vrátí logaritmus o základu 2.</span><span class="sxs-lookup"><span data-stu-id="b674b-313">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="b674b-314">Minimalizuje chybu zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="b674b-314">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="b674b-315">Odpovídá operaci `fma` IEEE, provádí přidaný násobek.</span><span class="sxs-lookup"><span data-stu-id="b674b-315">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="b674b-316">To znamená, že se `(x * y) + z` jedná o jedinou operaci, čímž se minimalizuje chyba zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="b674b-316">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="b674b-317">Příkladem může být `FusedMultiplyAdd(1e308, 2.0, -1e308)` vrácení. `1e308`</span><span class="sxs-lookup"><span data-stu-id="b674b-317">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="b674b-318">Funkce Regular `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="b674b-318">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="b674b-319">Odpovídá operaci `x`IEEE, vrací hodnotu, `y`ale s znaménkem. `copySign`</span><span class="sxs-lookup"><span data-stu-id="b674b-319">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="b674b-320">Rychlá integrovaná podpora JSON</span><span class="sxs-lookup"><span data-stu-id="b674b-320">Fast built-in JSON support</span></span>

<span data-ttu-id="b674b-321">Uživatelé rozhraní .NET mají převážně na [**JSON.NET**](https://www.newtonsoft.com/json) a další oblíbené knihovny JSON, které budou mít i nadále dobré možnosti.</span><span class="sxs-lookup"><span data-stu-id="b674b-321">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="b674b-322">**JSON.NET** používá řetězce .NET jako základní datový typ, který je v digestoři UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b674b-322">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="b674b-323">Nová integrovaná podpora JSON je vysoce výkonná, nízká alokace a založená na `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="b674b-323">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="b674b-324">Do .NET Core 3,0 <xref:System.Text.Json?displayProperty=nameWithType> oboru názvů se přidaly tři nové hlavní typy související s JSON.</span><span class="sxs-lookup"><span data-stu-id="b674b-324">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b674b-325">Tyto typy *ještě* nepodporují serializaci a deserializaci objektu CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="b674b-325">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="b674b-326">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="b674b-326">Utf8JsonReader</span></span>

<span data-ttu-id="b674b-327"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>je pro text JSON s kódováním UTF-8 s vysokým výkonem k dispozici vysoce výkonné a nízké přidělení, načtený z `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="b674b-327"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="b674b-328">`Utf8JsonReader` Je základní typ nízké úrovně, který lze použít k sestavení vlastních analyzátorů a deserializace.</span><span class="sxs-lookup"><span data-stu-id="b674b-328">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="b674b-329">Čtení prostřednictvím datové části JSON pomocí nového `Utf8JsonReader` je 2x rychlejší než použití čtecího zařízení z **JSON.NET**.</span><span class="sxs-lookup"><span data-stu-id="b674b-329">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="b674b-330">Nepřiřazuje se, dokud nebudete muset actualize tokeny JSON jako řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="b674b-330">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="b674b-331">Tady je příklad, jak číst pomocí souboru [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) vytvořeného pomocí Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="b674b-331">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="b674b-332">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="b674b-332">Utf8JsonWriter</span></span>

<span data-ttu-id="b674b-333"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>poskytuje vysoce výkonný a neuložený v mezipaměti, a to jenom pro psaní textu JSON v kódování UTF-8 ze běžných typů .NET, `String`jako `Int32`jsou, `DateTime`a.</span><span class="sxs-lookup"><span data-stu-id="b674b-333"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="b674b-334">Podobně jako čtenář je modul pro zápis základní typ nízké úrovně, který lze použít k vytvoření vlastních serializátorů.</span><span class="sxs-lookup"><span data-stu-id="b674b-334">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="b674b-335">Zápis datové části JSON pomocí nového `Utf8JsonWriter` je 30-80% rychlejší než použití zapisovače z **JSON.NET** a nepřiřazuje.</span><span class="sxs-lookup"><span data-stu-id="b674b-335">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="b674b-336">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="b674b-336">JsonDocument</span></span>

<span data-ttu-id="b674b-337"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>je postaven na začátku `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="b674b-337"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="b674b-338">`JsonDocument` Poskytuje možnost analyzovat data JSON a sestavit model DOM (Document Object Model) (DOM) jen pro čtení, které se dají dotazovat na podporu náhodného přístupu a výčtu.</span><span class="sxs-lookup"><span data-stu-id="b674b-338">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="b674b-339">Prvky JSON, které tvoří data, mohou být přístupné prostřednictvím <xref:System.Text.Json.JsonElement> typu, který je zveřejněn `JsonDocument` jako vlastnost s názvem `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="b674b-339">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="b674b-340">`JsonElement` Obsahuje enumerátory pole a objektu JSON spolu s rozhraními API pro převod textu JSON na běžné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="b674b-340">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="b674b-341">Analýza typické datové části JSON a přístup ke všem jeho členům pomocí `JsonDocument` je 2 – 3x rychlejší než **JSON.NET** s malým přidělením dat, která mají rozumně velikost (to znamená < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="b674b-341">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="b674b-342">Zde je ukázkové použití `JsonDocument` a `JsonElement` , které lze použít jako výchozí bod:</span><span class="sxs-lookup"><span data-stu-id="b674b-342">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

<span data-ttu-id="b674b-343">Tady je příklad C# 8,0 souboru [Launch. JSON](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) vytvořeného pomocí Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="b674b-343">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="b674b-344">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="b674b-344">JsonSerializer</span></span>

<span data-ttu-id="b674b-345"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>je postaven na začátku <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter> k poskytnutí rychlé možnosti serializace paměti při práci s dokumenty a fragmenty JSON.</span><span class="sxs-lookup"><span data-stu-id="b674b-345"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast, low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="b674b-346">Tady je příklad serializace objektu do formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="b674b-346">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="b674b-347">Zde je příklad deserializace řetězce JSON na objekt.</span><span class="sxs-lookup"><span data-stu-id="b674b-347">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="b674b-348">Můžete použít řetězec JSON vyprodukovaný předchozím příkladem:</span><span class="sxs-lookup"><span data-stu-id="b674b-348">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="b674b-349">Vylepšení spolupráce</span><span class="sxs-lookup"><span data-stu-id="b674b-349">Interop improvements</span></span>

<span data-ttu-id="b674b-350">.NET Core 3,0 vylepšuje nativní interoperabilitu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b674b-350">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="b674b-351">Zadejte: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="b674b-351">Type: NativeLibrary</span></span>

<span data-ttu-id="b674b-352"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>poskytuje zapouzdření pro načtení nativní knihovny (pomocí stejné logiky zatížení jako .NET Core P/Invoke) a poskytnutí relevantních pomocných funkcí, jako je `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="b674b-352"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="b674b-353">Příklad kódu naleznete v [ukázce DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="b674b-353">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="b674b-354">Nativní spolupráce Windows</span><span class="sxs-lookup"><span data-stu-id="b674b-354">Windows Native Interop</span></span>

<span data-ttu-id="b674b-355">Systém Windows nabízí bohatě nativní rozhraní API ve formě plochých rozhraní API jazyka C, COM a WinRT.</span><span class="sxs-lookup"><span data-stu-id="b674b-355">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="b674b-356">I když .NET Core podporuje **volání**nespravovaného voláním .net Core 3,0, přidává možnost **vytvořit rozhraní API modelu COM** a **aktivovat rozhraní API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="b674b-356">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="b674b-357">Příklad kódu naleznete v [ukázce v aplikaci Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="b674b-357">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="b674b-358">Podpora HTTP/2</span><span class="sxs-lookup"><span data-stu-id="b674b-358">HTTP/2 support</span></span>

<span data-ttu-id="b674b-359"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typ podporuje protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="b674b-359">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="b674b-360">Pokud je povolený protokol HTTP/2, vyjednává se verze protokolu HTTP prostřednictvím TLS/ALPN a protokol HTTP/2 se použije, pokud se server rozhodne ho použít.</span><span class="sxs-lookup"><span data-stu-id="b674b-360">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="b674b-361">Výchozí protokol zůstává HTTP/1.1, ale protokol HTTP/2 může být povolen dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="b674b-361">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="b674b-362">Nejdřív můžete nastavit zprávu požadavku HTTP na používání HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="b674b-362">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="b674b-363">Za druhé, ve výchozím <xref:System.Net.Http.HttpClient> nastavení se dá změnit na použití HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="b674b-363">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="b674b-364">V mnoha případech, kdy vyvíjíte aplikaci, chcete použít nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="b674b-364">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="b674b-365">Pokud víte, že cílový koncový bod bude používat protokol HTTP/2, můžete zapnout nezašifrovaná připojení pro HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="b674b-365">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="b674b-366">Můžete ji zapnout nastavením `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` proměnné prostředí na `1` nebo povolením v kontextu aplikace:</span><span class="sxs-lookup"><span data-stu-id="b674b-366">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="b674b-367">TLS 1,3 & OpenSSL 1.1.1 v systému Linux</span><span class="sxs-lookup"><span data-stu-id="b674b-367">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="b674b-368">.NET Core teď využívá [podporu TLS 1,3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), pokud je dostupná v daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="b674b-368">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="b674b-369">S protokolem TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="b674b-369">With TLS 1.3:</span></span>

* <span data-ttu-id="b674b-370">Časy připojení se zlepšily s omezenou špičkou odezvy mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="b674b-370">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="b674b-371">Vylepšené zabezpečení kvůli odebrání různých zastaralých a nezabezpečených kryptografických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="b674b-371">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="b674b-372">V případě, že je k dispozici, .NET Core 3,0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**nebo **OpenSSL 1.0.2** v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="b674b-372">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="b674b-373">Pokud je k dispozici služba **OpenSSL 1.1.1** <xref:System.Net.Security.SslStream?displayProperty=nameWithType> , budou v obou <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> typech použity **protokoly TLS 1,3** (za předpokladu, že klient i server podporují protokol **TLS 1,3**).</span><span class="sxs-lookup"><span data-stu-id="b674b-373">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="b674b-374">Windows a macOS ještě nepodporují **TLS 1,3**.</span><span class="sxs-lookup"><span data-stu-id="b674b-374">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="b674b-375">Až bude podpora k dispozici, bude .NET Core 3,0 podporovat **TLS 1,3** v těchto operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="b674b-375">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="b674b-376">Následující C# příklad 8,0 ukazuje rozhraní .net Core 3,0 v Ubuntu 18,10, které <https://www.cloudflare.com>se připojuje k:</span><span class="sxs-lookup"><span data-stu-id="b674b-376">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="b674b-377">Kryptografická šifry</span><span class="sxs-lookup"><span data-stu-id="b674b-377">Cryptography ciphers</span></span>

<span data-ttu-id="b674b-378">.NET 3,0 přidává podporu pro šifry **AES-GCM** a **AES-ccm** , implementovaná <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> v <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> a v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b674b-378">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="b674b-379">Tyto algoritmy jsou jak [ověřené šifrování, tak i algoritmy AEAD (Association data)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="b674b-379">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="b674b-380">Následující kód demonstruje `AesGcm` použití šifry k šifrování a dešifrování náhodných dat.</span><span class="sxs-lookup"><span data-stu-id="b674b-380">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="b674b-381">Import/export kryptografického klíče</span><span class="sxs-lookup"><span data-stu-id="b674b-381">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="b674b-382">.NET Core 3,0 podporuje import a export asymetrických veřejných a privátních klíčů ze standardních formátů.</span><span class="sxs-lookup"><span data-stu-id="b674b-382">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="b674b-383">Nemusíte používat certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="b674b-383">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="b674b-384">Všechny typy klíčů, jako jsou *RSA*, *DSA*, *ECDSA*a *ECDiffieHellman*, podporují následující formáty:</span><span class="sxs-lookup"><span data-stu-id="b674b-384">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="b674b-385">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="b674b-385">**Public Key**</span></span>
  * <span data-ttu-id="b674b-386">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="b674b-386">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="b674b-387">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="b674b-387">**Private key**</span></span>
  * <span data-ttu-id="b674b-388">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="b674b-388">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="b674b-389">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="b674b-389">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="b674b-390">Klíče RSA podporují i:</span><span class="sxs-lookup"><span data-stu-id="b674b-390">RSA keys also support:</span></span>

* <span data-ttu-id="b674b-391">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="b674b-391">**Public Key**</span></span>
  * <span data-ttu-id="b674b-392">RSAPublicKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="b674b-392">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="b674b-393">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="b674b-393">**Private key**</span></span>
  * <span data-ttu-id="b674b-394">RSAPrivateKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="b674b-394">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="b674b-395">Metody exportu vytváří binární data kódovaná v kódování DER a metody importu očekávají stejné.</span><span class="sxs-lookup"><span data-stu-id="b674b-395">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="b674b-396">Pokud je klíč uložený v textovém formátu PEM, volající bude muset před voláním metody import kódování Base64 a dekódovat obsah.</span><span class="sxs-lookup"><span data-stu-id="b674b-396">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="b674b-397">Soubory **PKCS # 8** lze kontrolovat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> souborů a soubory **PFX a PKCS # 12** lze zkontrolovat pomocí. <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b674b-397">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b674b-398">Soubory **PFX/PKCS # 12** se můžou manipulovat s <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b674b-398">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="b674b-399">Portu SerialPort pro Linux</span><span class="sxs-lookup"><span data-stu-id="b674b-399">SerialPort for Linux</span></span>

<span data-ttu-id="b674b-400">.NET Core 3,0 podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="b674b-400">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="b674b-401">Dřív se .NET Core podporuje jenom pomocí `SerialPort` systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b674b-401">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="b674b-402">Omezení paměti Docker a CGROUP</span><span class="sxs-lookup"><span data-stu-id="b674b-402">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="b674b-403">Počínaje verzí Preview 3 je používání .NET Core 3,0 na platformě Linux s nástrojem Docker lépe kompatibilní s cgroupmi omezeními paměti.</span><span class="sxs-lookup"><span data-stu-id="b674b-403">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="b674b-404">Spuštění kontejneru Docker s omezeními paměti, jako je například `docker run -m`s, se změní způsob, jakým se aplikace .NET Core chová.</span><span class="sxs-lookup"><span data-stu-id="b674b-404">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="b674b-405">Výchozí velikost haldy systému uvolňování paměti (GC): maximálně 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b674b-405">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="b674b-406">Explicitní velikost lze nastavit jako absolutní číslo nebo procento limitu CGROUP.</span><span class="sxs-lookup"><span data-stu-id="b674b-406">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="b674b-407">Minimální velikost rezervovaného segmentu na haldě GC je 16 MB.</span><span class="sxs-lookup"><span data-stu-id="b674b-407">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="b674b-408">Tato velikost snižuje počet hald, které jsou vytvořeny na počítačích.</span><span class="sxs-lookup"><span data-stu-id="b674b-408">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="b674b-409">Menší velikosti haldy uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b674b-409">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="b674b-410">Výchozí velikost haldy systému uvolňování paměti byla snížena z výsledku rozhraní .NET Core s menším množstvím paměti.</span><span class="sxs-lookup"><span data-stu-id="b674b-410">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="b674b-411">Tato změna se lépe zarovnává s rozpočtem přidělení 0. generace s moderními velikostmi mezipaměti procesoru.</span><span class="sxs-lookup"><span data-stu-id="b674b-411">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="b674b-412">Podpora velkokapacitních stránek uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b674b-412">Garbage Collection Large Page support</span></span>

<span data-ttu-id="b674b-413">Velké stránky (označované také jako velké stránky na platformě Linux) jsou funkce, ve které může operační systém vytvořit oblasti paměti větší než velikost nativní stránky (často 4K), aby se zlepšil výkon aplikace požadující tyto velké stránky.</span><span class="sxs-lookup"><span data-stu-id="b674b-413">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="b674b-414">Systém uvolňování paměti se teď dá nakonfigurovat s nastavením **GCLargePages** jako funkce výslovného souhlasu, která se rozhodne přidělit velké stránky ve Windows.</span><span class="sxs-lookup"><span data-stu-id="b674b-414">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="b674b-415">Podpora GPIO pro maliny PI</span><span class="sxs-lookup"><span data-stu-id="b674b-415">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="b674b-416">Do NuGet byly vydány dva balíčky, které můžete použít pro GPIO programování:</span><span class="sxs-lookup"><span data-stu-id="b674b-416">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="b674b-417">System. Device. GPIO</span><span class="sxs-lookup"><span data-stu-id="b674b-417">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="b674b-418">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="b674b-418">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="b674b-419">Balíčky GPIO obsahují rozhraní API pro zařízení *GPIO*, *SPI*, *I2C*a *PWM* .</span><span class="sxs-lookup"><span data-stu-id="b674b-419">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="b674b-420">Balíček vazeb IoT zahrnuje vazby zařízení.</span><span class="sxs-lookup"><span data-stu-id="b674b-420">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="b674b-421">Další informace najdete v [úložišti GitHubu zařízení](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="b674b-421">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="b674b-422">Podpora ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="b674b-422">ARM64 Linux support</span></span>

<span data-ttu-id="b674b-423">.NET Core 3,0 přidává podporu pro ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="b674b-423">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="b674b-424">Primární případ použití pro ARM64 je aktuálně ve scénářích IoT.</span><span class="sxs-lookup"><span data-stu-id="b674b-424">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="b674b-425">Další informace najdete v tématu [stav .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="b674b-425">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="b674b-426">[Image Docker pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b674b-426">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="b674b-427">**ARM64** Podpora Windows není ještě dostupná.</span><span class="sxs-lookup"><span data-stu-id="b674b-427">**ARM64** Windows support isn't yet available.</span></span>
