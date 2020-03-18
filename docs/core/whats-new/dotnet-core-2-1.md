---
title: Co je nového v .NET Core 2.1
description: Další informace o nových funkcích v rozhraní .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 54ace52fc6a8f4614c1f762b65453979bcb92c7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398865"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="868fe-103">Co je nového v .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="868fe-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="868fe-104">.NET Core 2.1 obsahuje vylepšení a nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="868fe-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="868fe-105">Nástroje</span><span class="sxs-lookup"><span data-stu-id="868fe-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="868fe-106">Posunout vpřed</span><span class="sxs-lookup"><span data-stu-id="868fe-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="868fe-107">Nasazení</span><span class="sxs-lookup"><span data-stu-id="868fe-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="868fe-108">Sada Kompatibilita systému Windows</span><span class="sxs-lookup"><span data-stu-id="868fe-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="868fe-109">Vylepšení kompilace JIT</span><span class="sxs-lookup"><span data-stu-id="868fe-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="868fe-110">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="868fe-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="868fe-111">Nástroje</span><span class="sxs-lookup"><span data-stu-id="868fe-111">Tooling</span></span>

<span data-ttu-id="868fe-112">Sada .NET Core 2.1 SDK (v 2.1.300), nástroj, který je součástí .NET Core 2.1, obsahuje následující změny a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="868fe-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="868fe-113">Vytváření vylepšení výkonu</span><span class="sxs-lookup"><span data-stu-id="868fe-113">Build performance improvements</span></span>

<span data-ttu-id="868fe-114">Hlavním zaměřením .NET Core 2.1 je zlepšení výkonu sestavení, zejména pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="868fe-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="868fe-115">Tato vylepšení výkonu platí pro sestavení `dotnet build` příkazového řádku pomocí a sestavení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="868fe-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="868fe-116">Některé jednotlivé oblasti zlepšení patří:</span><span class="sxs-lookup"><span data-stu-id="868fe-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="868fe-117">Pro řešení aktiv balíčku řešení pouze prostředky používané sestavení, nikoli všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="868fe-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="868fe-118">Ukládání odkazů na sestavení do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="868fe-118">Caching of assembly references.</span></span>

- <span data-ttu-id="868fe-119">Použití dlouho běžících serverů sestavení sady SDK, což `dotnet build` jsou procesy, které se rozprostírají mezi jednotlivými vyvoláními.</span><span class="sxs-lookup"><span data-stu-id="868fe-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="868fe-120">Eliminují potřebu JIT kompilovat `dotnet build` velké bloky kódu při každém spuštění.</span><span class="sxs-lookup"><span data-stu-id="868fe-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="868fe-121">Procesy sestavení serveru lze automaticky ukončit pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="868fe-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="868fe-122">Nové příkazy příkazu cli</span><span class="sxs-lookup"><span data-stu-id="868fe-122">New CLI commands</span></span>

<span data-ttu-id="868fe-123">Řada nástrojů, které byly k dispozici pouze `DotnetCliToolReference` na základě projektu pomocí jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="868fe-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="868fe-124">Mezi tyto nástroje patří:</span><span class="sxs-lookup"><span data-stu-id="868fe-124">These tools include:</span></span>

