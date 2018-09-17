---
title: Co je nového v .NET Core 2.1
description: Informace o nových funkcích v .NET Core 2.1.
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 850df87666c5beb0594f0672d8f558c11653f973
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746767"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="1c501-103">Co je nového v .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1c501-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="1c501-104">.NET core 2.1 obsahuje vylepšení a nových funkcí v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="1c501-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="1c501-105">Nástroje</span><span class="sxs-lookup"><span data-stu-id="1c501-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="1c501-106">Posunout vpřed</span><span class="sxs-lookup"><span data-stu-id="1c501-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="1c501-107">Nasazení</span><span class="sxs-lookup"><span data-stu-id="1c501-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="1c501-108">Windows Compatibility Pack</span><span class="sxs-lookup"><span data-stu-id="1c501-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="1c501-109">Vylepšení kompilace JIT</span><span class="sxs-lookup"><span data-stu-id="1c501-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="1c501-110">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1c501-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="1c501-111">Nástroje</span><span class="sxs-lookup"><span data-stu-id="1c501-111">Tooling</span></span>

<span data-ttu-id="1c501-112">.NET Core 2.1 SDK (v 2.1.300), nástroje, které jsou součástí rozhraní .NET Core 2.1 obsahuje následující změny a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="1c501-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="1c501-113">Vylepšení výkonu sestavení</span><span class="sxs-lookup"><span data-stu-id="1c501-113">Build performance improvements</span></span>

<span data-ttu-id="1c501-114">Hlavní fokus .NET Core 2.1 je zkracuje čas sestavení, zejména pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c501-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="1c501-115">Tato vylepšení výkonu platí pro obě sestavení příkazového řádku pomocí `dotnet build` a sestavení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c501-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="1c501-116">Některé jednotlivé oblasti vylepšení patří:</span><span class="sxs-lookup"><span data-stu-id="1c501-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="1c501-117">Rozlišení prostředků balíčku řešení pouze prostředky používané sestavení, ne všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="1c501-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="1c501-118">Ukládání do mezipaměti odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c501-118">Caching of assembly references.</span></span>

- <span data-ttu-id="1c501-119">Použití sady SDK dlouho probíhající sestavení servery, které jsou procesy, které jsou rozmístěny napříč jednotlivých `dotnet build` volání.</span><span class="sxs-lookup"><span data-stu-id="1c501-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="1c501-120">Tyto funkce odstraňují potřebu JIT-kompilovat velkých bloků kódu pokaždé, když `dotnet build` běží.</span><span class="sxs-lookup"><span data-stu-id="1c501-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="1c501-121">Buildovací server, které procesy mohou automaticky ukončeny následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="1c501-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="1c501-122">Nové příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="1c501-122">New CLI commands</span></span>

<span data-ttu-id="1c501-123">Různé nástroje, které byly k dispozici pouze v jednotlivých projektů pomocí [ `DotnetCliToolReference` ](../tools/extensibility.md) jsou teď k dispozici jako součást sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1c501-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="1c501-124">Mezi tyto nástroje patří:</span><span class="sxs-lookup"><span data-stu-id="1c501-124">These tools include:</span></span>

