---
title: Co je nového v rozhraní .NET Core 2.1
description: Další informace o nových funkcích v rozhraní .NET Core 2.1 nalezen.
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2018
ms.openlocfilehash: a7e0ae3c65a18376a7648198a43f1272a2bddafd
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696452"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="42700-103">Co je nového v rozhraní .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="42700-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="42700-104">.NET core 2.1 obsahuje vylepšení a nové funkce v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="42700-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="42700-105">Nástrojů</span><span class="sxs-lookup"><span data-stu-id="42700-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="42700-106">Dopředné posunutí</span><span class="sxs-lookup"><span data-stu-id="42700-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="42700-107">Nasazení</span><span class="sxs-lookup"><span data-stu-id="42700-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="42700-108">Kompatibilita sady Windows</span><span class="sxs-lookup"><span data-stu-id="42700-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="42700-109">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="42700-109">JIT compiler improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="42700-110">Rozhraní API změny</span><span class="sxs-lookup"><span data-stu-id="42700-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="42700-111">Nástrojů</span><span class="sxs-lookup"><span data-stu-id="42700-111">Tooling</span></span>

<span data-ttu-id="42700-112">.NET Core 2.1.300 SDK a nástrojů .NET Core 2.1, které jsou součástí obsahuje následující změny a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="42700-112">The .NET Core 2.1.300 SDK, the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="42700-113">Sestavení vylepšení výkonu</span><span class="sxs-lookup"><span data-stu-id="42700-113">Build performance improvements</span></span>

<span data-ttu-id="42700-114">Hlavní fokus .NET Core 2.1 je zvýšení výkonu době sestavení, zejména pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="42700-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="42700-115">Tato vylepšení výkonu platí pro obě sestavení příkazového řádku pomocí `dotnet build` a sestavení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42700-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="42700-116">Některé jednotlivé oblasti zlepšování patří:</span><span class="sxs-lookup"><span data-stu-id="42700-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="42700-117">Balíček asset překlad IP adres řešení pouze prostředky používané build, ne všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="42700-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="42700-118">Ukládání do mezipaměti odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="42700-118">Caching of assembly references.</span></span>

- <span data-ttu-id="42700-119">Použití sady SDK dlouho běžící sestavení serverů, které jsou procesy, které jsou rozmístěny napříč individuální `dotnet build` volání.</span><span class="sxs-lookup"><span data-stu-id="42700-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="42700-120">Odstraňují potřebu JIT – kompilace velké bloky kódu pokaždé, když `dotnet build` běží.</span><span class="sxs-lookup"><span data-stu-id="42700-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="42700-121">Vytvořit server pro procesy můžete automaticky ukončena s následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="42700-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="42700-122">Nové příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="42700-122">New CLI commands</span></span>

<span data-ttu-id="42700-123">Několik nástrojů, které byly k dispozici pouze na jednotlivých projektů za použití [ `DotnetCliToolReference` ](../tools/extensibility.md) jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="42700-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="42700-124">Mezi tyto nástroje patří:</span><span class="sxs-lookup"><span data-stu-id="42700-124">These tools include:</span></span>

