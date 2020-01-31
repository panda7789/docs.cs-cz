---
title: Co je nového v .NET Core 3.0
description: Přečtěte si o nových funkcích, které najdete v .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 10/22/2019
ms.openlocfilehash: b8aa19a1d422fe7d6accd2b095f15843446599cd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789893"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="29949-103">Co je nového v .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="29949-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="29949-104">Tento článek popisuje, co je v .NET Core 3.0 novinkou.</span><span class="sxs-lookup"><span data-stu-id="29949-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="29949-105">Jedním z největších vylepšení je podpora desktopových aplikací pro Windows (jenom Windows).</span><span class="sxs-lookup"><span data-stu-id="29949-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="29949-106">Pomocí aplikace .NET Core 3.0 SDK desktopové plochy systému Windows můžete přenést model Windows Forms aplikace a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="29949-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="29949-107">Aby bylo jasné, že je komponenta Desktop systému Windows podporována a je součástí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="29949-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="29949-108">Další informace najdete v části [Windows Desktop](#windows-desktop) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="29949-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="29949-109">.NET Core 3.0 přidává podporu pro C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="29949-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="29949-110">Důrazně doporučujeme, abyste používali [Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější, [Visual Studio pro Mac 8,3](/visualstudio/mac/install-preview) nebo novější, nebo [Visual Studio Code](https://code.visualstudio.com/) s nejnovějším  **C# rozšířením**.</span><span class="sxs-lookup"><span data-stu-id="29949-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="29949-111">[Stáhněte si a začněte používat .NET Core 3.0](https://aka.ms/netcore3download) hned teď ve Windows, MacOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="29949-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="29949-112">Další informace o této verzi najdete v tématu [oznámení .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="29949-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="29949-113">.NET Core RC1 se považuje za produkční verzi Microsoft a je plně podporovaná.</span><span class="sxs-lookup"><span data-stu-id="29949-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="29949-114">Pokud používáte verzi Preview, musíte pro pokračování podpory přejít na verzi RTM.</span><span class="sxs-lookup"><span data-stu-id="29949-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="29949-115">Jazykové vylepšení C# 8,0</span><span class="sxs-lookup"><span data-stu-id="29949-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="29949-116">C#8,0 je také součástí této verze, která zahrnuje funkce [typu odkazu s možnou hodnotou null](../../csharp/tutorials/nullable-reference-types.md) , [asynchronní datové proudy](../../csharp/tutorials/generate-consume-asynchronous-stream.md)a [Další vzory](../../csharp/tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="29949-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="29949-117">Další informace o C# funkcích 8.0 najdete v tématu [co je nového v C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="29949-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="29949-118">Byla přidána vylepšení jazyka pro podporu následujících funkcí rozhraní API, které jsou popsány níže:</span><span class="sxs-lookup"><span data-stu-id="29949-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="29949-119">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="29949-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="29949-120">Asynchronní streamy</span><span class="sxs-lookup"><span data-stu-id="29949-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="29949-121">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="29949-121">.NET Standard 2.1</span></span>

<span data-ttu-id="29949-122">.NET Core 3,0 implementuje **.NET Standard 2,1**.</span><span class="sxs-lookup"><span data-stu-id="29949-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="29949-123">Výchozí šablona `dotnet new classlib` však vygeneruje projekt, který je stále cílen **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="29949-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="29949-124">Chcete-li cílit na **.NET Standard 2.1**, upravte soubor projektu a `TargetFramework` změňte vlastnost `netstandard2.1`na:</span><span class="sxs-lookup"><span data-stu-id="29949-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="29949-125">Pokud používáte Visual Studio, budete potřebovat [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), protože Visual Studio 2017 nepodporuje **.NET Standard 2.1** nebo **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="29949-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="29949-126">Kompilovat/nasadit</span><span class="sxs-lookup"><span data-stu-id="29949-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="29949-127">Výchozí spustitelné soubory</span><span class="sxs-lookup"><span data-stu-id="29949-127">Default executables</span></span>

<span data-ttu-id="29949-128">.NET Core teď ve výchozím nastavení vytváří [spustitelné soubory závislé na rozhraní](../deploying/index.md#framework-dependent-executables-fde) .</span><span class="sxs-lookup"><span data-stu-id="29949-128">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="29949-129">Toto chování je nové u aplikací, které používají globálně nainstalovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="29949-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="29949-130">Dříve mohli pouze [samostatně nasazená nasazení](../deploying/index.md#self-contained-deployments-scd) vyvolat spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="29949-130">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="29949-131">Během `dotnet build` nebo `dotnet publish`se vytvoří spustitelný soubor, který odpovídá prostředí a platformě sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="29949-131">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="29949-132">Pomocí těchto spustitelných souborů můžete očekávat stejné věci jako jiné nativní spustitelné soubory, jako například:</span><span class="sxs-lookup"><span data-stu-id="29949-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="29949-133">Můžete dvakrát kliknout na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="29949-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="29949-134">Aplikaci můžete spustit z příkazového řádku přímo, například `myapp.exe` ve Windows, a `./myapp` v systémech Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="29949-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="29949-135">Spustitelné soubory s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="29949-135">Single-file executables</span></span>

<span data-ttu-id="29949-136">Příkaz `dotnet publish` podporuje balení vaší aplikace do spustitelného souboru specifického pro jednotlivé platformy.</span><span class="sxs-lookup"><span data-stu-id="29949-136">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="29949-137">Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativních), které jsou nutné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="29949-137">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="29949-138">Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru buildu.</span><span class="sxs-lookup"><span data-stu-id="29949-138">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="29949-139">Spuštění je rychlejší, když aplikaci znovu spustíte.</span><span class="sxs-lookup"><span data-stu-id="29949-139">Startup is faster when the application is run again.</span></span> <span data-ttu-id="29949-140">Pokud se nepoužila nová verze, aplikace se už nebude muset extrahovat druhou dobu.</span><span class="sxs-lookup"><span data-stu-id="29949-140">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="29949-141">Chcete-li publikovat soubor s jedním souborem, nastavte `PublishSingleFile` v projektu nebo na příkazovém řádku pomocí příkazu `dotnet publish`:</span><span class="sxs-lookup"><span data-stu-id="29949-141">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="29949-142">-nebo-</span><span class="sxs-lookup"><span data-stu-id="29949-142">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="29949-143">Další informace o publikování v jednom souboru najdete v [dokumentu návrhu sady prostředků s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="29949-143">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="29949-144">Propojení sestavení</span><span class="sxs-lookup"><span data-stu-id="29949-144">Assembly linking</span></span>

<span data-ttu-id="29949-145">Sada .NET Core 3.0 SDK je dodávána s nástrojem, který umožňuje zmenšit velikost aplikací analýzou IL a oříznutím nepoužívaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="29949-145">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="29949-146">Samostatné aplikace zahrnují vše potřebné ke spuštění kódu, aniž by bylo nutné nainstalovat rozhraní .NET do hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="29949-146">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="29949-147">Ale hodně, kolikrát aplikace jenom vyžaduje malou podmnožinu rozhraní, a další nepoužívané knihovny by se daly odebrat.</span><span class="sxs-lookup"><span data-stu-id="29949-147">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="29949-148">Rozhraní .NET Core nyní obsahuje nastavení, které bude používat nástroj [linkeru Il](https://github.com/mono/linker) ke kontrole Il vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="29949-148">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="29949-149">Tento nástroj zjistí, jaký kód je požadován, a poté ořízne nepoužívané knihovny.</span><span class="sxs-lookup"><span data-stu-id="29949-149">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="29949-150">Tento nástroj může významně snížit velikost nasazení některých aplikací.</span><span class="sxs-lookup"><span data-stu-id="29949-150">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="29949-151">Chcete-li tento nástroj povolit, přidejte do projektu nastavení `<PublishTrimmed>` a publikujte samostatně uzavřenou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="29949-151">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="29949-152">Příklad: základní šablona projektu "Hello World", která je součástí, je-li publikována, má velikost přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="29949-152">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="29949-153">Když použijete `<PublishTrimmed>`, zmenší se velikost na přibližně 30 MB.</span><span class="sxs-lookup"><span data-stu-id="29949-153">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="29949-154">Je důležité vzít v úvahu, že aplikace nebo architektury (včetně ASP.NET Core a WPF), které používají reflexi nebo související dynamické funkce, budou často přerušit při oříznutí.</span><span class="sxs-lookup"><span data-stu-id="29949-154">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="29949-155">K tomuto zlomku dochází, protože linker neví o tomto dynamickém chování a nemůže určit, které typy rozhraní jsou pro reflexi vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="29949-155">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="29949-156">Nástroj linkeru IL se dá nakonfigurovat tak, aby se na tento scénář dozvěděl.</span><span class="sxs-lookup"><span data-stu-id="29949-156">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="29949-157">Nad všemi ostatními nezapomeňte aplikaci otestovat po jejím oříznutí.</span><span class="sxs-lookup"><span data-stu-id="29949-157">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="29949-158">Další informace o nástroji linkeru IL naleznete v [dokumentaci](https://aka.ms/dotnet-illink) nebo v úložišti [mono/linker]( https://github.com/mono/linker) .</span><span class="sxs-lookup"><span data-stu-id="29949-158">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="29949-159">Vrstvená kompilace</span><span class="sxs-lookup"><span data-stu-id="29949-159">Tiered compilation</span></span>

<span data-ttu-id="29949-160">[Vrstvená kompilace](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) je ve výchozím nastavení zapnuté pomocí .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="29949-160">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="29949-161">Tato funkce umožňuje modulu runtime pružně použít kompilátor JIT (just-in-time) k zajištění lepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="29949-161">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="29949-162">Hlavní výhodou vrstvené kompilace je poskytnout dva způsoby jitting metod: v úrovni nižší kvality, ale rychlejší, nebo na vyšší kvalitu, ale na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="29949-162">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="29949-163">Kvalita odkazuje na to, jak dobře je metoda optimalizovaná.</span><span class="sxs-lookup"><span data-stu-id="29949-163">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="29949-164">TC pomáhá zlepšit výkon aplikace, když projde různými fázemi provádění, od spuštění po stabilním stavu.</span><span class="sxs-lookup"><span data-stu-id="29949-164">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="29949-165">Když je vrstvená kompilace zakázána, každá metoda je kompilována jedním způsobem, který je v průběhu spuštění posunut na výkon ustáleného stavu.</span><span class="sxs-lookup"><span data-stu-id="29949-165">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="29949-166">Když je povolený TC, platí následující chování pro kompilaci metody při spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="29949-166">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="29949-167">Pokud má metoda předem kompilovaný kód nebo [ReadyToRun](#readytorun-images), použije se předgenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="29949-167">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="29949-168">V opačném případě je metoda zpracovaných kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="29949-168">Otherwise, the method is jitted.</span></span> <span data-ttu-id="29949-169">Tyto metody jsou obvykle Obecné v rámci hodnotových typů.</span><span class="sxs-lookup"><span data-stu-id="29949-169">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="29949-170">*Rychlá kompilátor JIT* rychleji generuje kvalitní (nebo méně optimalizovaný) kód.</span><span class="sxs-lookup"><span data-stu-id="29949-170">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="29949-171">V rozhraní .NET Core 3,0 je rychlá technologie JIT standardně povolena pro metody, které neobsahují smyčky a jsou upřednostňovány při spuštění.</span><span class="sxs-lookup"><span data-stu-id="29949-171">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="29949-172">Plně optimalizovatelný kompilátor JIT vytváří vyšší kvalitu (nebo více optimalizovaného) kódu pomaleji.</span><span class="sxs-lookup"><span data-stu-id="29949-172">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="29949-173">Pro metody, kde by se nepoužila rychlá JIT (například pokud je metoda s atributem <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), se používá plně optimalizující kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="29949-173">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="29949-174">U často volaných metod kompilátor za běhu nakonec vytvoří plně optimalizovaný kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="29949-174">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="29949-175">Optimalizovaný kód pak nahradí předem kompilovaný kód pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="29949-175">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="29949-176">Kód generovaný rychlou JIT může běžet pomaleji, přidělit více paměti nebo použít více místa v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="29949-176">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="29949-177">V případě problémů můžete vypnout rychlou JIT pomocí této vlastnosti MSBuild v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="29949-177">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="29949-178">Chcete-li úplně zakázat použití TC, použijte tuto vlastnost MSBuild v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="29949-178">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="29949-179">Změníte-li tato nastavení v souboru projektu, bude pravděpodobně nutné provést čisté sestavení, aby se nové nastavení projevilo (odstraňte adresáře `obj` a `bin` a znovu sestavit).</span><span class="sxs-lookup"><span data-stu-id="29949-179">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="29949-180">Další informace o konfiguraci kompilace v době běhu naleznete v tématu [Možnosti konfigurace běhu pro kompilaci](../run-time-config/compilation.md).</span><span class="sxs-lookup"><span data-stu-id="29949-180">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="29949-181">ReadyToRun image</span><span class="sxs-lookup"><span data-stu-id="29949-181">ReadyToRun images</span></span>

<span data-ttu-id="29949-182">Můžete zlepšit čas spuštění aplikace .NET Core kompilováním sestavení aplikace jako formátu ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="29949-182">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="29949-183">R2R je forma kompilace v čase před zahájením (AOT).</span><span class="sxs-lookup"><span data-stu-id="29949-183">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="29949-184">R2R binární soubory zlepšují výkon při spuštění tím, že snižují množství práce, které kompilátor JIT (just-in-time) potřebuje k tomu, aby se vaše aplikace načítají.</span><span class="sxs-lookup"><span data-stu-id="29949-184">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="29949-185">Binární soubory obsahují podobný nativní kód v porovnání s tím, co by kompilátor JIT vytvořil.</span><span class="sxs-lookup"><span data-stu-id="29949-185">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="29949-186">R2R binární soubory jsou však větší, protože obsahují kód pro mezilehlé jazyky (IL), který je stále potřeba pro některé scénáře, a nativní verzi stejného kódu.</span><span class="sxs-lookup"><span data-stu-id="29949-186">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="29949-187">R2R je k dispozici pouze v případě, že publikujete samostatnou aplikaci, která cílí na konkrétní běhové prostředí (RID), jako je Linux x64 nebo Windows x64.</span><span class="sxs-lookup"><span data-stu-id="29949-187">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="29949-188">Chcete-li zkompilovat projekt jako ReadyToRun, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="29949-188">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="29949-189">Přidejte do projektu nastavení `<PublishReadyToRun>`:</span><span class="sxs-lookup"><span data-stu-id="29949-189">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="29949-190">Publikujte samostatně uzavřenou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="29949-190">Publish a self-contained app.</span></span> <span data-ttu-id="29949-191">Tento příkaz například vytvoří samostatnou aplikaci pro 64 verzi Windows:</span><span class="sxs-lookup"><span data-stu-id="29949-191">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="29949-192">Omezení pro různé platformy a architektury</span><span class="sxs-lookup"><span data-stu-id="29949-192">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="29949-193">Kompilátor ReadyToRun v současné době nepodporuje cílení na více platforem.</span><span class="sxs-lookup"><span data-stu-id="29949-193">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="29949-194">Je nutné kompilovat na daném cíli.</span><span class="sxs-lookup"><span data-stu-id="29949-194">You must compile on a given target.</span></span> <span data-ttu-id="29949-195">Například pokud chcete image R2R pro Windows x64, musíte v tomto prostředí spustit příkaz publikovat.</span><span class="sxs-lookup"><span data-stu-id="29949-195">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="29949-196">Výjimky pro cílení na více platforem:</span><span class="sxs-lookup"><span data-stu-id="29949-196">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="29949-197">Systém Windows x64 lze použít ke kompilaci imagí Windows ARM32, ARM64 a x86.</span><span class="sxs-lookup"><span data-stu-id="29949-197">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="29949-198">K kompilování imagí Windows ARM32 lze použít systém Windows x86.</span><span class="sxs-lookup"><span data-stu-id="29949-198">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="29949-199">Linux x64 lze použít ke kompilaci imagí ARM32 a ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="29949-199">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="29949-200">Modul runtime/sada SDK</span><span class="sxs-lookup"><span data-stu-id="29949-200">Runtime/SDK</span></span>

### <a name="major-version-roll-forward"></a><span data-ttu-id="29949-201">Hlavní verze – posunutí – posun</span><span class="sxs-lookup"><span data-stu-id="29949-201">Major-version Roll Forward</span></span>

<span data-ttu-id="29949-202">.NET Core 3.0 zavádí funkci pro výslovný souhlas, která umožňuje aplikaci přejít na nejnovější hlavní verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="29949-202">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="29949-203">Kromě toho bylo přidáno nové nastavení, které řídí, jak se ve vaší aplikaci aplikuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="29949-203">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="29949-204">Dá se nakonfigurovat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29949-204">This can be configured in the following ways:</span></span>

- <span data-ttu-id="29949-205">Vlastnost souboru projektu: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="29949-205">Project file property: `RollForward`</span></span>
- <span data-ttu-id="29949-206">Vlastnost konfiguračního souboru run-time: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="29949-206">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="29949-207">Proměnná prostředí: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="29949-207">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="29949-208">Argument příkazového řádku: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="29949-208">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="29949-209">Je nutné zadat jednu z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="29949-209">One of the following values must be specified.</span></span> <span data-ttu-id="29949-210">Pokud je nastavení vynecháno, je výchozí hodnota **podverze** .</span><span class="sxs-lookup"><span data-stu-id="29949-210">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="29949-211">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="29949-211">**LatestPatch**</span></span>\
<span data-ttu-id="29949-212">Vraťte se k nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="29949-212">Roll forward to the highest patch version.</span></span> <span data-ttu-id="29949-213">Tím se zakáže dílčí verze s posunem.</span><span class="sxs-lookup"><span data-stu-id="29949-213">This disables minor version roll forward.</span></span>
- <span data-ttu-id="29949-214">**Vedlejší**</span><span class="sxs-lookup"><span data-stu-id="29949-214">**Minor**</span></span>\
<span data-ttu-id="29949-215">V případě, že chybí požadovaná dílčí verze, převeďte nahoru na nejnižší nižší verzi.</span><span class="sxs-lookup"><span data-stu-id="29949-215">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="29949-216">Pokud je k dispozici požadovaná dílčí verze, použije se zásada **LatestPatch** .</span><span class="sxs-lookup"><span data-stu-id="29949-216">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="29949-217">**Hlavní**</span><span class="sxs-lookup"><span data-stu-id="29949-217">**Major**</span></span>\
<span data-ttu-id="29949-218">Pokud chybí požadovaná hlavní verze, převeďte ji nahoru na nejnižší nejvyšší hlavní verzi a nejnižší podverzi.</span><span class="sxs-lookup"><span data-stu-id="29949-218">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="29949-219">Pokud je k dispozici požadovaná hlavní verze, použije se **vedlejší** zásada.</span><span class="sxs-lookup"><span data-stu-id="29949-219">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="29949-220">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="29949-220">**LatestMinor**</span></span>\
<span data-ttu-id="29949-221">Převeďte do nejvyšší dílčí verze, i když je k dispozici požadovaná dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="29949-221">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="29949-222">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="29949-222">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="29949-223">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="29949-223">**LatestMajor**</span></span>\
<span data-ttu-id="29949-224">Převeďte do nejvyšší hlavní a nejvyšší dílčí verze, a to i v případě, že je k dispozici požadovaná hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="29949-224">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="29949-225">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="29949-225">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="29949-226">**Zakázat**</span><span class="sxs-lookup"><span data-stu-id="29949-226">**Disable**</span></span>\
<span data-ttu-id="29949-227">Nezadávejte vše.</span><span class="sxs-lookup"><span data-stu-id="29949-227">Don't roll forward.</span></span> <span data-ttu-id="29949-228">Vytvoří se jenom vazba na určenou verzi.</span><span class="sxs-lookup"><span data-stu-id="29949-228">Only bind to specified version.</span></span> <span data-ttu-id="29949-229">Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám.</span><span class="sxs-lookup"><span data-stu-id="29949-229">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="29949-230">Tato hodnota se doporučuje jenom pro testování.</span><span class="sxs-lookup"><span data-stu-id="29949-230">This value is only recommended for testing.</span></span>

<span data-ttu-id="29949-231">Kromě nastavení **Zakázat** bude pro všechna nastavení použita nejvyšší dostupná verze opravy.</span><span class="sxs-lookup"><span data-stu-id="29949-231">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="29949-232">Sestavení kopíruje závislosti</span><span class="sxs-lookup"><span data-stu-id="29949-232">Build copies dependencies</span></span>

<span data-ttu-id="29949-233">Příkaz `dotnet build` nyní kopíruje závislosti NuGet pro vaši aplikaci z mezipaměti NuGet do výstupní složky sestavení.</span><span class="sxs-lookup"><span data-stu-id="29949-233">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="29949-234">Dříve se závislosti zkopírovaly jenom jako součást `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="29949-234">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="29949-235">Existují některé operace, jako je propojování a publikování stránek Razor, které budou nadále vyžadovat publikování.</span><span class="sxs-lookup"><span data-stu-id="29949-235">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="29949-236">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="29949-236">Local tools</span></span>

<span data-ttu-id="29949-237">.NET Core 3.0 zavádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="29949-237">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="29949-238">Místní nástroje jsou podobné [globálním nástrojům](../tools/global-tools.md) , ale jsou přidruženy k určitému umístění na disku.</span><span class="sxs-lookup"><span data-stu-id="29949-238">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="29949-239">Místní nástroje nejsou globálně dostupné a distribuují se jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="29949-239">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="29949-240">Pokud jste si vyzkoušeli místní nástroje v rozhraní .NET Core 3.0 Preview 1 `dotnet tool restore` , `dotnet tool install`jako je třeba spuštění nebo, odstraňte složku mezipaměti místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="29949-240">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="29949-241">V opačném případě místní nástroje nebudou fungovat v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="29949-241">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="29949-242">Tato složka je umístěna v umístění:</span><span class="sxs-lookup"><span data-stu-id="29949-242">This folder is located at:</span></span>
>
> <span data-ttu-id="29949-243">V macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="29949-243">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="29949-244">Ve Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="29949-244">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="29949-245">Místní nástroje spoléhají na název souboru manifestu `dotnet-tools.json` v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="29949-245">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="29949-246">Tento soubor manifestu definuje nástroje, které jsou k dispozici v této složce a níže.</span><span class="sxs-lookup"><span data-stu-id="29949-246">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="29949-247">Můžete distribuovat soubor manifestu s vaším kódem, aby bylo zajištěno, že kdokoli, kdo spolupracuje s vaším kódem, může obnovit a použít stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="29949-247">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="29949-248">U globálních i místních nástrojů se vyžaduje kompatibilní verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="29949-248">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="29949-249">Mnoho nástrojů, které jsou aktuálně na NuGet.org Target pro .NET Core Runtime 2.1.</span><span class="sxs-lookup"><span data-stu-id="29949-249">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="29949-250">Pokud chcete tyto nástroje nainstalovat globálně nebo lokálně, budete si muset nainstalovat [modul runtime .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="29949-250">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="29949-251">Menší velikosti haldy uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="29949-251">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="29949-252">Výchozí velikost haldy systému uvolňování paměti byla snížena z výsledku rozhraní .NET Core s menším množstvím paměti.</span><span class="sxs-lookup"><span data-stu-id="29949-252">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="29949-253">Tato změna se lépe zarovnává s rozpočtem přidělení 0. generace s moderními velikostmi mezipaměti procesoru.</span><span class="sxs-lookup"><span data-stu-id="29949-253">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="29949-254">Podpora velkokapacitních stránek uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="29949-254">Garbage Collection Large Page support</span></span>

<span data-ttu-id="29949-255">Velké stránky (označované také jako velké stránky na platformě Linux) jsou funkce, ve které může operační systém vytvořit oblasti paměti větší než velikost nativní stránky (často 4K), aby se zlepšil výkon aplikace požadující tyto velké stránky.</span><span class="sxs-lookup"><span data-stu-id="29949-255">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="29949-256">Systém uvolňování paměti se teď dá nakonfigurovat s nastavením **GCLargePages** jako funkce výslovného souhlasu, která se rozhodne přidělit velké stránky ve Windows.</span><span class="sxs-lookup"><span data-stu-id="29949-256">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="29949-257">Windows Desktop & COM</span><span class="sxs-lookup"><span data-stu-id="29949-257">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="29949-258">.NET Core SDK Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="29949-258">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="29949-259">Instalační program MSI pro Windows se od verze .NET Core 3.0 změnil.</span><span class="sxs-lookup"><span data-stu-id="29949-259">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="29949-260">Instalační programy sady SDK teď upgradují verze sady SDK, které jsou na místě.</span><span class="sxs-lookup"><span data-stu-id="29949-260">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="29949-261">Pásma funkcí jsou definována ve *stovkách* v oddílu *patch* tohoto čísla verze.</span><span class="sxs-lookup"><span data-stu-id="29949-261">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="29949-262">Například **3.0. _101_**  a **3.0. _201_**  jsou verze ve dvou různých pruzích funkcí během **3.0. _101_**  a **3.0. _199_**  jsou ve stejném pásmu funkcí.</span><span class="sxs-lookup"><span data-stu-id="29949-262">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="29949-263">A při .NET Core SDK **3.0. _101_**  je nainstalováno, .NET Core SDK **3.0. _100_**  se odebere z počítače, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="29949-263">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="29949-264">Při .NET Core SDK **3.0. _200_**  je nainstalována na stejném počítači .NET Core SDK **3.0. _101_**  nebude odebráno.</span><span class="sxs-lookup"><span data-stu-id="29949-264">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="29949-265">Další informace o tom, jak se správou verzí, najdete v tématu Přehled toho, [jak je verze .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="29949-265">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="29949-266">Plocha Windows</span><span class="sxs-lookup"><span data-stu-id="29949-266">Windows desktop</span></span>

<span data-ttu-id="29949-267">.NET Core 3.0 podporuje desktopové aplikace Windows pomocí Windows Presentation Foundation (WPF) a model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="29949-267">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="29949-268">Tyto architektury také podporují použití moderních ovládacích prvků a Fluent stylování z knihovny XAML uživatelského rozhraní systému Windows (WinUI) přes [ostrovy XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="29949-268">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="29949-269">Součást Desktop systému Windows je součástí sady Windows .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="29949-269">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="29949-270">Novou aplikaci WPF nebo model Windows Forms můžete vytvořit pomocí následujících `dotnet` příkazů:</span><span class="sxs-lookup"><span data-stu-id="29949-270">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="29949-271">Visual Studio 2019 přidává **nové šablony projektů** pro .NET Core 3.0 model Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="29949-271">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="29949-272">Další informace o tom, jak přenést existující aplikaci .NET Framework, naleznete v tématu [port WPF Projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [port model Windows Forms Projects](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="29949-272">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="29949-273">Vysoké rozlišení DPI pro WinForms</span><span class="sxs-lookup"><span data-stu-id="29949-273">WinForms high DPI</span></span>

<span data-ttu-id="29949-274">Aplikace .NET Core model Windows Forms můžou nastavit režim vysokého rozlišení DPI pomocí <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29949-274">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29949-275">Metoda `SetHighDpiMode` nastaví odpovídající režim vysoké úrovně DPI, pokud nastavení nebylo nastaveno jiným způsobem jako `App.Manifest` nebo P/Invoke před `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="29949-275">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="29949-276">Možné hodnoty `highDpiMode`, jak vyjadřují <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> výčtu:</span><span class="sxs-lookup"><span data-stu-id="29949-276">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="29949-277">Další informace o režimech vysokého rozlišení DPI najdete v tématu [vývoj desktopových aplikací s vysokým rozlišením v systému Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="29949-277">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="29949-278">Vytvořit komponenty COM</span><span class="sxs-lookup"><span data-stu-id="29949-278">Create COM components</span></span>

<span data-ttu-id="29949-279">Ve Windows teď můžete vytvářet spravované komponenty, které lze volat v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="29949-279">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="29949-280">Tato možnost je zásadní pro použití .NET Core s modely doplňku COM a také k zajištění parity s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29949-280">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="29949-281">Na rozdíl od .NET Framework, kde se *Knihovna Mscoree. dll* použila jako server com, .NET Core při sestavování komponenty com přidá nativní spouštěcí knihovnu DLL do adresáře *bin* .</span><span class="sxs-lookup"><span data-stu-id="29949-281">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="29949-282">Příklad vytvoření komponenty modelu COM a její využití naleznete v [ukázce modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="29949-282">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="29949-283">Nativní spolupráce Windows</span><span class="sxs-lookup"><span data-stu-id="29949-283">Windows Native Interop</span></span>

<span data-ttu-id="29949-284">Systém Windows nabízí bohatě nativní rozhraní API ve formě plochých rozhraní API jazyka C, COM a WinRT.</span><span class="sxs-lookup"><span data-stu-id="29949-284">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="29949-285">I když .NET Core podporuje **volání nespravovaného voláním**.NET Core 3.0, přidává možnost **vytvořit rozhraní API modelu COM** a **aktivovat rozhraní API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="29949-285">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="29949-286">Příklad kódu naleznete v [ukázce v aplikaci Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="29949-286">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="29949-287">Nasazení MSIX</span><span class="sxs-lookup"><span data-stu-id="29949-287">MSIX Deployment</span></span>

<span data-ttu-id="29949-288">[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="29949-288">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="29949-289">Dá se použít k nasazení desktopových aplikací .NET Core 3.0 do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="29949-289">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="29949-290">[Projekt pro balení aplikace pro systém Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), který je k dispozici v aplikaci Visual Studio 2019, umožňuje vytvářet balíčky MSIX pomocí aplikací .NET Core s využitím [vlastních součástí](../deploying/index.md#self-contained-deployments-scd) .</span><span class="sxs-lookup"><span data-stu-id="29949-290">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="29949-291">Soubor projektu .NET Core musí určovat podporované moduly runtime ve vlastnosti `<RuntimeIdentifiers>`:</span><span class="sxs-lookup"><span data-stu-id="29949-291">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="29949-292">Vylepšení systému Linux</span><span class="sxs-lookup"><span data-stu-id="29949-292">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="29949-293">Portu SerialPort pro Linux</span><span class="sxs-lookup"><span data-stu-id="29949-293">SerialPort for Linux</span></span>

<span data-ttu-id="29949-294">.NET Core 3.0 poskytuje základní podporu pro <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> systém Linux.</span><span class="sxs-lookup"><span data-stu-id="29949-294">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="29949-295">Dřív se .NET Core podporuje jenom pomocí `SerialPort` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="29949-295">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="29949-296">Další informace o omezené podpoře sériového portu v systému Linux najdete v tématu [#33146 problému GitHubu](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="29949-296">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="29949-297">Omezení paměti Docker a CGROUP</span><span class="sxs-lookup"><span data-stu-id="29949-297">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="29949-298">Provoz .NET Core 3.0 na platformě Linux s Docker funguje lépe s omezeními CGROUP paměti.</span><span class="sxs-lookup"><span data-stu-id="29949-298">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="29949-299">Spuštění kontejneru Docker s omezeními paměti, jako je například s `docker run -m`, mění způsob, jakým se aplikace .NET Core chová.</span><span class="sxs-lookup"><span data-stu-id="29949-299">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="29949-300">Výchozí velikost haldy systému uvolňování paměti (GC): maximálně 20 MB nebo 75% limitu paměti v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="29949-300">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="29949-301">Explicitní velikost lze nastavit jako absolutní číslo nebo procento limitu CGROUP.</span><span class="sxs-lookup"><span data-stu-id="29949-301">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="29949-302">Minimální velikost rezervovaného segmentu na haldě GC je 16 MB.</span><span class="sxs-lookup"><span data-stu-id="29949-302">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="29949-303">Tato velikost snižuje počet hald, které jsou vytvořeny na počítačích.</span><span class="sxs-lookup"><span data-stu-id="29949-303">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="29949-304">Podpora GPIO pro maliny PI</span><span class="sxs-lookup"><span data-stu-id="29949-304">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="29949-305">Do NuGet byly vydány dva balíčky, které můžete použít pro GPIO programování:</span><span class="sxs-lookup"><span data-stu-id="29949-305">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="29949-306">System. Device. GPIO</span><span class="sxs-lookup"><span data-stu-id="29949-306">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="29949-307">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="29949-307">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="29949-308">Balíčky GPIO obsahují rozhraní API pro zařízení *GPIO*, *SPI*, *I2C*a *PWM* .</span><span class="sxs-lookup"><span data-stu-id="29949-308">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="29949-309">Balíček vazeb IoT zahrnuje vazby zařízení.</span><span class="sxs-lookup"><span data-stu-id="29949-309">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="29949-310">Další informace najdete v [úložišti GitHubu zařízení](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="29949-310">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="29949-311">Podpora ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="29949-311">ARM64 Linux support</span></span>

<span data-ttu-id="29949-312">.NET Core 3.0 přidává podporu pro ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="29949-312">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="29949-313">Primární případ použití pro ARM64 je aktuálně ve scénářích IoT.</span><span class="sxs-lookup"><span data-stu-id="29949-313">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="29949-314">Další informace najdete v tématu [stav .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="29949-314">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="29949-315">[Image Docker pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="29949-315">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="29949-316">**ARM64** Podpora Windows není ještě dostupná.</span><span class="sxs-lookup"><span data-stu-id="29949-316">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="29949-317">Zabezpečení –</span><span class="sxs-lookup"><span data-stu-id="29949-317">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="29949-318">TLS 1.3 & OpenSSL 1.1.1 v systému Linux</span><span class="sxs-lookup"><span data-stu-id="29949-318">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="29949-319">.NET Core teď využívá [podporu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), pokud je dostupná v daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="29949-319">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="29949-320">S protokolem TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="29949-320">With TLS 1.3:</span></span>

- <span data-ttu-id="29949-321">Časy připojení se zlepšily s omezenou špičkou odezvy mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="29949-321">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="29949-322">Vylepšené zabezpečení kvůli odebrání různých zastaralých a nezabezpečených kryptografických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="29949-322">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="29949-323">V případě, že je k dispozici, .NET Core 3.0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**nebo **OpenSSL 1.0.2** v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="29949-323">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="29949-324">Pokud je k dispozici služba **OpenSSL 1.1.1** <xref:System.Net.Security.SslStream?displayProperty=nameWithType> , budou v obou <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> typech použity **protokoly TLS 1.3** (za předpokladu, že klient i server podporují protokol **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="29949-324">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29949-325">Windows a macOS ještě nepodporují **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="29949-325">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="29949-326">Až bude podpora k dispozici, bude .NET Core 3.0 podporovat **TLS 1.3** v těchto operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="29949-326">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="29949-327">Následující C# příklad 8.0 ukazuje rozhraní .NET Core 3.0 v Ubuntu 18.10, které <https://www.cloudflare.com>se připojuje k:</span><span class="sxs-lookup"><span data-stu-id="29949-327">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="29949-328">Kryptografická šifry</span><span class="sxs-lookup"><span data-stu-id="29949-328">Cryptography ciphers</span></span>

<span data-ttu-id="29949-329">.NET 3,0 přidává podporu pro šifry **AES-GCM** a **AES-ccm** , implementovaná pomocí <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> a <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="29949-329">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="29949-330">Tyto algoritmy jsou jak [ověřené šifrování, tak i algoritmy AEAD (Association data)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="29949-330">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="29949-331">Následující kód demonstruje použití `AesGcm` šifry k šifrování a dešifrování náhodných dat.</span><span class="sxs-lookup"><span data-stu-id="29949-331">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="29949-332">Import/export kryptografického klíče</span><span class="sxs-lookup"><span data-stu-id="29949-332">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="29949-333">.NET Core 3.0 podporuje import a export asymetrických veřejných a privátních klíčů ze standardních formátů.</span><span class="sxs-lookup"><span data-stu-id="29949-333">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="29949-334">Nemusíte používat certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="29949-334">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="29949-335">Všechny typy klíčů, jako jsou *RSA*, *DSA*, *ECDSA*a *ECDiffieHellman*, podporují následující formáty:</span><span class="sxs-lookup"><span data-stu-id="29949-335">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="29949-336">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="29949-336">**Public Key**</span></span>
  - <span data-ttu-id="29949-337">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="29949-337">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="29949-338">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="29949-338">**Private key**</span></span>
  - <span data-ttu-id="29949-339">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="29949-339">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="29949-340">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="29949-340">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="29949-341">Klíče RSA podporují i:</span><span class="sxs-lookup"><span data-stu-id="29949-341">RSA keys also support:</span></span>

- <span data-ttu-id="29949-342">**Veřejný klíč**</span><span class="sxs-lookup"><span data-stu-id="29949-342">**Public Key**</span></span>
  - <span data-ttu-id="29949-343">RSAPublicKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="29949-343">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="29949-344">**Privátní klíč**</span><span class="sxs-lookup"><span data-stu-id="29949-344">**Private key**</span></span>
  - <span data-ttu-id="29949-345">RSAPrivateKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="29949-345">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="29949-346">Metody exportu vytváří binární data kódovaná v kódování DER a metody importu očekávají stejné.</span><span class="sxs-lookup"><span data-stu-id="29949-346">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="29949-347">Pokud je klíč uložený v textovém formátu PEM, volající bude muset před voláním metody import kódování Base64 a dekódovat obsah.</span><span class="sxs-lookup"><span data-stu-id="29949-347">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="29949-348">Soubory **PKCS # 8** lze kontrolovat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> a soubory **PFX/PKCS # 12** lze zkontrolovat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29949-348">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29949-349">Soubory **PFX/PKCS # 12** se můžou manipulovat s <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29949-349">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="29949-350">Změny rozhraní API .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="29949-350">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="29949-351">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="29949-351">Ranges and indices</span></span>

<span data-ttu-id="29949-352">Nový typ <xref:System.Index?displayProperty=nameWithType> lze použít k indexování.</span><span class="sxs-lookup"><span data-stu-id="29949-352">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="29949-353">Můžete vytvořit jednu z `int`, která se počítá od začátku, nebo s předponou `^` operátor (C#), která se počítá od konce:</span><span class="sxs-lookup"><span data-stu-id="29949-353">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="29949-354">K dispozici je také typ <xref:System.Range?displayProperty=nameWithType>, který se skládá ze dvou hodnot `Index`, jeden pro začátek a druhý pro konec a je možné ho zapsat pomocí výrazu `x..y` rozsahu (C#).</span><span class="sxs-lookup"><span data-stu-id="29949-354">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="29949-355">Pak můžete indexovat pomocí `Range`, který vytvoří řez:</span><span class="sxs-lookup"><span data-stu-id="29949-355">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="29949-356">Další informace najdete v [kurzu rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="29949-356">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="29949-357">Asynchronní streamy</span><span class="sxs-lookup"><span data-stu-id="29949-357">Async streams</span></span>

<span data-ttu-id="29949-358"><xref:System.Collections.Generic.IAsyncEnumerable%601> typ je nová asynchronní verze <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="29949-358">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="29949-359">Jazyk vám umožňuje `await foreach` přes `IAsyncEnumerable<T>` využívat jejich prvky a použít `yield return` pro vytváření elementů.</span><span class="sxs-lookup"><span data-stu-id="29949-359">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="29949-360">Následující příklad ukazuje produkci a spotřebu asynchronních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="29949-360">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="29949-361">Příkaz `foreach` je asynchronní a sám používá `yield return` k tvorbě asynchronního datového proudu pro volající.</span><span class="sxs-lookup"><span data-stu-id="29949-361">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="29949-362">Tento vzor (použití `yield return`) je doporučeným modelem pro vytváření asynchronních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="29949-362">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="29949-363">Kromě toho, že je možné `await foreach`, můžete také vytvořit asynchronní iterátory, například iterátor, který vrátí `IAsyncEnumerable/IAsyncEnumerator`, který můžete `await` a `yield` v.</span><span class="sxs-lookup"><span data-stu-id="29949-363">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="29949-364">Pro objekty, které je třeba uvolnit, můžete použít `IAsyncDisposable`, které implementují různé typy BCL, například `Stream` a `Timer`.</span><span class="sxs-lookup"><span data-stu-id="29949-364">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="29949-365">Další informace najdete v [kurzu asynchronní streamy](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="29949-365">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="29949-366">IEEE s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="29949-366">IEEE Floating-point</span></span>

<span data-ttu-id="29949-367">Rozhraní API s plovoucí desetinnou čárkou se aktualizují tak, aby odpovídalo [revizi IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="29949-367">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="29949-368">Cílem těchto změn je vystavit všechny **požadované** operace a zajistit, aby byly vyhovující požadavkům standardu IEEE. Další informace o vylepšeních s plovoucí desetinnou čárkou naleznete v příspěvku na blogu [.NET Core 3,0 v oblasti analýzy a formátování plovoucí desetinné](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) čárky.</span><span class="sxs-lookup"><span data-stu-id="29949-368">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="29949-369">Mezi aktualizace pro analýzu a formátování patří:</span><span class="sxs-lookup"><span data-stu-id="29949-369">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="29949-370">Správně Analyzujte a zaokrouhlujte vstupy libovolné délky.</span><span class="sxs-lookup"><span data-stu-id="29949-370">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="29949-371">Správně Analyzujte a formátujete záporné hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="29949-371">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="29949-372">Správně Analyzujte `Infinity` a `NaN` provedením kontroly bez rozlišování velkých a malých písmen a povolením nepovinné předchozí `+`, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="29949-372">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="29949-373">Mezi nová rozhraní <xref:System.Math?displayProperty=nameWithType> API patří:</span><span class="sxs-lookup"><span data-stu-id="29949-373">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="29949-374"><xref:System.Math.BitIncrement(System.Double)> a <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="29949-374"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="29949-375">Odpovídá `nextUp` a `nextDown` operace IEEE.</span><span class="sxs-lookup"><span data-stu-id="29949-375">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="29949-376">Vrátí nejmenší číslo s plovoucí desetinnou čárkou, které porovná větší nebo menší než vstup (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="29949-376">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="29949-377">`Math.BitIncrement(0.0)` například vrátí `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="29949-377">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="29949-378"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> a <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="29949-378"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="29949-379">Odpovídá `maxNumMag` a `minNumMag` operace IEEE, vrací hodnotu, která je větší nebo menší v rozsahu dvou vstupů (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="29949-379">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="29949-380">`Math.MaxMagnitude(2.0, -3.0)` například vrátí `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="29949-380">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="29949-381">Odpovídá `logB` operace IEEE, která vrací celočíselnou hodnotu, vrátí protokol integrálního protokolu Base-2 vstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="29949-381">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="29949-382">Tato metoda je efektivně stejná jako `floor(log2(x))`, ale byla provedena s minimální chybou zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="29949-382">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="29949-383">Odpovídá `scaleB` operace IEEE, která přebírá celočíselnou hodnotu, vrátí efektivně `x * pow(2, n)`, ale provede se minimální chybou zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="29949-383">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="29949-384">Odpovídá `log2` operace IEEE, vrátí logaritmus o základu 2.</span><span class="sxs-lookup"><span data-stu-id="29949-384">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="29949-385">Minimalizuje chybu zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="29949-385">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="29949-386">Odpovídá `fma` operace IEEE, provádí přidaný násobek.</span><span class="sxs-lookup"><span data-stu-id="29949-386">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="29949-387">To znamená, že se `(x * y) + z` jako jediná operace, čímž se minimalizuje chyba zaokrouhlování.</span><span class="sxs-lookup"><span data-stu-id="29949-387">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="29949-388">Příklad je `FusedMultiplyAdd(1e308, 2.0, -1e308)`, který vrací `1e308`.</span><span class="sxs-lookup"><span data-stu-id="29949-388">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="29949-389">Regulární `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="29949-389">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="29949-390">Odpovídá `copySign` operace IEEE, vrátí hodnotu `x`, ale s znaménkem `y`.</span><span class="sxs-lookup"><span data-stu-id="29949-390">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="29949-391">Vnitřní objekty závislé na platformě .NET</span><span class="sxs-lookup"><span data-stu-id="29949-391">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="29949-392">Byla přidána rozhraní API, která umožňují přístup k určitým pokynům pro procesor orientovaným na výkon, jako jsou **SIMD** nebo sady **instrukcí pro manipulaci** .</span><span class="sxs-lookup"><span data-stu-id="29949-392">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="29949-393">Tyto pokyny vám pomůžou dosáhnout výrazného zlepšení výkonu v některých scénářích, jako je efektivní zpracování dat paralelně.</span><span class="sxs-lookup"><span data-stu-id="29949-393">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="29949-394">V případě potřeby se pomocí těchto pokynů Vylepšete knihovny .NET, aby se zlepšil výkon.</span><span class="sxs-lookup"><span data-stu-id="29949-394">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="29949-395">Další informace najdete v tématu věnovaném [vnitřním procesorům platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="29949-395">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="29949-396">Vylepšená rozhraní API verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="29949-396">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="29949-397">Počínaje rozhraním .NET Core 3.0 verze rozhraní API poskytovaná pomocí .NET Core nyní vrátí očekávané informace.</span><span class="sxs-lookup"><span data-stu-id="29949-397">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="29949-398">Příklad:</span><span class="sxs-lookup"><span data-stu-id="29949-398">For example:</span></span>

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
> <span data-ttu-id="29949-399">Zásadní změna.</span><span class="sxs-lookup"><span data-stu-id="29949-399">Breaking change.</span></span> <span data-ttu-id="29949-400">To je technicky zásadní změna, protože se změnilo schéma správy verzí.</span><span class="sxs-lookup"><span data-stu-id="29949-400">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="29949-401">Rychlá integrovaná podpora JSON</span><span class="sxs-lookup"><span data-stu-id="29949-401">Fast built-in JSON support</span></span>

<span data-ttu-id="29949-402">Uživatelé rozhraní .NET mají převážně na [Newtonsoft. JSON](https://www.newtonsoft.com/json) a další oblíbené knihovny JSON, které budou mít i nadále dobré možnosti.</span><span class="sxs-lookup"><span data-stu-id="29949-402">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="29949-403">`Newtonsoft.Json` používá řetězce .NET jako svůj základní datový typ, což je UTF-16 pod digestoří.</span><span class="sxs-lookup"><span data-stu-id="29949-403">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="29949-404">Nová integrovaná podpora JSON je vysoce výkonná, nízká alokace a funguje s textem JSON kódovaným ve formátu UTF-8.</span><span class="sxs-lookup"><span data-stu-id="29949-404">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="29949-405">Další informace o <xref:System.Text.Json> obor názvů a typy najdete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="29949-405">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="29949-406">Serializace JSON v .NET – přehled</span><span class="sxs-lookup"><span data-stu-id="29949-406">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="29949-407">[Postup serializace a deserializace JSON v rozhraní .NET](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="29949-407">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="29949-408">Postup migrace z Newtonsoft. JSON na System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="29949-408">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="29949-409">Podpora HTTP/2</span><span class="sxs-lookup"><span data-stu-id="29949-409">HTTP/2 support</span></span>

<span data-ttu-id="29949-410">Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> podporuje protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="29949-410">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="29949-411">Pokud je povolený protokol HTTP/2, vyjednává se verze protokolu HTTP prostřednictvím TLS/ALPN a protokol HTTP/2 se použije, pokud se server rozhodne ho použít.</span><span class="sxs-lookup"><span data-stu-id="29949-411">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="29949-412">Výchozí protokol zůstává HTTP/1.1, ale protokol HTTP/2 může být povolen dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="29949-412">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="29949-413">Nejdřív můžete nastavit zprávu požadavku HTTP na používání HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="29949-413">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="29949-414">V druhém případě můžete <xref:System.Net.Http.HttpClient> ve výchozím nastavení změnit na použití HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="29949-414">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="29949-415">V mnoha případech, kdy vyvíjíte aplikaci, chcete použít nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="29949-415">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="29949-416">Pokud víte, že cílový koncový bod bude používat protokol HTTP/2, můžete zapnout nezašifrovaná připojení pro HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="29949-416">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="29949-417">Můžete ji zapnout nastavením proměnné prostředí `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` na `1` nebo povolením v kontextu aplikace:</span><span class="sxs-lookup"><span data-stu-id="29949-417">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="29949-418">Další kroky</span><span class="sxs-lookup"><span data-stu-id="29949-418">Next steps</span></span>

- [<span data-ttu-id="29949-419">Přečtěte si o nejnovějších změnách mezi .NET Core 2,2 a 3,0.</span><span class="sxs-lookup"><span data-stu-id="29949-419">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="29949-420">Přečtěte si o nejnovějších změnách v .NET Core 3,0 pro aplikace model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="29949-420">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)