- <span data-ttu-id="1c501-125">`dotnet watch` poskytuje sledování systému souborů, které čeká na soubor, chcete-li změnit před spuštěním určenou sadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="1c501-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="1c501-126">Následující příkaz například automaticky znovu sestaví projekt a vygeneruje podrobný výstup pokaždé, když se změní soubor v ní:</span><span class="sxs-lookup"><span data-stu-id="1c501-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="1c501-127">Poznámka: `--` možnost, která předchází `--verbose` možnost.</span><span class="sxs-lookup"><span data-stu-id="1c501-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="1c501-128">Vymezuje možnosti předané přímo `dotnet watch` z argumentů, které jsou předány do podřízeného `dotnet` procesu.</span><span class="sxs-lookup"><span data-stu-id="1c501-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="1c501-129">Bez toho `--verbose` možnost se vztahuje `dotnet watch` příkaz nebyl `dotnet build` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1c501-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="1c501-130">Další informace najdete v tématu [aplikace vyvíjet ASP.NET Core s využitím dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="1c501-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="1c501-131">`dotnet dev-certs` generuje a spravuje certifikáty používané při vývoji aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c501-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="1c501-132">`dotnet user-secrets` slouží ke správě tajných kódů v úložišti tajných kódů uživatelů v aplikacích ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c501-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="1c501-133">`dotnet sql-cache` vytvoří tabulky a indexy v databázi Microsoft SQL serveru, který má být použit pro distribuované ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1c501-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="1c501-134">`dotnet ef` je nástroj pro správu databází, <xref:Microsoft.EntityFrameworkCore.DbContext> objekty a migrace v aplikacích Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="1c501-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="1c501-135">Další informace najdete v tématu [nástroje příkazového řádku .NET Core EF](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="1c501-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="1c501-136">Globální nástroje</span><span class="sxs-lookup"><span data-stu-id="1c501-136">Global Tools</span></span>

<span data-ttu-id="1c501-137">.NET core 2.1 podporuje *globální nástroje* – to znamená, vlastních nástrojů, které jsou k dispozici globálně z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1c501-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="1c501-138">Model rozšiřitelnosti v předchozích verzích .NET Core zpřístupněn vlastních nástrojů na základě jednotlivých projektů pouze pomocí [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="1c501-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="1c501-139">Instalovat nástroj globální, použijte [instalace nástrojů dotnet](..\tools\dotnet-tool-install.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="1c501-139">To install a Global Tool, you use the [dotnet tool install](..\tools\dotnet-tool-install.md) command.</span></span> <span data-ttu-id="1c501-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1c501-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="1c501-141">Po instalaci, můžete nástroj spustit z příkazového řádku tak, že zadáte název nástroje.</span><span class="sxs-lookup"><span data-stu-id="1c501-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="1c501-142">Další informace najdete v tématu [globální nástroje .NET Core přehled](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1c501-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="1c501-143">Nástroj pro správu s `dotnet tool` příkaz</span><span class="sxs-lookup"><span data-stu-id="1c501-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="1c501-144">V rozhraní .NET Core SDK 2.1 (v 2.1.300), použít všechny operace nástroje `dotnet tool` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1c501-144">In .NET Core SDK 2.1 (v 2.1.300), all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="1c501-145">Jsou k dispozici následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="1c501-145">The following options are available:</span></span>

- <span data-ttu-id="1c501-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) Chcete-li nainstalovat nástroj.</span><span class="sxs-lookup"><span data-stu-id="1c501-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="1c501-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) Chcete-li odinstalovat a znovu nainstalovat nástroj, který efektivně aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="1c501-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="1c501-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) seznam aktuálně nainstalovaných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="1c501-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="1c501-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) Odinstalace nástrojů pro aktuálně nainstalovanou.</span><span class="sxs-lookup"><span data-stu-id="1c501-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="1c501-150">Posunout vpřed</span><span class="sxs-lookup"><span data-stu-id="1c501-150">Roll forward</span></span>

<span data-ttu-id="1c501-151">Všechny aplikace .NET Core od verze rozhraní příkazového řádku .NET Core 2.0 automaticky posunout vpřed na nejnovější verzi *podverze* nainstalované v systému.</span><span class="sxs-lookup"><span data-stu-id="1c501-151">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="1c501-152">Počínaje .NET Core 2.0, pokud není k dispozici za běhu verze .NET Core, která byla aplikace vytvořena, aplikace automaticky spouští nainstaluje *podverze* .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c501-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="1c501-153">Jinými slovy Pokud je aplikace sestavena s .NET Core 2.0 a .NET Core 2.0 není k dispozici v hostitelském systému, ale je .NET Core 2.1, aplikace bude spuštěna s .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="1c501-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c501-154">Toto chování vpřed neplatí pro verze preview.</span><span class="sxs-lookup"><span data-stu-id="1c501-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="1c501-155">Ani se nevztahuje na hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="1c501-155">Nor does it apply to major releases.</span></span> <span data-ttu-id="1c501-156">Aplikace .NET Core 1.0 by například posunout vpřed a .NET Core 2.0, .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="1c501-156">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="1c501-157">Můžete také zakázat podverze Posunutí vpřed v libovolné ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="1c501-157">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="1c501-158">Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` proměnné prostředí na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="1c501-158">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to 0.</span></span>

- <span data-ttu-id="1c501-159">Přidejte následující řádek do souboru runtimeconfig.json:</span><span class="sxs-lookup"><span data-stu-id="1c501-159">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="1c501-160">Při použití [nástroje rozhraní příkazového řádku .NET Core](../tools/index.md), patří například následující možnost pomocí příkazu .NET Core `run`:</span><span class="sxs-lookup"><span data-stu-id="1c501-160">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="1c501-161">Nasazení</span><span class="sxs-lookup"><span data-stu-id="1c501-161">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="1c501-162">Údržba samostatné aplikace</span><span class="sxs-lookup"><span data-stu-id="1c501-162">Self-contained application servicing</span></span>

<span data-ttu-id="1c501-163">`dotnet publish` nyní publikuje samostatné aplikace s obsluhované modulem runtime verze.</span><span class="sxs-lookup"><span data-stu-id="1c501-163">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="1c501-164">Při publikování samostatné aplikace pomocí sady .NET Core 2.1 SDK (v 2.1.300), vaše aplikace obsahuje nejnovější verze modulu runtime obsluhované platná pro tuto sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="1c501-164">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="1c501-165">Když upgradujete na nejnovější sadu SDK, budete publikovat pomocí nejnovější verze modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c501-165">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="1c501-166">To platí pro moduly runtime .NET Core 1.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="1c501-166">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="1c501-167">Samostatné publikování se spoléhá na verze modulu runtime na NuGet.org. Nemusíte mít obsluhované runtime na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="1c501-167">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="1c501-168">Pomocí sady .NET Core 2.0 SDK, samostatné aplikace jsou publikované s modulem runtime .NET Core 2.0.0 jinou verzi není určena prostřednictvím `RuntimeFrameworkVersion` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1c501-168">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="1c501-169">S toto nové chování už nebude potřeba nastavte tuto vlastnost na zvolte vyšší verze modulu runtime pro samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c501-169">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="1c501-170">Nejjednodušší způsob do budoucna, je vždy publikovat s .NET Core 2.1 SDK (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="1c501-170">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="1c501-171">Další informace najdete v tématu [samostatná nasazení modulu runtime dopředné posunutí](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="1c501-171">For more information, see [Self-contained deploymnet runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="1c501-172">Windows Compatibility Pack</span><span class="sxs-lookup"><span data-stu-id="1c501-172">Windows Compatibility Pack</span></span>

<span data-ttu-id="1c501-173">Když portujete existující kód z rozhraní .NET Framework do .NET Core, můžete použít [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="1c501-173">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="1c501-174">Poskytuje přístup k 20 000 další rozhraní API, než je k dispozici v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c501-174">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="1c501-175">Tato rozhraní API patří typy v <xref:System.Drawing?displayProperty=nameWithType> obor názvů, <xref:System.Diagnostics.EventLog> třídy, rozhraní WMI, čítače výkonu, služby Windows a Windows registru typy a členy.</span><span class="sxs-lookup"><span data-stu-id="1c501-175">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="1c501-176">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="1c501-176">JIT compiler improvements</span></span>

<span data-ttu-id="1c501-177">.NET core zahrnuje novou technologii kompilátor JIT volá *vrstvené kompilace* (označované také jako *Adaptivní optimalizace*), který může výrazně zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="1c501-177">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="1c501-178">Nastavení přihlášení je vrstvený kompilace.</span><span class="sxs-lookup"><span data-stu-id="1c501-178">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="1c501-179">Mezi důležité úlohy prováděné kompilátorem JIT je optimalizace spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="1c501-179">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="1c501-180">Cesty málo používané kódu ale může kompilátor věnovat víc času optimalizace kódu, než modul runtime stráví spuštěním neoptimalizované kódu.</span><span class="sxs-lookup"><span data-stu-id="1c501-180">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="1c501-181">Vrstvené kompilace zavádí dvě fáze kompilace JIT:</span><span class="sxs-lookup"><span data-stu-id="1c501-181">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="1c501-182">A **první úroveň**, který generuje kód co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="1c501-182">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="1c501-183">A **druhé vrstvy**, který generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často.</span><span class="sxs-lookup"><span data-stu-id="1c501-183">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="1c501-184">Druhá vrstva kompilace provádí paralelní pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="1c501-184">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="1c501-185">Můžete se rozhodnout do vrstvené kompilace v některém ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="1c501-185">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="1c501-186">Pokud chcete použít ve všech projektech, které používají sadu .NET Core 2.1 SDK vrstvenou kompilace, nastavte následující proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="1c501-186">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="1c501-187">Použití vrstveného kompilace na základě jednotlivých projektů, přidejte `<TieredCompilation>` vlastnost `<PropertyGroup>` část souboru projektu MSBuild, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1c501-187">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="1c501-188">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1c501-188">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="1c501-189">`Span<T>` a `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="1c501-189">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="1c501-190">.NET core 2.1 zahrnuje několik nových typů, které usnadňuje práci s poli a jiné druhy paměti mnohem efektivnější.</span><span class="sxs-lookup"><span data-stu-id="1c501-190">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="1c501-191">Nové typy patří:</span><span class="sxs-lookup"><span data-stu-id="1c501-191">The new types include:</span></span>

- <span data-ttu-id="1c501-192"><xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c501-192"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="1c501-193"><xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c501-193"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1c501-194">Bez těchto typů, při předávání takové položky jako část pole nebo jeho část vyrovnávací paměti budete muset vytvořit kopii nějakou část dat před předáním na metodu.</span><span class="sxs-lookup"><span data-stu-id="1c501-194">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="1c501-195">Tyto typy poskytují virtuální zobrazení data, která eliminuje potřebu další paměť přidělení a operací kopírování.</span><span class="sxs-lookup"><span data-stu-id="1c501-195">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="1c501-196">Následující příklad používá <xref:System.Span%601> instance virtuální zviditelňují 10 prvků pole.</span><span class="sxs-lookup"><span data-stu-id="1c501-196">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="1c501-197">Brotli komprese</span><span class="sxs-lookup"><span data-stu-id="1c501-197">Brotli compression</span></span>

<span data-ttu-id="1c501-198">.NET core 2.1 přidává podporu pro Brotli komprese a dekomprese.</span><span class="sxs-lookup"><span data-stu-id="1c501-198">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="1c501-199">Brotli je algoritmus pro obecné účely beze ztrát komprese, který je definován v [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a podporuje většina webových prohlížečů a hlavní webové servery.</span><span class="sxs-lookup"><span data-stu-id="1c501-199">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="1c501-200">Můžete použít datový proud podle <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> třídy nebo vysoce výkonné založených na rozsahu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> a <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="1c501-200">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="1c501-201">Následující příklad ukazuje komprese se <xref:System.IO.Compression.BrotliStream> třídy:</span><span class="sxs-lookup"><span data-stu-id="1c501-201">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="1c501-202"><xref:System.IO.Compression.BrotliStream> Chování je stejné jako <xref:System.IO.Compression.DeflateStream> a <xref:System.IO.Compression.GZipStream>, což usnadňuje převést kód, který volá tato rozhraní API pro <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="1c501-202">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="1c501-203">Šifrování nových rozhraní API a vylepšení kryptografie</span><span class="sxs-lookup"><span data-stu-id="1c501-203">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="1c501-204">.NET core 2.1 obsahuje četná vylepšení rozhraní API kryptografie:</span><span class="sxs-lookup"><span data-stu-id="1c501-204">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="1c501-205"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> je k dispozici v balíčku System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="1c501-205"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="1c501-206">Implementace je stejné jako <xref:System.Security.Cryptography.Pkcs.SignedCms> třídy v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c501-206">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="1c501-207">Nové přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody přijímají identifikátor algoritmu hash a umožnit tak volajícím získat hodnoty kryptografického otisku certifikátu pomocí algoritmů než SHA-1.</span><span class="sxs-lookup"><span data-stu-id="1c501-207">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="1c501-208">Nové <xref:System.Span%601>-založené na kryptografii rozhraní API jsou k dispozici pro vytvoření hodnoty hash, HMAC kryptografických náhodné generování čísel, generování asymetrického podpisu, zpracování asymetrického podpisu a šifrování RSA.</span><span class="sxs-lookup"><span data-stu-id="1c501-208">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="1c501-209">Výkon <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> je vylepšené o 15 % pomocí <xref:System.Span%601>– na základě implementace.</span><span class="sxs-lookup"><span data-stu-id="1c501-209">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="1c501-210">Nové <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> třída obsahuje dvě nové metody:</span><span class="sxs-lookup"><span data-stu-id="1c501-210">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="1c501-211"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> používá pevné množství času má být vrácen pro jakékoli dva vstupy stejnou délku, která je vhodná pro použití v ověření šifrování, aby přispívání do vypršení časového limitu na straně kanálu informace.</span><span class="sxs-lookup"><span data-stu-id="1c501-211"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="1c501-212"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> je paměť vymazání rutinu, která nemůže být optimalizované.</span><span class="sxs-lookup"><span data-stu-id="1c501-212"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="1c501-213">Statické <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> metoda výplně <xref:System.Span%601> s náhodné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1c501-213">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="1c501-214"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Je nyní podporována v systému Linux a maxOS.</span><span class="sxs-lookup"><span data-stu-id="1c501-214">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="1c501-215">Skupina Diffie-Hellman eliptické křivky (ECDH) je teď dostupná v <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> třídy řady.</span><span class="sxs-lookup"><span data-stu-id="1c501-215">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="1c501-216">Styčné plochy je stejný jako v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c501-216">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="1c501-217">Instanci vrácenou <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> můžete šifrování nebo dešifrování pomocí OAEP pomocí algoritmu SHA-2 digest, jakož i generovat nebo ověřování podpisů pomocí RSA služby PSS.</span><span class="sxs-lookup"><span data-stu-id="1c501-217">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="1c501-218">Vylepšení Sockets</span><span class="sxs-lookup"><span data-stu-id="1c501-218">Sockets improvements</span></span>

<span data-ttu-id="1c501-219">.NET core zahrnuje nový typ <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>a přepsaný <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, které tvoří základ sítí vyšší úrovně rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1c501-219">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="1c501-220"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, například je základem <xref:System.Net.Http.HttpClient> implementace.</span><span class="sxs-lookup"><span data-stu-id="1c501-220"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="1c501-221">V předchozích verzích .NET Core byly vyšší úrovně rozhraní API podle nativní implementace sítě.</span><span class="sxs-lookup"><span data-stu-id="1c501-221">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="1c501-222">Implementaci soketů zavedena v rozhraní .NET Core 2.1 má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="1c501-222">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="1c501-223">Významné výkonnostní zlepšení ve srovnání s předchozím implementací.</span><span class="sxs-lookup"><span data-stu-id="1c501-223">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="1c501-224">Úplného oproštění od závislostí platformy, která zjednodušuje nasazení a obsluhy.</span><span class="sxs-lookup"><span data-stu-id="1c501-224">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="1c501-225">Konzistentní chování na všech platformách .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c501-225">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="1c501-226"><xref:System.Net.Http.SocketsHttpHandler> je výchozí implementace v .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="1c501-226"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="1c501-227">Ale můžete nakonfigurovat vaší aplikaci použít starší <xref:System.Net.Http.HttpClientHandler> třídy voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="1c501-227">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="1c501-228">Můžete použít také prostředí proměnnou můžete kdykoliv zrušit pomocí soketů implementací na základě <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="1c501-228">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="1c501-229">Chcete-li to provést, nastavte `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` buď `false` nebo 0.</span><span class="sxs-lookup"><span data-stu-id="1c501-229">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="1c501-230">Na Windows, můžete také použít <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, které spoléhá na nativní implementaci nebo <xref:System.Net.Http.SocketsHttpHandler> třídy to předáním instance třídy, která se <xref:System.Net.Http.HttpClient> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1c501-230">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="1c501-231">V Linuxu a macOS, můžete konfigurovat pouze <xref:System.Net.Http.HttpClient> na základě na úrovni jednotlivého procesu.</span><span class="sxs-lookup"><span data-stu-id="1c501-231">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="1c501-232">V systému Linux, budete muset nasadit [libcurl](https://curl.haxx.se/libcurl/) Pokud chcete používat starý <xref:System.Net.Http.HttpClient> implementace.</span><span class="sxs-lookup"><span data-stu-id="1c501-232">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="1c501-233">(To se instaluje s .NET Core 2.0).</span><span class="sxs-lookup"><span data-stu-id="1c501-233">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="1c501-234">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c501-234">See also</span></span>

* [<span data-ttu-id="1c501-235">Co je nového v .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c501-235">What's new in .NET Core</span></span>](index.md)  
* [<span data-ttu-id="1c501-236">Novinky v EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1c501-236">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
* [<span data-ttu-id="1c501-237">Co je nového v ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1c501-237">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