- <span data-ttu-id="42700-125">`dotnet watch` poskytuje sledovací proces systému souboru, který čeká na soubor, který chcete změnit před provedením určenou sadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="42700-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="42700-126">Následující příkaz například automaticky znovu sestaví aktuální projekt a generuje podrobný výstup, vždy, když je soubor v ní změny:</span><span class="sxs-lookup"><span data-stu-id="42700-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="42700-127">Další informace najdete v tématu [ASP.NET Core vyvíjet aplikace pomocí sledování dotnet.](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="42700-127">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="42700-128">`dotnet dev-certs` generuje a spravuje certifikáty používané během vývoje v aplikacích ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="42700-128">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="42700-129">`dotnet user-secrets` spravuje tajných klíčů v tajný úložiště uživatele v aplikacích ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="42700-129">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="42700-130">`dotnet sql-cache` vytvoří tabulku a indexy v databázi Microsoft SQL Server má být použit pro distribuované ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="42700-130">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="42700-131">`dotnet ef` je nástroj pro správu databází, <xref:Microsoft.EntityFrameworkCore.DbContext> objekty a migrace v aplikacích Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="42700-131">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="42700-132">Další informace najdete v tématu [nástroje příkazového řádku .NET Core EF](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="42700-132">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="42700-133">Globální nástroje</span><span class="sxs-lookup"><span data-stu-id="42700-133">Global Tools</span></span>

<span data-ttu-id="42700-134">.NET core 2.1 podporuje *globální nástroje* – to znamená, vlastních nástrojů, které jsou k dispozici globálně z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="42700-134">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="42700-135">Model rozšiřitelnosti v předchozích verzích .NET Core zpřístupněn vlastních nástrojů na projektu na základě pouze pomocí [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="42700-135">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="42700-136">Chcete-li nainstalovat nástroj globální, je použít [instalace nástroje pro dotnet](..\tools\dotnet-tool-install.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="42700-136">To install a Global Tool, you use the [dotnet tool install](..\tools\dotnet-tool-install.md) command.</span></span> <span data-ttu-id="42700-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="42700-137">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="42700-138">Po instalaci nástroj můžete spustit z příkazového řádku zadáním názvu nástroj.</span><span class="sxs-lookup"><span data-stu-id="42700-138">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="42700-139">Další informace najdete v tématu [.NET Core globální nástroje Přehled](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="42700-139">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="single-source-tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="42700-140">Jediný zdroj nástrojů pro správu pomocí `dotnet tool` příkaz</span><span class="sxs-lookup"><span data-stu-id="42700-140">Single-source tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="42700-141">V rozhraní .NET Core 2.1, všechny operace nástroje pro použití `dotnet tool` příkaz.</span><span class="sxs-lookup"><span data-stu-id="42700-141">In .NET Core 2.1, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="42700-142">K dispozici jsou následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="42700-142">The following options are available:</span></span>

- <span data-ttu-id="42700-143">`dotnet tool install` Chcete-li nainstalovat nástroj.</span><span class="sxs-lookup"><span data-stu-id="42700-143">`dotnet tool install` to install a tool.</span></span>

- <span data-ttu-id="42700-144">`dotnet tool update` odinstalovat a znovu nainstalovat nástroj, který efektivně se aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="42700-144">`dotnet tool update` to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="42700-145">`dotnet tool list` seznam aktuálně nainstalovaných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="42700-145">`dotnet tool list` to list currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="42700-146">Dopředné posunutí</span><span class="sxs-lookup"><span data-stu-id="42700-146">Roll forward</span></span>

<span data-ttu-id="42700-147">Všechny aplikace .NET Core od verze rozhraní .NET 2.0 základní automaticky Posunutí vpřed na nejnovější *podverze* nainstalovaná v systému.</span><span class="sxs-lookup"><span data-stu-id="42700-147">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span> <span data-ttu-id="42700-148">To znamená pokud byla aplikace vytvořené s nástroji verze .NET Core není dostupná, je aplikace spuštěná proti nejnovější nainstalované vedlejší verzi.</span><span class="sxs-lookup"><span data-stu-id="42700-148">That is, if the .NET Core version that an application was built with is not present, the application runs against the latest installed minor version.</span></span> <span data-ttu-id="42700-149">Jinými slovy Pokud je aplikace vytvořené s .NET Core 2.0 a .NET Core 2.0, samotné se nenachází v hostitelském systému, ale .NET Core 2.1, aplikace bude spuštěna s .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="42700-149">In other words, if an application is built with .NET Core 2.0 and .NET Core 2.0 itself is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42700-150">Toto chování úplné dopředné nezávisle na verze preview.</span><span class="sxs-lookup"><span data-stu-id="42700-150">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="42700-151">Ani se nevztahuje na hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="42700-151">Nor does it apply to major releases.</span></span> <span data-ttu-id="42700-152">Aplikace .NET Core 1.0 by například Posunutí vpřed .NET Core 2.0 nebo .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="42700-152">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="42700-153">Můžete také zakázat podverze dopředné posunutí v jednom ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="42700-153">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="42700-154">Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` rovná 0, proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="42700-154">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable equal to 0,</span></span>

- <span data-ttu-id="42700-155">Přidejte následující řádek do souboru runtimeconfig.json:</span><span class="sxs-lookup"><span data-stu-id="42700-155">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="42700-156">Při použití [nástrojů příkazového řádku .NET Core](../tools/index.md), obsahují následující možnost pomocí příkazu .NET Core, například `run`:</span><span class="sxs-lookup"><span data-stu-id="42700-156">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="42700-157">Nasazení</span><span class="sxs-lookup"><span data-stu-id="42700-157">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="42700-158">Samostatný aplikace údržby</span><span class="sxs-lookup"><span data-stu-id="42700-158">Self-contained application servicing</span></span>

<span data-ttu-id="42700-159">`dotnet publish` nyní publikuje nezávislý aplikace s verzí obsluhované runtime.</span><span class="sxs-lookup"><span data-stu-id="42700-159">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="42700-160">Když publikujete samostatné aplikace pomocí .NET SDK 2.1 jádra, vaše aplikace obsahuje nejnovější verzi modulu runtime obsluhované známého této sady SDK.</span><span class="sxs-lookup"><span data-stu-id="42700-160">When you publish a self-contained application with the .NET Core 2.1 SDK, your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="42700-161">Při upgradu na nejnovější SDK, budete publikovat na nejnovější verzi modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42700-161">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="42700-162">To platí pro moduly runtime .NET Core 1.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="42700-162">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="42700-163">Samostatná publikování závisí na modulu runtime verze na NuGet.org. Není nutné mít obsluhované modul runtime na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="42700-163">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="42700-164">Pomocí .NET SDK 2.0 jádra, úplný a samostatný aplikace jsou publikovány s modulem runtime .NET Core 2.0.0 prostřednictvím je uvedeno jinou verzi `RuntimeFrameworkVersion` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="42700-164">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="42700-165">Pomocí této nové chování už musíte nastavit tuto vlastnost na vybrat vyšší verzi modulu runtime pro samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="42700-165">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="42700-166">Nejjednodušší způsob do budoucna, je vždy publikovat pomocí .NET SDK 2.1 jádra.</span><span class="sxs-lookup"><span data-stu-id="42700-166">The easiest approach going forward is to always publish with .NET Core 2.1 SDK.</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="42700-167">Kompatibilita sady Windows</span><span class="sxs-lookup"><span data-stu-id="42700-167">Windows Compatibility Pack</span></span>

<span data-ttu-id="42700-168">Pokud je to port existující kód z rozhraní .NET Framework na .NET Core, můžete použít [Windows kompatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="42700-168">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="42700-169">Poskytuje přístup na 20 000 další rozhraní API, než je k dispozici v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42700-169">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="42700-170">Tato rozhraní API obsahovat typy v <xref:System.Drawing?displayProperty="nameWithType"> obor názvů, <xref:System.Diagnostics.EventLog> třídy, rozhraní WMI, čítače výkonu, služby systému Windows a typy registru systému Windows a členů.</span><span class="sxs-lookup"><span data-stu-id="42700-170">These APIs include types in the <xref:System.Drawing?displayProperty="nameWithType"> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="42700-171">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="42700-171">JIT compiler improvements</span></span>

<span data-ttu-id="42700-172">.NET core zahrnuje novou technologií kompilátoru JIT názvem *vrstvené kompilace* (také označované jako *Adaptivní optimalizace*), může výrazně zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="42700-172">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span>

<span data-ttu-id="42700-173">Jeden z nejdůležitějších úkolů provádí kompilátoru za běhu je optimalizace provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="42700-173">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="42700-174">Pro kód málo používané cesty ale kompilátor může trávit déle než modulu runtime stráví spuštěním kódu neoptimalizované optimalizace kódu.</span><span class="sxs-lookup"><span data-stu-id="42700-174">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="42700-175">Vrstvený kompilace zavádí dvou fázích v JIT – kompilace:</span><span class="sxs-lookup"><span data-stu-id="42700-175">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="42700-176">A **první úroveň**, který generuje kód co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="42700-176">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="42700-177">A **druhé vrstvy**, který generuje optimalizovaného kódu pro tyto metody, které jsou spouštěny často.</span><span class="sxs-lookup"><span data-stu-id="42700-177">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="42700-178">Druhé vrstvy kompilace se provádí současně pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="42700-178">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="42700-179">Vrstvený kompilace pomocí .NET Core 2.1 aplikaci můžete otestovat nastavením následující proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="42700-179">You can test tiered compilation with a .NET Core 2.1 app by setting the following environment variable:</span></span>

```console
COMPlus_TieredCompilation="1"
```

## <a name="api-changes"></a><span data-ttu-id="42700-180">Rozhraní API změny</span><span class="sxs-lookup"><span data-stu-id="42700-180">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="42700-181">`Span<T>` A `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="42700-181">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="42700-182">.NET core 2.1 obsahuje některé nové typy, které práci s poli a dalších typů paměti mnohem efektivnější.</span><span class="sxs-lookup"><span data-stu-id="42700-182">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="42700-183">Nové typy patří:</span><span class="sxs-lookup"><span data-stu-id="42700-183">The new types include:</span></span>

- <span data-ttu-id="42700-184"><xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42700-184"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="42700-185"><xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42700-185"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="42700-186">Bez těchto typů, při předávání takové položky jako část pole nebo jeho část vyrovnávací paměti budete muset vytvořit kopii některé část dat před jeho odesláním metodu.</span><span class="sxs-lookup"><span data-stu-id="42700-186">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="42700-187">Tyto typy poskytují virtuální zobrazení data, která eliminuje potřebu další paměť přidělení a operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="42700-187">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="42700-188">Následující příklad používá <xref:System.Span%601> instance zajistit virtuální zobrazení 10 prvky pole.</span><span class="sxs-lookup"><span data-stu-id="42700-188">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="42700-189">Komprese Brotli</span><span class="sxs-lookup"><span data-stu-id="42700-189">Brotli compression</span></span>

<span data-ttu-id="42700-190">.NET core 2.1 přidává podporu pro Brotli komprese a dekomprese.</span><span class="sxs-lookup"><span data-stu-id="42700-190">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="42700-191">Brotli je algoritmus pro obecné účely beze ztrát komprese, která je definována v [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a podporuje většina webových prohlížečů a hlavní webové servery.</span><span class="sxs-lookup"><span data-stu-id="42700-191">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="42700-192">Můžete použít datový proud na základě <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> třídu nebo výkonné na základě rozpětí <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> a <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="42700-192">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="42700-193">Následující příklad ilustruje komprese s <xref:System.IO.Compression.BrotliStream> třídy:</span><span class="sxs-lookup"><span data-stu-id="42700-193">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="42700-194"><xref:System.IO.Compression.BrotliStream> Chování je stejné jako <xref:System.IO.Compression.DeflateStream> a <xref:System.IO.Compression.GZipStream>, což usnadňuje převést kód, který volá tyto rozhraní API pro <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="42700-194">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="42700-195">Kryptografie nové rozhraní API a vylepšení kryptografie</span><span class="sxs-lookup"><span data-stu-id="42700-195">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="42700-196">.NET core 2.1 zahrnuje množství vylepšení cryptography API:</span><span class="sxs-lookup"><span data-stu-id="42700-196">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="42700-197"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> je k dispozici v balíčku System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="42700-197"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="42700-198">Implementace je stejný jako <xref:System.Security.Cryptography.Pkcs.SignedCms> – třída v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42700-198">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="42700-199">Nové přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody přijímají identifikátor algoritmus hash povolit volající získat hodnoty kryptografického otisku certifikátu pomocí algoritmů než SHA-1.</span><span class="sxs-lookup"><span data-stu-id="42700-199">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="42700-200">Nové <xref:System.Span%601>-založené na kryptografii rozhraní API jsou k dispozici pro použití algoritmu hash, klíčem HMAC, kryptografické náhodné generování čísel, generování podpisů asymetrické, zpracování asymetrické podpis a šifrování RSA.</span><span class="sxs-lookup"><span data-stu-id="42700-200">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="42700-201">Výkon <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> je vylepšený o 15 % pomocí <xref:System.Span%601>– na základě implementace.</span><span class="sxs-lookup"><span data-stu-id="42700-201">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="42700-202">Nové <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> třída obsahuje dvě nové metody:</span><span class="sxs-lookup"><span data-stu-id="42700-202">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="42700-203"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> trvá pevné množství času se chcete vrátit všechny dva vstupy stejnou délku, takže je vhodné pro použití v kryptografických ověření předejdete přispívání do časování informace o kanálu straně.</span><span class="sxs-lookup"><span data-stu-id="42700-203"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="42700-204"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> je rutinou mažou paměti, která nelze optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="42700-204"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="42700-205">Statické <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> metoda výplněmi <xref:System.Span%601> s náhodných hodnot.</span><span class="sxs-lookup"><span data-stu-id="42700-205">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="42700-206"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Se teď podporuje na Linuxu a maxOS.</span><span class="sxs-lookup"><span data-stu-id="42700-206">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="42700-207">Elliptic Curve Diffie-Hellman (ECDH) je nyní k dispozici v <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> třídy rodiny.</span><span class="sxs-lookup"><span data-stu-id="42700-207">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="42700-208">Možnosti útoku je stejný jako v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42700-208">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="42700-209">Instance vrácený <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> můžete zašifrovat nebo dešifrovat s OAEP pomocí hodnotu hash SHA-2, a také vygenerovat nebo ověřit podpisy pomocí RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="42700-209">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="42700-210">Vylepšení Sockets</span><span class="sxs-lookup"><span data-stu-id="42700-210">Sockets improvements</span></span>

<span data-ttu-id="42700-211">.NET core zahrnuje nový typ, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>a přepsaná <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, které tvoří základ sítě vyšší úrovně rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="42700-211">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="42700-212"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, například je základem <xref:System.Net.Http.HttpClient> implementace.</span><span class="sxs-lookup"><span data-stu-id="42700-212"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="42700-213">V předchozích verzích .NET Core jsou vyšší úrovně rozhraní API založené na nativní implementace sítě.</span><span class="sxs-lookup"><span data-stu-id="42700-213">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="42700-214">Implementace sockets byla zavedená v rozhraní .NET Core 2.1 má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="42700-214">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="42700-215">Zlepšování významně zvýšit výkon ve srovnání s předchozí implementací.</span><span class="sxs-lookup"><span data-stu-id="42700-215">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="42700-216">Odstranění v závislosti na platformě, což zjednodušuje nasazení a údržby.</span><span class="sxs-lookup"><span data-stu-id="42700-216">Elimination on platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="42700-217">Konzistentní chování pro všechny platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42700-217">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="42700-218">Na základě Sockets <xref:System.Net.Http.SocketsHttpHandler> je výchozí implementace v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="42700-218">Sockets based on <xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="42700-219">Ale můžete nakonfigurovat aplikace pomocí starší <xref:System.Net.Http.HttpClientHandler> třída voláním <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> metoda:</span><span class="sxs-lookup"><span data-stu-id="42700-219">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

<span data-ttu-id="42700-220">Můžete taky prostředí proměnnou pro vyjádření výslovného nesouhlasu pomocí soketů implementací na základě <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="42700-220">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="42700-221">Chcete-li to provést, nastavte `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` buď `false` nebo rovna 0.</span><span class="sxs-lookup"><span data-stu-id="42700-221">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="42700-222">V systému Windows, můžete také použít <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, které závisí na nativní implementaci nebo <xref:System.Net.Http.SocketsHttpHandler> třída předáním instance třídy k <xref:System.Net.Http.HttpClient> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="42700-222">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="42700-223">V systému macOS a Linux, můžete konfigurovat pouze <xref:System.Net.Http.HttpClient> na základě procesů.</span><span class="sxs-lookup"><span data-stu-id="42700-223">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="42700-224">V systému Linux, je třeba nasadit [libcurl](https://curl.haxx.se/libcurl/) Pokud chcete použít starý <xref:System.Net.Http.HttpClient> implementace.</span><span class="sxs-lookup"><span data-stu-id="42700-224">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="42700-225">(Je nainstalovaná s .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="42700-225">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="42700-226">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42700-226">See also</span></span>

[<span data-ttu-id="42700-227">Co je nového v .NET Core</span><span class="sxs-lookup"><span data-stu-id="42700-227">What's new in .NET Core</span></span>](index.md)  
[<span data-ttu-id="42700-228">Nové funkce v EF základní 2.1</span><span class="sxs-lookup"><span data-stu-id="42700-228">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
[<span data-ttu-id="42700-229">Co je nového v technologii ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="42700-229">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
