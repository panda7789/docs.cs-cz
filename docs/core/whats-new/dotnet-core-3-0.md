---
title: Co je nového v .NET Core 3.0
description: Informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 06/14/2019
ms.openlocfilehash: a808a35876df8d2f6cee3c240c606b7bd979e9ee
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539277"
---
# <a name="whats-new-in-net-core-30-preview-6"></a><span data-ttu-id="f234b-103">Co je nového v .NET Core 3.0 (ve verzi Preview 6)</span><span class="sxs-lookup"><span data-stu-id="f234b-103">What's new in .NET Core 3.0 (Preview 6)</span></span>

<span data-ttu-id="f234b-104">Tento článek popisuje, co je nového v .NET Core 3.0 (prostřednictvím preview 6).</span><span class="sxs-lookup"><span data-stu-id="f234b-104">This article describes what is new in .NET Core 3.0 (through preview 6).</span></span> <span data-ttu-id="f234b-105">Jedním z největších vylepšení je podpora aplikací klasické pracovní plochy Windows (jenom Windows).</span><span class="sxs-lookup"><span data-stu-id="f234b-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="f234b-106">Pomocí sady SDK .NET Core 3.0 součásti Windows Desktop můžete port aplikace Windows Forms a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f234b-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="f234b-107">Jasno, komponenta Windows Desktop pouze podporované a součástí Windows.</span><span class="sxs-lookup"><span data-stu-id="f234b-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="f234b-108">Další informace najdete v tématu [Windows desktop](#windows-desktop) části dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="f234b-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="f234b-109">Přidává podporu pro .NET core 3.0 C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="f234b-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="f234b-110">Důrazně doporučujeme použít [nejnovější verze sady Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), nebo Visual Studio Code příponou OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="f234b-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="f234b-111">[Stáhnout a začít pracovat s .NET Core 3.0 ve verzi Preview 6](https://aka.ms/netcore3download) teď na Windows, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="f234b-111">[Download and get started with .NET Core 3.0 Preview 6](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="f234b-112">Další informace o jednotlivých verzí preview najdete v následující oznámení:</span><span class="sxs-lookup"><span data-stu-id="f234b-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="f234b-113">.NET core 3.0 ve verzi Preview 6 oznámení</span><span class="sxs-lookup"><span data-stu-id="f234b-113">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="f234b-114">.NET core 3.0 ve verzi Preview 5 oznámení</span><span class="sxs-lookup"><span data-stu-id="f234b-114">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="f234b-115">.NET core 3.0 ve verzi Preview 4 oznámení</span><span class="sxs-lookup"><span data-stu-id="f234b-115">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="f234b-116">.NET core 3.0 ve verzi Preview 3 oznámení</span><span class="sxs-lookup"><span data-stu-id="f234b-116">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="f234b-117">.NET core 3.0 ve verzi Preview 2 oznámení</span><span class="sxs-lookup"><span data-stu-id="f234b-117">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="f234b-118">.NET core 3.0 ve verzi Preview 1 oznámení</span><span class="sxs-lookup"><span data-stu-id="f234b-118">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="f234b-119">Instalační program Windows .NET core SDK</span><span class="sxs-lookup"><span data-stu-id="f234b-119">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="f234b-120">Instalační program MSI pro Windows se změnila od verze .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f234b-120">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="f234b-121">Instalační programy sady SDK se nyní upgradovat verze funkce band SDK na místě.</span><span class="sxs-lookup"><span data-stu-id="f234b-121">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="f234b-122">Funkce pruhy, které jsou definovány v *stovky* skupiny v *opravy* část čísla verze.</span><span class="sxs-lookup"><span data-stu-id="f234b-122">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="f234b-123">Například **3.0. \* 101**\* a **3.0. \* 201**\* jsou verze ve dvou různých funkčních pruhy při **3.0. \* 101**\* a **3.0. \* 199**\* jsou stejnou funkci obsluhy vzdálené správy.</span><span class="sxs-lookup"><span data-stu-id="f234b-123">For example, **3.0.\*101**\* and **3.0.\*201**\* are versions in two different feature bands while **3.0.\*101**\* and **3.0.\*199**\* are in the same feature band.</span></span> <span data-ttu-id="f234b-124">A když .NET Core SDK **3.0. \* 101**\* je nainstalovaná sada .NET Core SDK **3.0. \* 100**\* bude odebrána z počítače, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="f234b-124">And, when .NET Core SDK **3.0.\*101**\* is installed, .NET Core SDK **3.0.\*100**\* will be removed from the machine if it exists.</span></span> <span data-ttu-id="f234b-125">Když .NET Core SDK **3.0. \* 200**\* je nainstalovaná na stejném počítači, .NET Core SDK **3.0. \* 101**\* se neodeberou.</span><span class="sxs-lookup"><span data-stu-id="f234b-125">When .NET Core SDK **3.0.\*200**\* is installed on the same machine, .NET Core SDK **3.0.\*101**\* won't be removed.</span></span>

<span data-ttu-id="f234b-126">Další informace o správě verzí naleznete v tématu [přehled jak .NET Core se systémovou správou verzí](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="f234b-126">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="f234b-127">C#8.0 ve verzi preview</span><span class="sxs-lookup"><span data-stu-id="f234b-127">C# 8.0 preview</span></span>

<span data-ttu-id="f234b-128">.NET core 3.0 podporuje C# 8 ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="f234b-128">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="f234b-129">Další informace o C# 8.0 funkce, najdete v článku [co je nového v C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="f234b-129">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="f234b-130">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="f234b-130">.NET Standard 2.1</span></span>

<span data-ttu-id="f234b-131">Přestože podporuje .NET Core 3.0 **.NET Standard 2.1**, výchozí `dotnet new classlib` Šablona generuje projekt, který se zaměřuje **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="f234b-131">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="f234b-132">K cíli **.NET Standard 2.1**, upravte soubor projektu a změňte `TargetFramework` vlastnost `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="f234b-132">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="f234b-133">Pokud používáte Visual Studio, budete potřebovat [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), jak Visual Studio 2017 nepodporuje **.NET Standard 2.1** nebo **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="f234b-133">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="f234b-134">Vylepšení .NET Core verze rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f234b-134">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="f234b-135">Od verze rozhraní .NET Core 3.0, verze, kterou najdete rozhraní API pomocí .NET Core teď vrácené informace měli očekávat.</span><span class="sxs-lookup"><span data-stu-id="f234b-135">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="f234b-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f234b-136">For example:</span></span>

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
> <span data-ttu-id="f234b-137">Rozbíjející změny.</span><span class="sxs-lookup"><span data-stu-id="f234b-137">Breaking change.</span></span> <span data-ttu-id="f234b-138">Toto je technicky rozbíjející změny, protože došlo ke změně schématu vytváření verzí.</span><span class="sxs-lookup"><span data-stu-id="f234b-138">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="f234b-139">Vnitřní objekty závislého na platformě .NET</span><span class="sxs-lookup"><span data-stu-id="f234b-139">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="f234b-140">Rozhraní API nepřidali, která umožňují přístup k určité pokyny orientované výkonu procesoru, jako **SIMD** nebo **Bit zpracování instrukcí** nastaví.</span><span class="sxs-lookup"><span data-stu-id="f234b-140">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="f234b-141">Tyto pokyny mohou pomoci dosáhnout výrazné zlepšení výkonu v některých scénářích, jako je zpracování dat, efektivně paralelně.</span><span class="sxs-lookup"><span data-stu-id="f234b-141">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="f234b-142">Kde je to vhodné, knihovny .NET jste začali, podle těchto pokynů ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="f234b-142">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="f234b-143">Další informace najdete v tématu [závislé vnitřní funkce platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="f234b-143">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="f234b-144">Výchozí spustitelné soubory</span><span class="sxs-lookup"><span data-stu-id="f234b-144">Default executables</span></span>

<span data-ttu-id="f234b-145">Sestavení .NET core teď [závisí na architektuře spustitelných souborů](../deploying/index.md#framework-dependent-executables-fde) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f234b-145">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="f234b-146">Toto chování je nová pro aplikace, které používají globálně nainstalovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f234b-146">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="f234b-147">Předtím jenom [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) vytvoří spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f234b-147">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="f234b-148">Během `dotnet build` nebo `dotnet publish`, je vytvořen spustitelný soubor, který odpovídá prostředí a platformě sady SDK, které používáte.</span><span class="sxs-lookup"><span data-stu-id="f234b-148">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="f234b-149">Můžete očekávat, že stejné operace tyto spustitelné soubory stejně jako další nativní spustitelné soubory, jako například:</span><span class="sxs-lookup"><span data-stu-id="f234b-149">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="f234b-150">Můžete dvakrát kliknout na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f234b-150">You can double-click on the executable.</span></span>
* <span data-ttu-id="f234b-151">Aplikace z příkazového řádku můžete spustit přímo, jako například `myapp.exe` na Windows, a `./myapp` v Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="f234b-151">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="f234b-152">Spustitelné soubory jedním souborem</span><span class="sxs-lookup"><span data-stu-id="f234b-152">Single-file executables</span></span>

<span data-ttu-id="f234b-153">`dotnet publish` Příkaz podporuje vytváření balíčků aplikací do spustitelného souboru specifické pro platformu jedním souborem.</span><span class="sxs-lookup"><span data-stu-id="f234b-153">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="f234b-154">Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativní), které jsou potřeba ke spouštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f234b-154">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="f234b-155">Při prvním spuštění aplikace, aplikace je extrahován do adresáře podle aplikaci název a identifikátor sestavení.</span><span class="sxs-lookup"><span data-stu-id="f234b-155">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="f234b-156">Po spuštění je rychlejší při dalším spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f234b-156">Startup is faster when the application is run again.</span></span> <span data-ttu-id="f234b-157">Aplikace nemusí extrahovat samotné podruhé, pokud byla použita nová verze.</span><span class="sxs-lookup"><span data-stu-id="f234b-157">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="f234b-158">Chcete-li publikovat do jednoho souboru spustitelný soubor, nastavte `PublishSingleFile` ve vašem projektu nebo na příkazovém řádku se `dotnet publish` příkaz:</span><span class="sxs-lookup"><span data-stu-id="f234b-158">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="f234b-159">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f234b-159">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="f234b-160">Další informace o publikování jednoho souboru, najdete v článku [dokumentu návrh například položky bundler jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="f234b-160">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="f234b-161">Propojování sestavení</span><span class="sxs-lookup"><span data-stu-id="f234b-161">Assembly linking</span></span>

<span data-ttu-id="f234b-162">.NET core 3.0 SDK obsahuje nástroj, který můžete zmenšit velikost aplikací tak, že analýza IL a ořezávání nevyužité sestavení.</span><span class="sxs-lookup"><span data-stu-id="f234b-162">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="f234b-163">Samostatná aplikace patří vše potřebné pro spuštění kódu, bez nutnosti .NET být nainstalovaný na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="f234b-163">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="f234b-164">Ale v mnoha případech aplikace vyžaduje pouze malou podmnožinu rozhraní pro funkci a další nepoužité knihovny nebylo možné odebrat.</span><span class="sxs-lookup"><span data-stu-id="f234b-164">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="f234b-165">.NET core teď zahrnuje nastavení, které budou používat [IL linkeru](https://github.com/mono/linker) nástroj pro skenování IL vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f234b-165">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="f234b-166">Tento nástroj rozpozná, jaký kód je povinný a potom ořízne nepoužité knihovny.</span><span class="sxs-lookup"><span data-stu-id="f234b-166">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="f234b-167">Tento nástroj může výrazně snížit velikost některé aplikace pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="f234b-167">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="f234b-168">Pokud chcete povolit Tenhle nástroj, přidejte `<PublishTrimmed>` nastavení ve vašem projektu a publikování samostatnou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="f234b-168">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="f234b-169">Například volání základní "hello world" nové konzoly šablony projektu, který je součástí, při publikování, velikost přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="f234b-169">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="f234b-170">S použitím `<PublishTrimmed>`, zmenšení velikosti na přibližně 30 MB.</span><span class="sxs-lookup"><span data-stu-id="f234b-170">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="f234b-171">Je důležité vzít v úvahu, že aplikace nebo rozhraní (včetně ASP.NET Core a WPF), které používají reflexi nebo související dynamické funkce se často přerušit, když oříznut.</span><span class="sxs-lookup"><span data-stu-id="f234b-171">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="f234b-172">Tato rozbití dochází, protože nebude vědět o toto dynamické chování linkeru a nemůže určit typy rozhraní framework, které jsou požadovány pro účely reflexe.</span><span class="sxs-lookup"><span data-stu-id="f234b-172">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="f234b-173">Je potřeba vědět tento scénář lze nakonfigurovat nástroj IL Linker.</span><span class="sxs-lookup"><span data-stu-id="f234b-173">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="f234b-174">Nad všemi jinak nezapomeňte otestovat vaši aplikaci po oříznutí.</span><span class="sxs-lookup"><span data-stu-id="f234b-174">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="f234b-175">Další informace o nástroji IL Linkeru, naleznete v tématu [dokumentaci](https://aka.ms/dotnet-illink) , případně přejděte [mono/linkeru]( https://github.com/mono/linker) úložiště.</span><span class="sxs-lookup"><span data-stu-id="f234b-175">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="f234b-176">Vrstvené kompilace</span><span class="sxs-lookup"><span data-stu-id="f234b-176">Tiered compilation</span></span>

<span data-ttu-id="f234b-177">[Vrstvené kompilace](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) je ve výchozím s .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f234b-177">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="f234b-178">Tato funkce umožňuje modulu runtime více Adaptivně kompilátor za běhu (JIT) umožňuje dosahovat vyšších výkonů.</span><span class="sxs-lookup"><span data-stu-id="f234b-178">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="f234b-179">Hlavní výhodou TC je povolit zpětný jitting metody s pomalejší – ale – rychlejší pro vytvoření kódu nebo vyšší kvality – ale pomalejší vytvářet kód.</span><span class="sxs-lookup"><span data-stu-id="f234b-179">The main benefit of TC is to enable (re-)jitting methods with slower-but-faster to produce code or higher-quality-but-slower to produce code.</span></span> <span data-ttu-id="f234b-180">To pomáhá zvýšit výkon aplikace, protože probíhá různé fáze zpracování, od spuštění do stabilního stavu.</span><span class="sxs-lookup"><span data-stu-id="f234b-180">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="f234b-181">Tím se liší od přístup bez TC, kde je zkompilován každou metodu jeden způsob (stejné jako na úrovni vysoce kvalitní), který je tendenční do stabilního stavu přes výkon při spouštění.</span><span class="sxs-lookup"><span data-stu-id="f234b-181">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="f234b-182">Pokud chcete povolit rychlé JIT (vrstva 0 kódu), použijte následující nastavení v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="f234b-182">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="f234b-183">Chcete-li zcela zakázat TC, použijte následující nastavení v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="f234b-183">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="f234b-184">ReadyToRun imagí</span><span class="sxs-lookup"><span data-stu-id="f234b-184">ReadyToRun images</span></span>

<span data-ttu-id="f234b-185">Spuštění aplikace .NET Core můžete zlepšit kompilaci vaším sestavením aplikace jako formát ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="f234b-185">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="f234b-186">R2R je forma kompilace ahead of time (AOT).</span><span class="sxs-lookup"><span data-stu-id="f234b-186">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="f234b-187">Binární soubory R2R zlepšit výkon při spuštění snížením množství práce, kompilátor just-in-time (JIT) se musí provést jako zatížení vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="f234b-187">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="f234b-188">Binární soubory obsahují podobné nativního kódu ve srovnání s co by vytvořila kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="f234b-188">The binaries contain similar native code compared to what the JIT would produce.</span></span>

<span data-ttu-id="f234b-189">R2R binární soubory jsou větší, protože obsahují i kód (IL intermediate language), který je stále potřeba pro některé scénáře a nativní verzi stejný kód.</span><span class="sxs-lookup"><span data-stu-id="f234b-189">R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="f234b-190">R2R je k dispozici pouze při publikování, který cílí modulu runtime specifické prostředí (RID), jako je Linux x64 nebo Windows x64 samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f234b-190">R2R is only available when you publish a self-contained app that targets a specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="f234b-191">Chcete-li kompilovat aplikaci jako R2R, přidejte `<PublishReadyToRun>` nastavení:</span><span class="sxs-lookup"><span data-stu-id="f234b-191">To compile your app as R2R, add the `<PublishReadyToRun>` setting:</span></span>

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

<span data-ttu-id="f234b-192">Publikování samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f234b-192">Publish a self-contained app.</span></span> <span data-ttu-id="f234b-193">Třeba tento příkaz vytvoří samostatnou aplikaci pro 64bitové verzi systému Windows:</span><span class="sxs-lookup"><span data-stu-id="f234b-193">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="f234b-194">Pro různé platformy/architektura omezení</span><span class="sxs-lookup"><span data-stu-id="f234b-194">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="f234b-195">Kompilátor ReadyToRun v současné době nepodporuje cílí na různé.</span><span class="sxs-lookup"><span data-stu-id="f234b-195">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="f234b-196">Je nutné kompilovat na daném cíli.</span><span class="sxs-lookup"><span data-stu-id="f234b-196">You must compile on a given target.</span></span> <span data-ttu-id="f234b-197">Například pokud chcete R2R imagí Windows x64, musíte ke spuštění příkazu Publikovat v tomto prostředí.</span><span class="sxs-lookup"><span data-stu-id="f234b-197">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="f234b-198">Cílení na různé výjimky:</span><span class="sxs-lookup"><span data-stu-id="f234b-198">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="f234b-199">Windows x64 lze použít ke kompilaci Windows ARM32, ARM64 a x86 bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="f234b-199">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="f234b-200">Windows x86 lze použít ke kompilaci Windows ARM32 Image.</span><span class="sxs-lookup"><span data-stu-id="f234b-200">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="f234b-201">Linux x64 lze použít ke kompilaci imagí Linuxu ARM32 a ARM64.</span><span class="sxs-lookup"><span data-stu-id="f234b-201">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="f234b-202">Vytvoření kopie závislosti</span><span class="sxs-lookup"><span data-stu-id="f234b-202">Build copies dependencies</span></span>

<span data-ttu-id="f234b-203">`dotnet build` Příkaz nyní zkopíruje závislostí NuGet pro vaši aplikaci z mezipaměti NuGet k výstupní složce sestavení.</span><span class="sxs-lookup"><span data-stu-id="f234b-203">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="f234b-204">Dříve byly závislosti pouze zkopírovány jako součást `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="f234b-204">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="f234b-205">Existují některé operace, jako je stránka propojení a razor publikování, který se stále vyžadují publikování.</span><span class="sxs-lookup"><span data-stu-id="f234b-205">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="f234b-206">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="f234b-206">Local tools</span></span>

<span data-ttu-id="f234b-207">.NET core 3.0 představuje místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="f234b-207">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="f234b-208">Místní nástroje se podobají [globální nástroje](../tools/global-tools.md) , ale jsou spojeny s konkrétní umístění na disku.</span><span class="sxs-lookup"><span data-stu-id="f234b-208">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="f234b-209">Místní nástroje nejsou k dispozici globálně a distribuují jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="f234b-209">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="f234b-210">Pokud jste se pokusili místní nástroje .NET Core 3.0 ve verzi Preview 1, jako je například spuštění `dotnet tool restore` nebo `dotnet tool install`, odstraňte složku mezipaměti místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="f234b-210">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="f234b-211">V opačném případě nástrojů pro místní nebude fungovat v jakékoli novější verze.</span><span class="sxs-lookup"><span data-stu-id="f234b-211">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="f234b-212">Tato složka nachází tady:</span><span class="sxs-lookup"><span data-stu-id="f234b-212">This folder is located at:</span></span>
>
> <span data-ttu-id="f234b-213">V systému macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="f234b-213">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="f234b-214">Ve Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="f234b-214">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="f234b-215">Místní nástroje spoléhají na název souboru manifestu `dotnet-tools.json` v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="f234b-215">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="f234b-216">Tento soubor manifestu definuje nástroje k dispozici v této složce a níže.</span><span class="sxs-lookup"><span data-stu-id="f234b-216">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="f234b-217">Soubor manifestu můžete distribuovat s vaším kódem zajistit, že každý, kdo pracuje s vaším kódem můžete obnovit a použít stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="f234b-217">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="f234b-218">Pro globální a místní nástroje se vyžaduje kompatibilní verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f234b-218">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="f234b-219">Mnoho nástrojů aktuálně na NuGet.org cílit na .NET Core Runtime 2.1.</span><span class="sxs-lookup"><span data-stu-id="f234b-219">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="f234b-220">K instalaci těchto nástrojů globálně nebo místně, je stále třeba k instalaci [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="f234b-220">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="f234b-221">Hlavní verze Posunutí vpřed</span><span class="sxs-lookup"><span data-stu-id="f234b-221">Major-version Roll Forward</span></span>

<span data-ttu-id="f234b-222">.NET core 3.0 zavádí přihlašovaná funkce, které vaše aplikace bude posunout vpřed na nejnovější hlavní verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f234b-222">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="f234b-223">Kromě toho byla přidána nové nastavení pro řízení použití posunutí vpřed do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f234b-223">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="f234b-224">To lze nastavit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="f234b-224">This can be configured in the following ways:</span></span>

- <span data-ttu-id="f234b-225">Vlastnost souboru projektu: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="f234b-225">Project file property: `RollForward`</span></span>
- <span data-ttu-id="f234b-226">Vlastnost souboru konfigurace modulu runtime: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="f234b-226">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="f234b-227">Proměnné prostředí: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="f234b-227">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="f234b-228">Argument příkazového řádku: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="f234b-228">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="f234b-229">Musíte zadat jeden z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="f234b-229">One of the following values must be specified.</span></span> <span data-ttu-id="f234b-230">Pokud toto nastavení je tento parametr vynechán, **menší** je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="f234b-230">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="f234b-231">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="f234b-231">**LatestPatch**</span></span>\
<span data-ttu-id="f234b-232">Posunout vpřed na nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="f234b-232">Roll forward to the highest patch version.</span></span> <span data-ttu-id="f234b-233">Zakáže podverze Posunutí vpřed.</span><span class="sxs-lookup"><span data-stu-id="f234b-233">This disables minor version roll forward.</span></span>
- <span data-ttu-id="f234b-234">**Podverze**</span><span class="sxs-lookup"><span data-stu-id="f234b-234">**Minor**</span></span>\
<span data-ttu-id="f234b-235">Program posunout vpřed na nejnižší vyšší dílčí verze, pokud chybí požadovaný podverze.</span><span class="sxs-lookup"><span data-stu-id="f234b-235">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="f234b-236">Pokud požadovaný dílčí verze je k dispozici, pak bude **LatestPatch** zásady použít.</span><span class="sxs-lookup"><span data-stu-id="f234b-236">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="f234b-237">**Hlavní**</span><span class="sxs-lookup"><span data-stu-id="f234b-237">**Major**</span></span>\
<span data-ttu-id="f234b-238">Program posunout vpřed na nejnižší vyšší hlavní verze a nejnižší podverze, pokud chybí požadovaný hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="f234b-238">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="f234b-239">Pokud je k dispozici, vyžádaná hlavní verze pak bude **menší** použití zásad.</span><span class="sxs-lookup"><span data-stu-id="f234b-239">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="f234b-240">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="f234b-240">**LatestMinor**</span></span>\
<span data-ttu-id="f234b-241">Program posunout vpřed na nejvyšší podverze, i v případě, že požadovaný dílčí verze je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f234b-241">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="f234b-242">Určeno pro scénáře hostování součásti.</span><span class="sxs-lookup"><span data-stu-id="f234b-242">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="f234b-243">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="f234b-243">**LatestMajor**</span></span>\
<span data-ttu-id="f234b-244">Vrátit vpřed na nejvyšší hlavní a nejvyšší podverze, i v případě, že požadovaný hlavní je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f234b-244">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="f234b-245">Určeno pro scénáře hostování součásti.</span><span class="sxs-lookup"><span data-stu-id="f234b-245">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="f234b-246">**Zakázat**</span><span class="sxs-lookup"><span data-stu-id="f234b-246">**Disable**</span></span>\
<span data-ttu-id="f234b-247">Není posunout vpřed.</span><span class="sxs-lookup"><span data-stu-id="f234b-247">Don't roll forward.</span></span> <span data-ttu-id="f234b-248">Pouze vytvořit vazbu na zadanou verzi.</span><span class="sxs-lookup"><span data-stu-id="f234b-248">Only bind to specified version.</span></span> <span data-ttu-id="f234b-249">Tato zásada se nedoporučuje pro obecné použití, protože zakáže schopnost posunout vpřed na nejnovějších oprav.</span><span class="sxs-lookup"><span data-stu-id="f234b-249">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="f234b-250">Tato hodnota se doporučuje jenom pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="f234b-250">This value is only recommended for testing.</span></span>

<span data-ttu-id="f234b-251">Kromě **zakázat** nastavení, budou všechna nastavení používat nejvyšší verze k dispozici opravy.</span><span class="sxs-lookup"><span data-stu-id="f234b-251">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="f234b-252">Plocha Windows</span><span class="sxs-lookup"><span data-stu-id="f234b-252">Windows desktop</span></span>

<span data-ttu-id="f234b-253">.NET core 3.0 podporuje desktopové aplikace Windows pomocí formulářů Windows a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f234b-253">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="f234b-254">Tyto architektury podporují také pomocí moderních ovládací prvky a Fluent stylů v knihovně Windows uživatelského rozhraní XAML (WinUI) prostřednictvím [XAML ostrovy](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="f234b-254">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="f234b-255">Komponenta Windows Desktop je součástí Windows .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f234b-255">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="f234b-256">Můžete vytvořit novou aplikaci WPF nebo Windows Forms s následujícími `dotnet` příkazy:</span><span class="sxs-lookup"><span data-stu-id="f234b-256">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="f234b-257">Visual Studio 2019 přidá **nový projekt** šablon pro .NET Core 3.0 Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="f234b-257">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="f234b-258">Další informace o způsobu přenesení existující aplikaci .NET Framework najdete v tématu [projekty Port WPF](../porting/wpf.md) a [Port Windows Forms projekty](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="f234b-258">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="f234b-259">Součásti COM-callable - Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="f234b-259">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="f234b-260">Na Windows můžete teď vytvořit volatelná aplikacemi COM spravované součásti.</span><span class="sxs-lookup"><span data-stu-id="f234b-260">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="f234b-261">Tato funkce je důležité pro použití .NET Core s modelu COM doplněk modely a také k poskytování parity pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f234b-261">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="f234b-262">Na rozdíl od rozhraní .NET Framework ve kterém *mscoree.dll* byl použit jako COM server, .NET Core přidá Spouštěč nativní knihovnu dll *bin* adresáře při sestavování vaší komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f234b-262">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="f234b-263">Příklad toho, jak vytvořit komponentu modelu COM a používat ji, najdete v článku [COM ukázka](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="f234b-263">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="f234b-264">Nasazení MSIX – Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="f234b-264">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="f234b-265">[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="f234b-265">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="f234b-266">Slouží k nasazení rozhraní .NET Core 3.0 desktopové aplikace pro Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f234b-266">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="f234b-267">[Projekt Windows Application Packaging](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), k dispozici v aplikaci Visual Studio 2019, vám umožní vytvořit MSIX balíčky s [samostatná](../deploying/index.md#self-contained-deployments-scd) aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f234b-267">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="f234b-268">Soubor projektu .NET Core, musíte zadat podporované moduly Runtime v `<RuntimeIdentifiers>` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="f234b-268">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="f234b-269">WinForms HighDPI</span><span class="sxs-lookup"><span data-stu-id="f234b-269">WinForms HighDPI</span></span>

<span data-ttu-id="f234b-270">Aplikace modelu Windows Forms .NET core můžete nastavit režim vysokého nastavení DPI s <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f234b-270">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f234b-271">`SetHighDpiMode` Metoda nastaví odpovídající režim vysokého nastavení DPI, pokud nastavení jinými způsoby `App.Manifest` nebo P/Invoke před `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="f234b-271">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="f234b-272">Možné `highDpiMode` hodnoty, jak je vyjádřen podle <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> výčtu jsou:</span><span class="sxs-lookup"><span data-stu-id="f234b-272">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="f234b-273">Další informace o režimech vysokého nastavení DPI, naleznete v tématu [vysoké rozlišení DPI Desktop Application Development na Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="f234b-273">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="f234b-274">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="f234b-274">Ranges and indices</span></span>

<span data-ttu-id="f234b-275">Nové <xref:System.Index?displayProperty=nameWithType> typ lze použít k indexování.</span><span class="sxs-lookup"><span data-stu-id="f234b-275">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="f234b-276">Můžete je vytvořit z `int` , které se počítá od začátku, nebo s předponou `^` – operátor (C#), které se počítá od konce:</span><span class="sxs-lookup"><span data-stu-id="f234b-276">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="f234b-277">K dispozici je také <xref:System.Range?displayProperty=nameWithType> typ, který se skládá ze dvou `Index` hodnoty, jeden pro spuštění a jeden pro ukončení a může být zapsaný s `x..y` výrazu v rozsahu (C#).</span><span class="sxs-lookup"><span data-stu-id="f234b-277">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="f234b-278">Potom můžete index s využitím `Range`, které produkuje řez:</span><span class="sxs-lookup"><span data-stu-id="f234b-278">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="f234b-279">Další informace najdete v tématu [kurz rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="f234b-279">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="f234b-280">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="f234b-280">Async streams</span></span>

<span data-ttu-id="f234b-281"><xref:System.Collections.Generic.IAsyncEnumerable%601> Typ je nový asynchronní verze <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f234b-281">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f234b-282">Jazyk umožňuje `await foreach` přes `IAsyncEnumerable<T>` využívat jejich prvky a použití `yield return` k nim pro produkci prvků.</span><span class="sxs-lookup"><span data-stu-id="f234b-282">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="f234b-283">Následující příklad ukazuje produkční scénáře i využití asynchronních streamů.</span><span class="sxs-lookup"><span data-stu-id="f234b-283">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="f234b-284">`foreach` Příkaz je asynchronní a sama používá `yield return` vytvoří na asynchronní datový proud pro volající.</span><span class="sxs-lookup"><span data-stu-id="f234b-284">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="f234b-285">Tento model (pomocí `yield return`) je doporučený model pro vytváření asynchronních streamů.</span><span class="sxs-lookup"><span data-stu-id="f234b-285">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="f234b-286">Kromě toho, že možnost `await foreach`, můžete také vytvořit asynchronní iterátory, například iterátoru, který vrátí `IAsyncEnumerable/IAsyncEnumerator` , můžete obě `await` a `yield` v.</span><span class="sxs-lookup"><span data-stu-id="f234b-286">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="f234b-287">Pro objekty, které je potřeba se dá uvolnit, můžete použít `IAsyncDisposable`, které různé typy BCL implementovat jako `Stream` a `Timer`.</span><span class="sxs-lookup"><span data-stu-id="f234b-287">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="f234b-288">Další informace najdete v tématu [asynchronní datové proudy kurzu](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="f234b-288">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="f234b-289">Vylepšení plovoucí desetinné čárky IEEE</span><span class="sxs-lookup"><span data-stu-id="f234b-289">IEEE Floating-point improvements</span></span>

<span data-ttu-id="f234b-290">Číslo s plovoucí čárkou bodu rozhraní API se aktualizují v souladu s [IEEE 754-2008 revize](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="f234b-290">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="f234b-291">Cílem těchto změn je vystavit všechny **požadované** operací a ujistěte se, že byly behaviorally kompatibilní s specifikace IEEE. Další informace o vylepšeních s plovoucí desetinnou čárkou, najdete v článku [vylepšení analýzy plovoucí desetinné čárky a formátování v .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blogový příspěvek.</span><span class="sxs-lookup"><span data-stu-id="f234b-291">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="f234b-292">Analýza a formátování opravy patří:</span><span class="sxs-lookup"><span data-stu-id="f234b-292">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="f234b-293">Správně analyzovat a zaokrouhlit vstupů o libovolné délce.</span><span class="sxs-lookup"><span data-stu-id="f234b-293">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="f234b-294">Správně analyzovat a formátování záporná nula.</span><span class="sxs-lookup"><span data-stu-id="f234b-294">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="f234b-295">Správně analyzovat `Infinity` a `NaN` to dělat kontrolu velkých a malých písmen a volitelné předcházející `+` kde je to možné.</span><span class="sxs-lookup"><span data-stu-id="f234b-295">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="f234b-296">Nové <xref:System.Math?displayProperty=nameWithType> rozhraní API patří:</span><span class="sxs-lookup"><span data-stu-id="f234b-296">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="f234b-297"><xref:System.Math.BitIncrement(System.Double)> a <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="f234b-297"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="f234b-298">Odpovídá `nextUp` a `nextDown` IEEE operace.</span><span class="sxs-lookup"><span data-stu-id="f234b-298">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="f234b-299">Vrátí nejmenší s plovoucí desetinnou čárkou čísla, která porovnává větší nebo menší než vstup (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="f234b-299">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="f234b-300">Například `Math.BitIncrement(0.0)` vracel `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="f234b-300">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="f234b-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> a <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="f234b-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="f234b-302">Odpovídá `maxNumMag` a `minNumMag` IEEE operace, vrátí hodnotu, která je větší nebo menší řádově dva vstupy (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="f234b-302">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="f234b-303">Například `Math.MaxMagnitude(2.0, -3.0)` vracel `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="f234b-303">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="f234b-304">Odpovídá `logB` IEEE operace, která vrací celé číslo, vrátí integrální protokolu základu 2 vstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="f234b-304">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="f234b-305">Tato metoda je v podstatě totéž jako `floor(log2(x))`, ale ukončili minimální zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="f234b-305">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="f234b-306">Odpovídá `scaleB` IEEE operace, která přebírá celé číslo, vrátí efektivně `x * pow(2, n)`, ale se provádí s minimálními zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="f234b-306">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="f234b-307">Odpovídá `log2` IEEE operace Vrátí logaritmus o základu 2.</span><span class="sxs-lookup"><span data-stu-id="f234b-307">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="f234b-308">Minimalizuje zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="f234b-308">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="f234b-309">Odpovídá `fma` IEEE operace provádí roztaveného vynásobit sčítanec.</span><span class="sxs-lookup"><span data-stu-id="f234b-309">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="f234b-310">To znamená, že nemá `(x * y) + z` jako jediná operace, existuje-minimalizací zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="f234b-310">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="f234b-311">Příkladem může být `FusedMultiplyAdd(1e308, 2.0, -1e308)` která vrací `1e308`.</span><span class="sxs-lookup"><span data-stu-id="f234b-311">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="f234b-312">Standardní `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="f234b-312">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="f234b-313">Odpovídá `copySign` IEEE operace, vrátí hodnotu `x`, ale s znaménko `y`.</span><span class="sxs-lookup"><span data-stu-id="f234b-313">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="f234b-314">Rychlé integrovanou podporou JSON</span><span class="sxs-lookup"><span data-stu-id="f234b-314">Fast built-in JSON support</span></span>

<span data-ttu-id="f234b-315">Uživatelé rozhraní .NET mají do značné míry spoléhat [ **Json.NET** ](https://www.newtonsoft.com/json) a dalších oblíbených knihoven JSON, které dál vhodná rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="f234b-315">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="f234b-316">**Json.NET** používá .NET řetězce jako jeho základní datový typ, který je UTF-16 pod pokličkou.</span><span class="sxs-lookup"><span data-stu-id="f234b-316">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="f234b-317">Nové integrované podpoře JSON je vysoce výkonné, nízká přidělení a na základě `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="f234b-317">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="f234b-318">Tři nové hlavní JSON související typy byly přidány pro .NET Core 3.0 <xref:System.Text.Json?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f234b-318">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f234b-319">Tyto typy není *ještě* podporu prostý staré CLR objektů (POCO) serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="f234b-319">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="f234b-320">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="f234b-320">Utf8JsonReader</span></span>

<span data-ttu-id="f234b-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> je vysoce výkonné, s nízkou přidělení, dopředné čtecí modul pro kódování UTF-8 kódovaný JSON čtení z textu `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="f234b-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="f234b-322">`Utf8JsonReader` Je nízké úrovně, základní typ, který je možné vytvářet vlastní analyzátory a deserializers.</span><span class="sxs-lookup"><span data-stu-id="f234b-322">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="f234b-323">Přečtení datovou část JSON pomocí nového `Utf8JsonReader` je 2 × rychleji než při použití reader od **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="f234b-323">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="f234b-324">Nelze přidělit, dokud je potřeba actualize tokeny JSON jako řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="f234b-324">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="f234b-325">Tady je příklad čtení až [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) soubor vytvořený Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="f234b-325">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="f234b-326">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="f234b-326">Utf8JsonWriter</span></span>

<span data-ttu-id="f234b-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> poskytuje vysoce výkonné, bez mezipaměti, dopředné až po zápisu kódování UTF-8, jako je JSON textu z běžných typů .NET `String`, `Int32`, a `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="f234b-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="f234b-328">Podobně jako čtenář je modul pro zápis nízké úrovně, základní typ, který je možné vytvářet vlastní serializátory.</span><span class="sxs-lookup"><span data-stu-id="f234b-328">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="f234b-329">Zápis datové části JSON pomocí nového `Utf8JsonWriter` je 30 80 % rychlejší než při použití modulu pro zápis z **Json.NET** a nebude přidělovat.</span><span class="sxs-lookup"><span data-stu-id="f234b-329">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="f234b-330">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="f234b-330">JsonDocument</span></span>

<span data-ttu-id="f234b-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> je postavený na `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="f234b-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="f234b-332">`JsonDocument` Poskytuje schopnost analyzovat JSON data a sestavení jen pro čtení Document Object Model (DOM), který může být dotazována k podporují náhodný přístup a výčet.</span><span class="sxs-lookup"><span data-stu-id="f234b-332">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="f234b-333">Elementy JSON, které tvoří dat přístupné prostřednictvím <xref:System.Text.Json.JsonElement> typ, který je zveřejněný prostřednictvím `JsonDocument` jako vlastnost s názvem `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="f234b-333">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="f234b-334">`JsonElement` Obsahuje čítačů, společně s rozhraním API pro převod textu JSON na běžné typy .NET pole a objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="f234b-334">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="f234b-335">Parsování typické datová část JSON a přístup k všechny její členy pomocí `JsonDocument` je 2 až 3 x rychlejší než **Json.NET** s malou přidělení pro data, která je poměrně velké (to znamená, že < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="f234b-335">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="f234b-336">Tady je ukázkový používání `JsonDocument` a `JsonElement` , který může sloužit jako výchozí bod:</span><span class="sxs-lookup"><span data-stu-id="f234b-336">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

<span data-ttu-id="f234b-337">Tady je C# 8.0 Příklad čtení až [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) soubor vytvořený Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="f234b-337">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="f234b-338">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="f234b-338">JsonSerializer</span></span>

<span data-ttu-id="f234b-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> je postavený na <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter> poskytnout možnost serializace rychlé nedostatku paměti při práci s dokumenty JSON a fragmenty.</span><span class="sxs-lookup"><span data-stu-id="f234b-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="f234b-340">VYHLEDEJTE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md příklad port, který se v tomto článku</span><span class="sxs-lookup"><span data-stu-id="f234b-340">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md for an example to port to this article</span></span>

<span data-ttu-id="f234b-341">Tady je příklad serializace objektu do formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="f234b-341">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="f234b-342">Tady je příklad deserializaci řetězce JSON na objekt.</span><span class="sxs-lookup"><span data-stu-id="f234b-342">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="f234b-343">Řetězec JSON vytvořený v předchozím příkladu můžete použít:</span><span class="sxs-lookup"><span data-stu-id="f234b-343">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="f234b-344">Vylepšení spolupráce</span><span class="sxs-lookup"><span data-stu-id="f234b-344">Interop improvements</span></span>

<span data-ttu-id="f234b-345">.NET core 3.0 zlepšuje nativní rozhraní API zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="f234b-345">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="f234b-346">Zadejte: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="f234b-346">Type: NativeLibrary</span></span>

<span data-ttu-id="f234b-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> zapouzdření pro načítání nativní knihovny (pomocí stejné logiky zatížení jako P/Invoke .NET Core) a poskytuje relevantní pomocných funkcí, jako `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="f234b-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="f234b-348">Příklad kódu, najdete v článku [DLLMap ukázka](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="f234b-348">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="f234b-349">Windows nativní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="f234b-349">Windows Native Interop</span></span>

<span data-ttu-id="f234b-350">Windows nabízí bohaté nativní rozhraní API v podobě bez stromové struktury rozhraní API jazyka C, COM a WinRT.</span><span class="sxs-lookup"><span data-stu-id="f234b-350">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="f234b-351">Přestože podporuje .NET Core **P/Invoke**, .NET Core 3.0 přidává možnost **souběžné vytvoření součásti COM API** a **aktivovat rozhraní API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="f234b-351">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="f234b-352">Příklad kódu, najdete v článku [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="f234b-352">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="f234b-353">Podpora HTTP/2</span><span class="sxs-lookup"><span data-stu-id="f234b-353">HTTP/2 support</span></span>

<span data-ttu-id="f234b-354"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typů podporuje protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="f234b-354">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="f234b-355">Pokud je povolená HTTP/2, verzi protokolu HTTP se vyjedná přes protokol TLS/ALPN a HTTP/2 se používá v případě, že rozhodne ho použít server.</span><span class="sxs-lookup"><span data-stu-id="f234b-355">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="f234b-356">Výchozím protokolem zůstane HTTP/1.1, ale HTTP/2 je možné povolit dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="f234b-356">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="f234b-357">Nejprve můžete nastavit zprávy s požadavkem HTTP používat HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="f234b-357">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="f234b-358">Za druhé, můžete změnit <xref:System.Net.Http.HttpClient> používat HTTP/2 ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="f234b-358">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="f234b-359">V mnoha případech Když vyvíjíte aplikaci, budete chtít použít nezašifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="f234b-359">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="f234b-360">Pokud víte, že cílový koncový bod se pomocí protokolu HTTP/2, můžete zapnout nezašifrované připojení HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="f234b-360">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="f234b-361">Můžete zapnout ho tak, že nastavíte `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` proměnnou prostředí, aby `1` nebo tím, že v rámci aplikace:</span><span class="sxs-lookup"><span data-stu-id="f234b-361">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="f234b-362">TLS verze 1.3 & OpenSSL 1.1.1 v Linuxu</span><span class="sxs-lookup"><span data-stu-id="f234b-362">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="f234b-363">Teď využívá výhod platformy .NET core [podpora protokolu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), až bude k dispozici v daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="f234b-363">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="f234b-364">S TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="f234b-364">With TLS 1.3:</span></span>

* <span data-ttu-id="f234b-365">Čas připojení jsou vylepšeny sníženou má zpáteční převod vyžaduje mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="f234b-365">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="f234b-366">Vyšší úroveň zabezpečení z důvodu odstranění různých zastaralé a nezabezpečené kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="f234b-366">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="f234b-367">Pokud je k dispozici, .NET Core 3.0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, nebo **OpenSSL 1.0.2** v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="f234b-367">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="f234b-368">Při **OpenSSL 1.1.1** je k dispozici, i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> a <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> používat typy **TLS 1.3** (za předpokladu, že klient i server podpory **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="f234b-368">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="f234b-369">Windows a macOS zatím ještě nepodporují **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="f234b-369">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="f234b-370">Bude podporovat .NET core 3.0 **TLS 1.3** v těchto operačních systémech, jakmile je k dispozici podpora.</span><span class="sxs-lookup"><span data-stu-id="f234b-370">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="f234b-371">Následující C# 8.0 příklad ukazuje, .NET Core 3.0 na Ubuntu 18.10 propojíte <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="f234b-371">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="f234b-372">Šifry šifrování</span><span class="sxs-lookup"><span data-stu-id="f234b-372">Cryptography ciphers</span></span>

<span data-ttu-id="f234b-373">Přidává podporu pro .NET 3.0 **AES-GCM** a **AES-CCM** šifry, prováděné s <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> a <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f234b-373">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="f234b-374">Tyto algoritmy jsou obě [ověření šifrování pomocí algoritmů přidružení dat (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="f234b-374">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="f234b-375">Následující kód ukazuje použití `AesGcm` šifer k šifrování a dešifrování náhodná data.</span><span class="sxs-lookup"><span data-stu-id="f234b-375">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="f234b-376">Kryptografické klíče Import/Export</span><span class="sxs-lookup"><span data-stu-id="f234b-376">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="f234b-377">.NET core 3.0 podporuje příkaz import a export asymetrické veřejného a privátního klíče ze standardní formáty.</span><span class="sxs-lookup"><span data-stu-id="f234b-377">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="f234b-378">Není nutné použít certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="f234b-378">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="f234b-379">Všechny klíče typy, jako například *RSA*, *DSA*, *ECDsa*, a *ECDiffieHellman*, podporu následujících formátů:</span><span class="sxs-lookup"><span data-stu-id="f234b-379">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="f234b-380">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="f234b-380">**Public Key**</span></span>
  * <span data-ttu-id="f234b-381">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="f234b-381">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="f234b-382">**privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="f234b-382">**Private key**</span></span>
  * <span data-ttu-id="f234b-383">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="f234b-383">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="f234b-384">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="f234b-384">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="f234b-385">Klíčů RSA také podporu:</span><span class="sxs-lookup"><span data-stu-id="f234b-385">RSA keys also support:</span></span>

* <span data-ttu-id="f234b-386">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="f234b-386">**Public Key**</span></span>
  * <span data-ttu-id="f234b-387">PKCS č. 1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="f234b-387">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="f234b-388">**privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="f234b-388">**Private key**</span></span>
  * <span data-ttu-id="f234b-389">PKCS č. 1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="f234b-389">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="f234b-390">Export metody vracet kódování DER binárních dat, a metod importu očekávají, že stejné.</span><span class="sxs-lookup"><span data-stu-id="f234b-390">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="f234b-391">Pokud je klíč uložený ve formátu PEM popisný text, volajícího bude nutné base64 – dekódování obsahu před voláním metody importu.</span><span class="sxs-lookup"><span data-stu-id="f234b-391">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="f234b-392">**PKCS č. 8** soubory můžete prozkoumat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> a **PFX/PKCS #12** soubory můžete prozkoumat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f234b-392">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f234b-393">**PFX/PKCS #12** soubory lze manipulovat s <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f234b-393">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="f234b-394">SerialPort pro Linux</span><span class="sxs-lookup"><span data-stu-id="f234b-394">SerialPort for Linux</span></span>

<span data-ttu-id="f234b-395">.NET core 3.0 podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="f234b-395">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="f234b-396">Dříve, .NET Core, které jsou podporovány pouze při použití `SerialPort` na Windows.</span><span class="sxs-lookup"><span data-stu-id="f234b-396">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="f234b-397">Omezuje dockeru a cgroup paměti</span><span class="sxs-lookup"><span data-stu-id="f234b-397">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="f234b-398">Od verze Preview 3, spuštěné .NET Core 3.0 v Linuxu pomocí Dockeru lépe funguje s cgroup paměťová omezení.</span><span class="sxs-lookup"><span data-stu-id="f234b-398">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="f234b-399">Spuštění kontejneru Dockeru s omezení paměti, například s `docker run -m`, změní chování .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f234b-399">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="f234b-400">Výchozí velikost haldy systému uvolňování paměti (GC): maximálně 20 mb nebo 75 % omezení paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f234b-400">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="f234b-401">Explicitní velikost můžete nastavit jako absolutní číslo nebo procento cgroup limit.</span><span class="sxs-lookup"><span data-stu-id="f234b-401">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="f234b-402">Velikost minimální vyhrazeného segmentu na haldě uvolňování paměti je 16 mb.</span><span class="sxs-lookup"><span data-stu-id="f234b-402">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="f234b-403">Tato velikost snižuje počet haldy, které jsou vytvořeny na počítačích.</span><span class="sxs-lookup"><span data-stu-id="f234b-403">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="f234b-404">Menší velikost haldy uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="f234b-404">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="f234b-405">Velikost haldy systému uvolňování paměti výchozí zkrátila, což vede k .NET Core pomocí méně paměti.</span><span class="sxs-lookup"><span data-stu-id="f234b-405">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="f234b-406">Tato změna lépe sladěné s rozpočtem generace 0 přidělení s velikostí mezipaměti moderní procesoru.</span><span class="sxs-lookup"><span data-stu-id="f234b-406">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="f234b-407">Podpora velkých stránek kolekce uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="f234b-407">Garbage Collection Large Page support</span></span>

<span data-ttu-id="f234b-408">Velké stránky (označované také jako velké stránky v Linuxu) je funkce, kde je operační systém schopný vytvořit oblasti paměti větší než velikost nativní stránky (často 4 kB) ke zlepšení výkonu aplikací, které požadují tyto velkých stránek.</span><span class="sxs-lookup"><span data-stu-id="f234b-408">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="f234b-409">Uvolňování paměti se teď dá nakonfigurovat s **GCLargePages** nastavení jako funkce opt-in k výběru přidělit velkých stránek ve Windows.</span><span class="sxs-lookup"><span data-stu-id="f234b-409">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="f234b-410">Podpora GPIO Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="f234b-410">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="f234b-411">Byly vydány dva balíčky nuget, který můžete použít pro programování GPIO:</span><span class="sxs-lookup"><span data-stu-id="f234b-411">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="f234b-412">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="f234b-412">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="f234b-413">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="f234b-413">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="f234b-414">GPIO balíčky obsahují rozhraní API pro *GPIO*, *SPI*, *I2C*, a *PWM* zařízení.</span><span class="sxs-lookup"><span data-stu-id="f234b-414">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="f234b-415">Sada IoT vazby zahrnuje zařízení vazby.</span><span class="sxs-lookup"><span data-stu-id="f234b-415">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="f234b-416">Další informace najdete v tématu [zařízení úložiště GitHub se vzorovými](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="f234b-416">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="f234b-417">Podpora Linuxu ARM64</span><span class="sxs-lookup"><span data-stu-id="f234b-417">ARM64 Linux support</span></span>

<span data-ttu-id="f234b-418">.NET core 3.0 přidává podporu pro ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="f234b-418">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="f234b-419">Případem primárního použití pro ARM64 je aktuálně s scénáře IoT.</span><span class="sxs-lookup"><span data-stu-id="f234b-419">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="f234b-420">Další informace najdete v tématu [.NET Core ARM64 stav](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="f234b-420">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="f234b-421">[Image dockeru pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f234b-421">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="f234b-422">**ARM64** podporu Windows ještě není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f234b-422">**ARM64** Windows support isn't yet available.</span></span>
