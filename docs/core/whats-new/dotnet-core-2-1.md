---
title: Co je nového v .NET Core 2.1
description: Přečtěte si o nových funkcích, které najdete v .NET Core 2,1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 3e6f3a921238a5897c7aa4b6034be979724b7167
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283439"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="5cefa-103">Co je nového v .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5cefa-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="5cefa-104">.NET Core 2,1 obsahuje vylepšení a nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="5cefa-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="5cefa-105">Nástroje</span><span class="sxs-lookup"><span data-stu-id="5cefa-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="5cefa-106">Posunout nahoru</span><span class="sxs-lookup"><span data-stu-id="5cefa-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="5cefa-107">Nasazení</span><span class="sxs-lookup"><span data-stu-id="5cefa-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="5cefa-108">Sada Compatibility Pack pro Windows</span><span class="sxs-lookup"><span data-stu-id="5cefa-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="5cefa-109">Vylepšení kompilace JIT</span><span class="sxs-lookup"><span data-stu-id="5cefa-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="5cefa-110">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5cefa-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="5cefa-111">Nástroje</span><span class="sxs-lookup"><span data-stu-id="5cefa-111">Tooling</span></span>

<span data-ttu-id="5cefa-112">Sada SDK .NET Core 2,1 (v 2.1.300), nástroje, které jsou součástí .NET Core 2,1, obsahují tyto změny a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="5cefa-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="5cefa-113">Vylepšení výkonu sestavení</span><span class="sxs-lookup"><span data-stu-id="5cefa-113">Build performance improvements</span></span>

<span data-ttu-id="5cefa-114">Hlavní zaměření rozhraní .NET Core 2,1 zvyšuje výkon při sestavování, zejména pro přírůstková sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cefa-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="5cefa-115">Tato vylepšení výkonu platí pro sestavení příkazového řádku pomocí `dotnet build` a pro sestavení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5cefa-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="5cefa-116">Mezi jednotlivé oblasti vylepšení patří:</span><span class="sxs-lookup"><span data-stu-id="5cefa-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="5cefa-117">Pro účely řešení Asset Resolution vyřešte pouze prostředky využívané sestavením místo všech prostředků.</span><span class="sxs-lookup"><span data-stu-id="5cefa-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="5cefa-118">Ukládání odkazů na sestavení do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5cefa-118">Caching of assembly references.</span></span>

- <span data-ttu-id="5cefa-119">Použití dlouhotrvajících serverů sestavení sady SDK, které jsou procesy, které jsou rozloženy mezi jednotlivá `dotnet build` volání.</span><span class="sxs-lookup"><span data-stu-id="5cefa-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="5cefa-120">Eliminují potřebu JIT zkompilovat velké bloky kódu pokaždé, když `dotnet build` se spustí.</span><span class="sxs-lookup"><span data-stu-id="5cefa-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="5cefa-121">Procesy sestavení serveru mohou být automaticky ukončeny pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="5cefa-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="5cefa-122">Nové příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5cefa-122">New CLI commands</span></span>