- <span data-ttu-id="868fe-125">`dotnet watch`Poskytuje sledovací proces systému souborů, který čeká na změnu souboru před provedením určené sady příkazů.</span><span class="sxs-lookup"><span data-stu-id="868fe-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="868fe-126">Například následující příkaz automaticky znovu vytvoří aktuální projekt a generuje podrobný výstup při každé změně souboru v něm:</span><span class="sxs-lookup"><span data-stu-id="868fe-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="868fe-127">Všimněte `--` si možnosti, která předchází `--verbose` možnost.</span><span class="sxs-lookup"><span data-stu-id="868fe-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="868fe-128">Vymezuje možnosti `dotnet watch` předané přímo příkazu z `dotnet` argumentů, které jsou předány podřízenému procesu.</span><span class="sxs-lookup"><span data-stu-id="868fe-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="868fe-129">Bez ní `--verbose` se tato možnost `dotnet watch` vztahuje na `dotnet build` příkaz, nikoli na příkaz.</span><span class="sxs-lookup"><span data-stu-id="868fe-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="868fe-130">Další informace najdete [v tématu Vývoj aplikací ASP.NET Core pomocí hodinek Dotnet](/aspnet/core/tutorials/dotnet-watch)Watch .</span><span class="sxs-lookup"><span data-stu-id="868fe-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="868fe-131">`dotnet dev-certs`generuje a spravuje certifikáty používané při vývoji v ASP.NET základních aplikacích.</span><span class="sxs-lookup"><span data-stu-id="868fe-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="868fe-132">`dotnet user-secrets`spravuje tajné klíče v úložišti tajných klíčů uživatele v ASP.NET základních aplikacích.</span><span class="sxs-lookup"><span data-stu-id="868fe-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="868fe-133">`dotnet sql-cache`vytvoří tabulku a indexuje v databázi serveru Microsoft SQL Server, která se použije pro distribuované ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="868fe-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="868fe-134">`dotnet ef`je nástroj pro správu <xref:Microsoft.EntityFrameworkCore.DbContext> databází, objektů a migrací v aplikacích Core frameworku entit.</span><span class="sxs-lookup"><span data-stu-id="868fe-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="868fe-135">Další informace naleznete v tématu [EF Core .NET Nástroje příkazového řádku](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="868fe-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="868fe-136">Globální nástroje</span><span class="sxs-lookup"><span data-stu-id="868fe-136">Global Tools</span></span>

<span data-ttu-id="868fe-137">.NET Core 2.1 podporuje *globální nástroje* – to znamená vlastní nástroje, které jsou k dispozici globálně z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="868fe-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="868fe-138">Model rozšiřitelnosti v předchozích verzích rozhraní .NET Core zpřístupnil `DotnetCliToolReference`vlastní nástroje pro projekt pouze pomocí .</span><span class="sxs-lookup"><span data-stu-id="868fe-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="868fe-139">Chcete-li nainstalovat globální nástroj, použijte příkaz [instalace nástroje dotnet.](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="868fe-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="868fe-140">Například:</span><span class="sxs-lookup"><span data-stu-id="868fe-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="868fe-141">Po instalaci lze nástroj spustit z příkazového řádku zadáním názvu nástroje.</span><span class="sxs-lookup"><span data-stu-id="868fe-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="868fe-142">Další informace naleznete v tématu [.NET Core Global Tools overview](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="868fe-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="868fe-143">Správa nástrojů `dotnet tool` pomocí příkazu</span><span class="sxs-lookup"><span data-stu-id="868fe-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="868fe-144">V sdk.net core 2.1 sdk všechny nástroje operace použít `dotnet tool` příkaz.</span><span class="sxs-lookup"><span data-stu-id="868fe-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="868fe-145">K dispozici jsou následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="868fe-145">The following options are available:</span></span>

- <span data-ttu-id="868fe-146">[`dotnet tool install`](../tools/dotnet-tool-install.md)pro instalaci nástroje.</span><span class="sxs-lookup"><span data-stu-id="868fe-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="868fe-147">[`dotnet tool update`](../tools/dotnet-tool-update.md)odinstalovat a znovu nainstalovat nástroj, který jej účinně aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="868fe-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="868fe-148">[`dotnet tool list`](../tools/dotnet-tool-list.md)do seznamu aktuálně nainstalovaných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="868fe-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="868fe-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)odinstalovat aktuálně nainstalované nástroje.</span><span class="sxs-lookup"><span data-stu-id="868fe-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="868fe-150">Posunout vpřed</span><span class="sxs-lookup"><span data-stu-id="868fe-150">Roll forward</span></span>

<span data-ttu-id="868fe-151">Všechny aplikace .NET Core začínající na rozhraní .NET Core 2.0 se automaticky přepínají na nejnovější *dílčí verzi* nainstalovanou v systému.</span><span class="sxs-lookup"><span data-stu-id="868fe-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="868fe-152">Počínaje rozhraním .NET Core 2.0, pokud verze rozhraní .NET Core, se kterou byla aplikace vytvořena, není k dispozici za běhu, aplikace se automaticky spustí s nejnovější *nainstalovanou dílčí verzí* rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="868fe-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="868fe-153">Jinými slovy, pokud je aplikace vytvořena s rozhraním .NET Core 2.0 a rozhraní .NET Core 2.0 není v hostitelském systému k dispozici, ale je .NET Core 2.1, aplikace je spuštěna s rozhraním .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="868fe-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="868fe-154">Toto chování pro přechod vpřed se nevztahuje na verze preview.</span><span class="sxs-lookup"><span data-stu-id="868fe-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="868fe-155">Ve výchozím nastavení se také nevztahuje na hlavní verze, ale to lze změnit pomocí níže uvedených nastavení.</span><span class="sxs-lookup"><span data-stu-id="868fe-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="868fe-156">Toto chování můžete změnit změnou nastavení pro roll-forward na žádný kandidát sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="868fe-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="868fe-157">Dostupná nastavení jsou:</span><span class="sxs-lookup"><span data-stu-id="868fe-157">The available settings are:</span></span>

- <span data-ttu-id="868fe-158">`0`- zakázat chování dílčí verze roll-forward.</span><span class="sxs-lookup"><span data-stu-id="868fe-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="868fe-159">Při tomto nastavení se aplikace vytvořená pro rozhraní .NET Core 2.0.0 posune dopředu na .NET Core 2.0.1, ale ne na .NET Core 2.2.0 nebo .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="868fe-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="868fe-160">`1`- povolit chování dílčí verze roll-forward.</span><span class="sxs-lookup"><span data-stu-id="868fe-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="868fe-161">Toto je výchozí hodnota pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="868fe-161">This is the default value for the setting.</span></span> <span data-ttu-id="868fe-162">Při tomto nastavení se aplikace vytvořená pro rozhraní .NET Core 2.0.0 posune dopředu buď na .NET Core 2.0.1 nebo .NET Core 2.2.0, v závislosti na tom, který z nich je nainstalován, ale nebude se posunout dopředu na .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="868fe-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="868fe-163">`2`- povolit chování dílčí ch a hlavních verzí.</span><span class="sxs-lookup"><span data-stu-id="868fe-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="868fe-164">Pokud je nastavena, jsou považovány i různé hlavní verze, takže aplikace vytvořená pro rozhraní .NET Core 2.0.0 se posune dopředu na .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="868fe-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="868fe-165">Toto nastavení můžete upravit libovolným ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="868fe-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="868fe-166">Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` proměnnou prostředí na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="868fe-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="868fe-167">Do souboru *.runtimeconfig.json* přidejte následující řádek s požadovanou hodnotou:</span><span class="sxs-lookup"><span data-stu-id="868fe-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="868fe-168">Při použití [rozhraní PŘÍKAZU .NET Core](../tools/index.md)přidejte do příkazu .NET `run`Core následující možnost s požadovanou hodnotou, například :</span><span class="sxs-lookup"><span data-stu-id="868fe-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="868fe-169">Posun out verze opravy je nezávislý na tomto nastavení a provádí se po použití jakékoli potenciální vedlejší nebo hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="868fe-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="868fe-170">Nasazení</span><span class="sxs-lookup"><span data-stu-id="868fe-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="868fe-171">Samostatný servis aplikací</span><span class="sxs-lookup"><span data-stu-id="868fe-171">Self-contained application servicing</span></span>

<span data-ttu-id="868fe-172">`dotnet publish`nyní publikuje samostatné aplikace s obsluhovnou runtime verzí.</span><span class="sxs-lookup"><span data-stu-id="868fe-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="868fe-173">Při publikování samostatné aplikace s .NET Core 2.1 SDK (v 2.1.300), aplikace obsahuje nejnovější verzi runtime s obsluhou známou tímto sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="868fe-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="868fe-174">Při upgradu na nejnovější sadu SDK budete publikovat s nejnovější verzí za běhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="868fe-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="868fe-175">To platí pro běhové časy .NET Core 1.0 a novější.</span><span class="sxs-lookup"><span data-stu-id="868fe-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="868fe-176">Samostatné publikování závisí na runtime verzích na NuGet.org. Není nutné mít v počítači servisní runtime.</span><span class="sxs-lookup"><span data-stu-id="868fe-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="868fe-177">Pomocí sady .NET Core 2.0 SDK jsou samostatné aplikace publikovány pomocí runtime .NET Core 2.0.0, pokud není prostřednictvím vlastnosti `RuntimeFrameworkVersion` zadána jiná verze.</span><span class="sxs-lookup"><span data-stu-id="868fe-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="868fe-178">S tímto novým chováním již nebudete muset tuto vlastnost nastavit, abyste vybrali vyšší verzi runtime pro samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="868fe-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="868fe-179">Nejjednodušší přístup do budoucna je vždy publikovat s .NET Core 2.1 SDK (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="868fe-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="868fe-180">Další informace naleznete [v tématu Samostatné nasazení runtime posun vpřed](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="868fe-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="868fe-181">Sada Kompatibilita systému Windows</span><span class="sxs-lookup"><span data-stu-id="868fe-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="868fe-182">Při přenosu existujícího kódu z rozhraní .NET Framework do rozhraní .NET Core můžete použít [sadu Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="868fe-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="868fe-183">Poskytuje přístup k 20 000 více rozhraní API, než jsou k dispozici v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="868fe-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="868fe-184">Tato api zahrnují typy <xref:System.Drawing?displayProperty=nameWithType> v oboru <xref:System.Diagnostics.EventLog> názvů, třídy, služby WMI, čítače výkonu, služby systému Windows a typy a členy registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="868fe-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="868fe-185">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="868fe-185">JIT compiler improvements</span></span>

<span data-ttu-id="868fe-186">.NET Core obsahuje novou technologii kompilátoru JIT nazvanou *vrstvená kompilace (označovaná* také jako *adaptivní optimalizace),* která může výrazně zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="868fe-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="868fe-187">Vrstvená kompilace je nastavení opt-in.</span><span class="sxs-lookup"><span data-stu-id="868fe-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="868fe-188">Jedním z důležitých úkolů prováděných kompilátorem JIT je optimalizace spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="868fe-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="868fe-189">Pro málo používané cesty kódu však kompilátor může strávit více času optimalizací kódu, než runtime stráví spuštěním neoptimalizovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="868fe-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="868fe-190">Vrstvená kompilace zavádí dvě fáze kompilace JIT:</span><span class="sxs-lookup"><span data-stu-id="868fe-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="868fe-191">**První vrstva**, která generuje kód co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="868fe-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="868fe-192">**Druhá vrstva**, která generuje optimalizovaný kód pro ty metody, které jsou často spouštěny.</span><span class="sxs-lookup"><span data-stu-id="868fe-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="868fe-193">Druhá vrstva kompilace se provádí paralelně pro zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="868fe-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="868fe-194">Můžete se přihlásit do vrstvené kompilace v obou způsobech.</span><span class="sxs-lookup"><span data-stu-id="868fe-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="868fe-195">Chcete-li použít vrstvenou kompilaci ve všech projektech, které používají sadu .NET Core 2.1 SDK, nastavte následující proměnnou prostředí:</span><span class="sxs-lookup"><span data-stu-id="868fe-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="868fe-196">Chcete-li použít vrstvenou kompilaci pro `<TieredCompilation>` jednotlivý `<PropertyGroup>` projekt, přidejte vlastnost do části souboru projektu MSBuild, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="868fe-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="868fe-197">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="868fe-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="868fe-198">`Span<T>` a `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="868fe-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="868fe-199">.NET Core 2.1 obsahuje některé nové typy, které usnadňují práci s poli a jinými typy paměti.</span><span class="sxs-lookup"><span data-stu-id="868fe-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="868fe-200">Mezi nové typy patří:</span><span class="sxs-lookup"><span data-stu-id="868fe-200">The new types include:</span></span>

- <span data-ttu-id="868fe-201"><xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="868fe-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="868fe-202"><xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="868fe-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="868fe-203">Bez těchto typů při předávání těchto položek jako část pole nebo část vyrovnávací paměti, je nutné vytvořit kopii některé části dat před předáním metodě.</span><span class="sxs-lookup"><span data-stu-id="868fe-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="868fe-204">Tyto typy poskytují virtuální zobrazení těchto dat, které eliminuje potřebu další přidělení paměti a operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="868fe-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="868fe-205">Následující příklad používá <xref:System.Span%601> <xref:System.Memory%601> a instance poskytnout virtuální zobrazení 10 prvků pole.</span><span class="sxs-lookup"><span data-stu-id="868fe-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="868fe-206">Brotli komprese</span><span class="sxs-lookup"><span data-stu-id="868fe-206">Brotli compression</span></span>

<span data-ttu-id="868fe-207">.NET Core 2.1 přidává podporu pro kompresi a dekompresi Brotli.</span><span class="sxs-lookup"><span data-stu-id="868fe-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="868fe-208">Brotli je univerzální bezeztrátový kompresní algoritmus, který je definován v [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a je podporován většinou webových prohlížečů a hlavních webových serverů.</span><span class="sxs-lookup"><span data-stu-id="868fe-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="868fe-209">Můžete použít třídu <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> založenou na datovém proudu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> nebo <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> vysoce výkonné rozsah založené a třídy.</span><span class="sxs-lookup"><span data-stu-id="868fe-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="868fe-210">Následující příklad ilustruje kompresi s třídou: <xref:System.IO.Compression.BrotliStream></span><span class="sxs-lookup"><span data-stu-id="868fe-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="868fe-211">Chování <xref:System.IO.Compression.BrotliStream> je stejné <xref:System.IO.Compression.DeflateStream> jako <xref:System.IO.Compression.GZipStream>a , což usnadňuje převod kódu, <xref:System.IO.Compression.BrotliStream>který volá tato api na .</span><span class="sxs-lookup"><span data-stu-id="868fe-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="868fe-212">Nová rozhraní API kryptografie a vylepšení kryptografie</span><span class="sxs-lookup"><span data-stu-id="868fe-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="868fe-213">.NET Core 2.1 obsahuje řadu vylepšení rozhraní API kryptografie:</span><span class="sxs-lookup"><span data-stu-id="868fe-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="868fe-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>je k dispozici v balíčku System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="868fe-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="868fe-215">Implementace je stejná <xref:System.Security.Cryptography.Pkcs.SignedCms> jako třída v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="868fe-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="868fe-216">Nové přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody přijmout identifikátor algoritmu hash umožnit volajícím získat hodnoty kryptografického otisku certifikátu pomocí algoritmů než SHA-1.</span><span class="sxs-lookup"><span data-stu-id="868fe-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="868fe-217">Nová <xref:System.Span%601>kryptografická rozhraní API jsou k dispozici pro hašování, HMAC, kryptografické generování náhodných čísel, generování asymetrických podpisů, zpracování asymetrických podpisů a šifrování RSA.</span><span class="sxs-lookup"><span data-stu-id="868fe-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="868fe-218">Výkon <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> se zlepšil a to asi o <xref:System.Span%601>15 % pomocí implementace založené na článku.</span><span class="sxs-lookup"><span data-stu-id="868fe-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="868fe-219">Nová <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> třída obsahuje dvě nové metody:</span><span class="sxs-lookup"><span data-stu-id="868fe-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="868fe-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>trvá pevně dobu vrátit pro všechny dva vstupy stejné délky, což je vhodné pro použití v kryptografické ověření, aby se zabránilo přispívání k časování informace o postranním kanálu.</span><span class="sxs-lookup"><span data-stu-id="868fe-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="868fe-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>je rutina vymazání paměti, kterou nelze optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="868fe-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="868fe-222">Statická <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> metoda vyplní <xref:System.Span%601> náhodné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="868fe-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="868fe-223">Nyní <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> je podporován na Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="868fe-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="868fe-224">Elliptic-Curve Diffie-Hellman (ECDH) je <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> nyní k dispozici v řadě rodiny.</span><span class="sxs-lookup"><span data-stu-id="868fe-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="868fe-225">Plocha je stejná jako v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="868fe-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="868fe-226">Instance vrácená <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> pomocí aplikace OAEP pomocí metody OAEP pomocí výtahu SHA-2, stejně jako generování nebo ověřování podpisů pomocí RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="868fe-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="868fe-227">Vylepšení soketů</span><span class="sxs-lookup"><span data-stu-id="868fe-227">Sockets improvements</span></span>

<span data-ttu-id="868fe-228">Jádro .NET obsahuje nový <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>typ a <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>přepsaný , které tvoří základ síťových rozhraní API vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="868fe-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="868fe-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, je například základem <xref:System.Net.Http.HttpClient> provádění.</span><span class="sxs-lookup"><span data-stu-id="868fe-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="868fe-230">V předchozích verzích rozhraní .NET Core byla rozhraní API vyšší úrovně založena na nativních síťových implementacích.</span><span class="sxs-lookup"><span data-stu-id="868fe-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="868fe-231">Implementace soketů zavedená v rozhraní .NET Core 2.1 má řadu výhod:</span><span class="sxs-lookup"><span data-stu-id="868fe-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="868fe-232">Významné zlepšení výkonu ve srovnání s předchozí implementací.</span><span class="sxs-lookup"><span data-stu-id="868fe-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="868fe-233">Eliminace závislostí platformy, což zjednodušuje nasazení a obsluhu.</span><span class="sxs-lookup"><span data-stu-id="868fe-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="868fe-234">Konzistentní chování na všech platformách .NET Core.</span><span class="sxs-lookup"><span data-stu-id="868fe-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="868fe-235"><xref:System.Net.Http.SocketsHttpHandler>je výchozí implementace v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="868fe-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="868fe-236">Aplikaci však můžete nakonfigurovat <xref:System.Net.Http.HttpClientHandler> tak, aby <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> používala starší třídu voláním metody:</span><span class="sxs-lookup"><span data-stu-id="868fe-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="868fe-237">Proměnnou prostředí můžete také použít k odhlášení z <xref:System.Net.Http.SocketsHttpHandler>používání implementací soketů založených na aplikaci .</span><span class="sxs-lookup"><span data-stu-id="868fe-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="868fe-238">Chcete-li to `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` provést, `false` nastavte buď nebo 0.</span><span class="sxs-lookup"><span data-stu-id="868fe-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="868fe-239">V systému Windows můžete <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>také použít , který spoléhá na <xref:System.Net.Http.SocketsHttpHandler> nativní implementaci nebo třídu <xref:System.Net.Http.HttpClient> předáním instance třídy konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="868fe-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="868fe-240">V Linuxu a macOS <xref:System.Net.Http.HttpClient> můžete konfigurovat pouze na základě procesu.</span><span class="sxs-lookup"><span data-stu-id="868fe-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="868fe-241">V systému Linux je třeba nasadit [libcurl,](https://curl.haxx.se/libcurl/) pokud chcete použít starou <xref:System.Net.Http.HttpClient> implementaci.</span><span class="sxs-lookup"><span data-stu-id="868fe-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="868fe-242">(Je nainstalován s rozhraním .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="868fe-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="868fe-243">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="868fe-243">Breaking changes</span></span>

<span data-ttu-id="868fe-244">Informace o narušujících změnách naleznete v [tématu Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span><span class="sxs-lookup"><span data-stu-id="868fe-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="868fe-245">Viz také</span><span class="sxs-lookup"><span data-stu-id="868fe-245">See also</span></span>

- [<span data-ttu-id="868fe-246">Co je nového v .NET Core</span><span class="sxs-lookup"><span data-stu-id="868fe-246">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="868fe-247">Nové funkce v EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="868fe-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="868fe-248">Co je nového v ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="868fe-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