<span data-ttu-id="5cefa-123">K dispozici je řada nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí, `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5cefa-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="5cefa-124">Mezi tyto nástroje patří:</span><span class="sxs-lookup"><span data-stu-id="5cefa-124">These tools include:</span></span>

- <span data-ttu-id="5cefa-125">`dotnet watch`poskytuje sledovací proces systému souborů, který čeká na změnu souboru před spuštěním určené sady příkazů.</span><span class="sxs-lookup"><span data-stu-id="5cefa-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="5cefa-126">Například následující příkaz automaticky znovu sestaví aktuální projekt a generuje podrobný výstup pokaždé, když se změní soubor:</span><span class="sxs-lookup"><span data-stu-id="5cefa-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="5cefa-127">Všimněte si `--` Možnosti, která předchází této `--verbose` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="5cefa-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="5cefa-128">Omezuje možnosti předané přímo na `dotnet watch` příkaz z argumentů, které jsou předány podřízenému `dotnet` procesu.</span><span class="sxs-lookup"><span data-stu-id="5cefa-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="5cefa-129">Bez této `--verbose` možnosti platí pro `dotnet watch` příkaz, nikoli `dotnet build` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5cefa-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="5cefa-130">Další informace najdete v tématu [vývoj aplikací ASP.NET Core pomocí příkazu dotnet Watch](/aspnet/core/tutorials/dotnet-watch).</span><span class="sxs-lookup"><span data-stu-id="5cefa-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="5cefa-131">`dotnet dev-certs`generuje a spravuje certifikáty používané během vývoje v aplikacích ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cefa-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="5cefa-132">`dotnet user-secrets`spravuje tajné klíče v úložišti tajného uživatele v aplikacích ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cefa-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="5cefa-133">`dotnet sql-cache`Vytvoří tabulku a indexy v databázi Microsoft SQL Server, která se má použít pro distribuované ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5cefa-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="5cefa-134">`dotnet ef`je nástroj pro správu databází, <xref:Microsoft.EntityFrameworkCore.DbContext> objektů a migrací v aplikacích Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="5cefa-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="5cefa-135">Další informace najdete v tématu [EF Core nástroje příkazového řádku .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="5cefa-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="5cefa-136">Globální nástroje</span><span class="sxs-lookup"><span data-stu-id="5cefa-136">Global Tools</span></span>

<span data-ttu-id="5cefa-137">.NET Core 2,1 podporuje *globální nástroje* – tedy vlastní nástroje, které jsou k dispozici globálně z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5cefa-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="5cefa-138">Model rozšiřitelnosti v předchozích verzích rozhraní .NET Core, které jsou k dispozici pro jednotlivé projekty, pouze pomocí nástroje `DotnetCliToolReference` .</span><span class="sxs-lookup"><span data-stu-id="5cefa-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="5cefa-139">K instalaci globálního nástroje použijte příkaz [dotnet Tool Install](../tools/dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="5cefa-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="5cefa-140">Například:</span><span class="sxs-lookup"><span data-stu-id="5cefa-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="5cefa-141">Po instalaci můžete nástroj spustit z příkazového řádku zadáním názvu nástroje.</span><span class="sxs-lookup"><span data-stu-id="5cefa-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="5cefa-142">Další informace najdete v tématu [Přehled globálních nástrojů .NET Core](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5cefa-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="5cefa-143">Správa nástrojů pomocí `dotnet tool` příkazu</span><span class="sxs-lookup"><span data-stu-id="5cefa-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="5cefa-144">V sadě .NET Core 2,1 SDK všechny operace nástrojů používají `dotnet tool` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5cefa-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="5cefa-145">K dispozici jsou následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="5cefa-145">The following options are available:</span></span>

- <span data-ttu-id="5cefa-146">[`dotnet tool install`](../tools/dotnet-tool-install.md)pro instalaci nástroje.</span><span class="sxs-lookup"><span data-stu-id="5cefa-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="5cefa-147">[`dotnet tool update`](../tools/dotnet-tool-update.md)k odinstalaci a přeinstalaci nástroje, který ji efektivně aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="5cefa-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="5cefa-148">[`dotnet tool list`](../tools/dotnet-tool-list.md)k vypsání aktuálně nainstalovaných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="5cefa-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="5cefa-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)k odinstalaci aktuálně nainstalovaných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="5cefa-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="5cefa-150">Posunout nahoru</span><span class="sxs-lookup"><span data-stu-id="5cefa-150">Roll forward</span></span>

<span data-ttu-id="5cefa-151">Všechny aplikace .NET Core počínaje platformou .NET Core 2,0 se automaticky předají do nejnovější *dílčí verze* nainstalované v systému.</span><span class="sxs-lookup"><span data-stu-id="5cefa-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="5cefa-152">Od verze .NET Core 2,0, pokud není k dispozici verze .NET Core, se kterou byla aplikace sestavena v době běhu, aplikace se automaticky spustí s nejnovější nainstalovanou *podverzí* rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cefa-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at run time, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="5cefa-153">Jinými slovy, pokud je aplikace sestavená pomocí .NET Core 2,0 a .NET Core 2,0 není v hostitelském systému k dispozici, ale .NET Core 2,1 je, aplikace se spouští s .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="5cefa-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cefa-154">Toto chování při přeposílání se nevztahuje na verze Preview.</span><span class="sxs-lookup"><span data-stu-id="5cefa-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="5cefa-155">Ve výchozím nastavení se ani na hlavní verze nevztahují, ale dá se změnit pomocí níže uvedených nastavení.</span><span class="sxs-lookup"><span data-stu-id="5cefa-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="5cefa-156">Toto chování můžete upravit tak, že změníte nastavení pro přeposílání na žádné kandidátské sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5cefa-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="5cefa-157">K dispozici jsou následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="5cefa-157">The available settings are:</span></span>

- <span data-ttu-id="5cefa-158">`0`– Zakažte chování při přeposílání dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="5cefa-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="5cefa-159">S tímto nastavením bude aplikace vytvořená pro .NET Core 2.0.0 předána do .NET Core 2.0.1, ale ne do .NET Core 2.2.0 nebo .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="5cefa-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="5cefa-160">`1`– povolí chování při přeposílání dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="5cefa-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="5cefa-161">Toto je výchozí hodnota pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="5cefa-161">This is the default value for the setting.</span></span> <span data-ttu-id="5cefa-162">S tímto nastavením se aplikace sestavená pro .NET Core 2.0.0 bude převádět na rozhraní .NET Core 2.0.1 nebo .NET Core 2.2.0, podle toho, která z nich je nainstalovaná, ale nebude se převádět do .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="5cefa-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="5cefa-163">`2`– umožňuje povolit menší a hlavní verzi – chování při přeposílání.</span><span class="sxs-lookup"><span data-stu-id="5cefa-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="5cefa-164">V případě, že je nastavena i jiná hlavní verze, bude aplikace vytvořená pro .NET Core 2.0.0 předána do .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="5cefa-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="5cefa-165">Toto nastavení můžete upravit některým ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="5cefa-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="5cefa-166">Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` proměnnou prostředí na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5cefa-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="5cefa-167">Přidejte následující řádek s požadovanou hodnotou do souboru *. runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="5cefa-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="5cefa-168">Při použití [.NET Core CLI](../tools/index.md)přidejte následující možnost s požadovanou hodnotou do příkazu .NET Core, například `run` :</span><span class="sxs-lookup"><span data-stu-id="5cefa-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="5cefa-169">Přeposílání opravné verze je nezávisle na tomto nastavení a je provedeno po použití jakékoli případné nepatrné nebo hlavní verze posunutí.</span><span class="sxs-lookup"><span data-stu-id="5cefa-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="5cefa-170">Nasazení</span><span class="sxs-lookup"><span data-stu-id="5cefa-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="5cefa-171">Samoobslužná Údržba aplikací</span><span class="sxs-lookup"><span data-stu-id="5cefa-171">Self-contained application servicing</span></span>

<span data-ttu-id="5cefa-172">`dotnet publish`nyní publikuje samostatné aplikace s verzí modulu runtime, který je součástí služby.</span><span class="sxs-lookup"><span data-stu-id="5cefa-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="5cefa-173">Když publikujete samostatnou aplikaci se sadou SDK .NET Core 2,1 (v 2.1.300), vaše aplikace zahrnuje nejnovější verzi služby runtime známou danou sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="5cefa-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="5cefa-174">Když upgradujete na nejnovější sadu SDK, publikujete s nejnovější verzí modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cefa-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="5cefa-175">To platí pro modul runtime .NET Core 1,0 a novější.</span><span class="sxs-lookup"><span data-stu-id="5cefa-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="5cefa-176">Samoobslužné publikování spoléhá na verze modulu runtime v NuGet.org. V počítači nemusíte mít službu runtime, která je v provozu.</span><span class="sxs-lookup"><span data-stu-id="5cefa-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="5cefa-177">Pomocí sady .NET Core 2,0 SDK jsou samostatně obsažené aplikace publikovány s modulem runtime .NET Core 2.0.0, pokud není zadána jiná verze prostřednictvím `RuntimeFrameworkVersion` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5cefa-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="5cefa-178">S tímto novým chováním už nebudete muset tuto vlastnost nastavovat, aby se pro samostatnou aplikaci vybrala vyšší verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5cefa-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="5cefa-179">Nejjednodušší způsob, jak dál, je publikovat vždy pomocí .NET Core 2,1 SDK (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="5cefa-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="5cefa-180">Další informace najdete v tématu implementace [modulu runtime pro samostatné nasazení](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="5cefa-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="5cefa-181">Sada Compatibility Pack pro Windows</span><span class="sxs-lookup"><span data-stu-id="5cefa-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="5cefa-182">Při portování existujícího kódu z .NET Framework do .NET Core můžete použít [sadu Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="5cefa-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="5cefa-183">Poskytuje přístup k 20 000 více rozhraním API, než je k dispozici v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cefa-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="5cefa-184">Tato rozhraní API zahrnují typy v <xref:System.Drawing?displayProperty=nameWithType> oboru názvů, <xref:System.Diagnostics.EventLog> třídy, rozhraní WMI, čítače výkonu, služby systému Windows a typy a členy registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5cefa-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="5cefa-185">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="5cefa-185">JIT compiler improvements</span></span>

<span data-ttu-id="5cefa-186">.NET Core zahrnuje novou technologii kompilátoru JIT nazvanou *vrstvená kompilace* (označovaná také jako *adaptivní optimalizace*), která může významně zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="5cefa-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="5cefa-187">Vrstvená kompilace je nastavení pro výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="5cefa-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="5cefa-188">Jedním z důležitých úloh prováděných kompilátorem JIT je optimalizace provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="5cefa-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="5cefa-189">Pro málo používané cesty kódu však může kompilátor strávit více času optimalizací kódu, než modul runtime stráví neoptimalizovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="5cefa-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="5cefa-190">Vrstvená kompilace přináší dvě fáze kompilace JIT:</span><span class="sxs-lookup"><span data-stu-id="5cefa-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="5cefa-191">**První vrstva**, která generuje kód co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="5cefa-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="5cefa-192">**Druhá vrstva**, která generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často.</span><span class="sxs-lookup"><span data-stu-id="5cefa-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="5cefa-193">Druhá vrstva kompilace se paralelně provádí za účelem zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="5cefa-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="5cefa-194">Můžete vyjádřit souhlas s vrstvenými kompilacemi jedním ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="5cefa-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="5cefa-195">Chcete-li použít vrstvenou kompilaci ve všech projektech, které používají sadu .NET Core 2,1 SDK, nastavte následující proměnnou prostředí:</span><span class="sxs-lookup"><span data-stu-id="5cefa-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="5cefa-196">Chcete-li použít vrstvenou kompilaci pro každý projekt, přidejte `<TieredCompilation>` vlastnost do `<PropertyGroup>` oddílu souboru projektu MSBuild, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="5cefa-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="5cefa-197">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5cefa-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="5cefa-198">`Span<T>` a `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="5cefa-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="5cefa-199">.NET Core 2,1 obsahuje některé nové typy, které umožňují pracovat s poli a dalšími typy paměti mnohem efektivnější.</span><span class="sxs-lookup"><span data-stu-id="5cefa-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="5cefa-200">Mezi nové typy patří:</span><span class="sxs-lookup"><span data-stu-id="5cefa-200">The new types include:</span></span>

- <span data-ttu-id="5cefa-201"><xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5cefa-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="5cefa-202"><xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5cefa-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5cefa-203">Bez těchto typů při předávání takových položek jako části pole nebo oddílu vyrovnávací paměti je nutné vytvořit kopii určité části dat před předáním do metody.</span><span class="sxs-lookup"><span data-stu-id="5cefa-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="5cefa-204">Tyto typy poskytují virtuální pohled na tato data, který eliminuje nutnost dodatečného přidělení paměti a operací kopírování.</span><span class="sxs-lookup"><span data-stu-id="5cefa-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="5cefa-205">V následujícím příkladu se používá <xref:System.Span%601> <xref:System.Memory%601> instance a k poskytnutí virtuálního zobrazení 10 prvků pole.</span><span class="sxs-lookup"><span data-stu-id="5cefa-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="5cefa-206">Komprese Brotli</span><span class="sxs-lookup"><span data-stu-id="5cefa-206">Brotli compression</span></span>

<span data-ttu-id="5cefa-207">.NET Core 2,1 přidává podporu pro kompresi a dekompresi Brotli.</span><span class="sxs-lookup"><span data-stu-id="5cefa-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="5cefa-208">Brotli je univerzální bezeztrátová kompresní algoritmus, který je definovaný v [dokumentu RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a který podporuje většina webových prohlížečů a hlavních webových serverů.</span><span class="sxs-lookup"><span data-stu-id="5cefa-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="5cefa-209">Můžete použít třídu založenou na datovém proudu <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> nebo vysoce výkonné rozsahy <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> a <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="5cefa-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="5cefa-210">Následující příklad znázorňuje kompresi s <xref:System.IO.Compression.BrotliStream> třídou:</span><span class="sxs-lookup"><span data-stu-id="5cefa-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="5cefa-211"><xref:System.IO.Compression.BrotliStream>Chování je stejné jako <xref:System.IO.Compression.DeflateStream> a <xref:System.IO.Compression.GZipStream> , což usnadňuje převod kódu, který volá tato rozhraní API na <xref:System.IO.Compression.BrotliStream> .</span><span class="sxs-lookup"><span data-stu-id="5cefa-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="5cefa-212">Nová kryptografická rozhraní API a kryptografická vylepšení</span><span class="sxs-lookup"><span data-stu-id="5cefa-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="5cefa-213">.NET Core 2,1 obsahuje řadu vylepšení rozhraní API kryptografie:</span><span class="sxs-lookup"><span data-stu-id="5cefa-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="5cefa-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>je k dispozici v balíčku System. Security. Cryptography. PKCS.</span><span class="sxs-lookup"><span data-stu-id="5cefa-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="5cefa-215">Implementace je stejná jako <xref:System.Security.Cryptography.Pkcs.SignedCms> Třída v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5cefa-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="5cefa-216">Nová přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metod a přijímají identifikátor algoritmu hash, aby mohli volajícím získat hodnoty kryptografického otisku certifikátu pomocí jiných algoritmů než SHA-1.</span><span class="sxs-lookup"><span data-stu-id="5cefa-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="5cefa-217">Nová <xref:System.Span%601> kryptografická rozhraní API jsou k dispozici pro generování hodnot hash, HMAC, kryptografické generování náhodných čísel, generování asymetrických podpisů, zpracování asymetrického podpisu a šifrování RSA.</span><span class="sxs-lookup"><span data-stu-id="5cefa-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="5cefa-218">Výkon systému <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> byl vylepšen o 15% pomocí <xref:System.Span%601> implementace založené na.</span><span class="sxs-lookup"><span data-stu-id="5cefa-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="5cefa-219">Nová <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> Třída obsahuje dvě nové metody:</span><span class="sxs-lookup"><span data-stu-id="5cefa-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="5cefa-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>vybere pevně určenou dobu pro všechny dva vstupy stejné délky, což usnadňuje použití v kryptografickém ověřování, aby se předešlo tomu, že by bylo možné přispívat k načasování informací o kanálu na straně.</span><span class="sxs-lookup"><span data-stu-id="5cefa-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="5cefa-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>je rutina pro mazání paměti, která nemůže být optimalizována.</span><span class="sxs-lookup"><span data-stu-id="5cefa-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="5cefa-222">Statická <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> Metoda vyplní <xref:System.Span%601> náhodné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5cefa-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="5cefa-223">Rozhraní <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> se teď podporuje v systémech Linux a MacOS.</span><span class="sxs-lookup"><span data-stu-id="5cefa-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="5cefa-224">Eliptická Vlnová třída Diffie-Hellman (ECDH) je teď dostupná v <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> rodině tříd.</span><span class="sxs-lookup"><span data-stu-id="5cefa-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="5cefa-225">Oblast Surface je stejná jako v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5cefa-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="5cefa-226">Instance vrácená nástrojem <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> může šifrovat nebo dešifrovat pomocí výplně OAEP s využitím algoritmu SHA-2 a generovat nebo ověřovat podpisy pomocí technologie RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="5cefa-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="5cefa-227">Vylepšení soketů</span><span class="sxs-lookup"><span data-stu-id="5cefa-227">Sockets improvements</span></span>

<span data-ttu-id="5cefa-228">.NET Core obsahuje nový typ, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> a přepsaný <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> , který tvoří základ rozhraní API sítě vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="5cefa-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="5cefa-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>Například je základem <xref:System.Net.Http.HttpClient> implementace.</span><span class="sxs-lookup"><span data-stu-id="5cefa-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="5cefa-230">V předchozích verzích rozhraní .NET Core rozhraní API na vyšší úrovni byly založeny na nativních implementacích sítě.</span><span class="sxs-lookup"><span data-stu-id="5cefa-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="5cefa-231">Implementace soketů představená v .NET Core 2,1 má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="5cefa-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="5cefa-232">Významné zlepšení výkonu při porovnání s předchozí implementací.</span><span class="sxs-lookup"><span data-stu-id="5cefa-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="5cefa-233">Eliminujte závislosti platforem, což zjednodušuje nasazení a údržbu.</span><span class="sxs-lookup"><span data-stu-id="5cefa-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="5cefa-234">Konzistentní chování napříč všemi platformami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cefa-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="5cefa-235"><xref:System.Net.Http.SocketsHttpHandler>je výchozí implementací v rozhraní .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="5cefa-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="5cefa-236">Můžete však nakonfigurovat aplikaci tak, aby používala starší <xref:System.Net.Http.HttpClientHandler> třídu voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="5cefa-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="5cefa-237">Můžete také použít proměnnou prostředí pro výslovný souhlas s používáním implementací soketů založených na <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="5cefa-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="5cefa-238">To provedete tak, že nastavíte hodnotu `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` na `false` nebo 0.</span><span class="sxs-lookup"><span data-stu-id="5cefa-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="5cefa-239">V systému Windows můžete také zvolit použití <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType> , který spoléhá na nativní implementaci, nebo na <xref:System.Net.Http.SocketsHttpHandler> třídu předáním instance třídy do <xref:System.Net.Http.HttpClient> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5cefa-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="5cefa-240">V systémech Linux a macOS můžete nakonfigurovat pouze <xref:System.Net.Http.HttpClient> jednotlivé procesy.</span><span class="sxs-lookup"><span data-stu-id="5cefa-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="5cefa-241">Pokud chcete použít starou implementaci, musíte v systému Linux nasadit [libcurl](https://curl.haxx.se/libcurl/) <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="5cefa-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="5cefa-242">(Instaluje se s .NET Core 2,0.)</span><span class="sxs-lookup"><span data-stu-id="5cefa-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="5cefa-243">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="5cefa-243">Breaking changes</span></span>

<span data-ttu-id="5cefa-244">Informace o zásadních změnách najdete v tématu zásadní [změny migrace z verze 2,0 na 2,1](../compatibility/2.0-2.1.md).</span><span class="sxs-lookup"><span data-stu-id="5cefa-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5cefa-245">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cefa-245">See also</span></span>

- [<span data-ttu-id="5cefa-246">Co je nového v .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5cefa-246">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="5cefa-247">Nové funkce v EF Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5cefa-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="5cefa-248">Co je nového v ASP.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5cefa-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
