---
title: dotnet – výpis paměti – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-dump.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 7eba0cba28f0575be4b374b26e9aca26a70df603
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321594"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="aea4c-103">Vypsat shromažďování a nástroj pro analýzu (`dotnet-dump`)</span><span class="sxs-lookup"><span data-stu-id="aea4c-103">Dump collection and analysis utility (`dotnet-dump`)</span></span>

<span data-ttu-id="aea4c-104">**Tento článek se týká: ✓** .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="aea4c-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="aea4c-105">`dotnet-dump` není v macOS podporováno.</span><span class="sxs-lookup"><span data-stu-id="aea4c-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="installing-dotnet-dump"></a><span data-ttu-id="aea4c-106">Instalace `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="aea4c-106">Installing `dotnet-dump`</span></span>

<span data-ttu-id="aea4c-107">Chcete-li nainstalovat nejnovější vydanou verzi [balíčku NuGet](https://www.nuget.org/packages/dotnet-dump)`dotnet-dump`, použijte příkaz pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="aea4c-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="aea4c-108">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="aea4c-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="aea4c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="aea4c-109">Description</span></span>

<span data-ttu-id="aea4c-110">Globální nástroj `dotnet-dump` je způsob, jak shromažďovat a analyzovat výpisy Windows a Linux bez jakéhokoli nativního ladicího programu, jako je `lldb` v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="aea4c-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="aea4c-111">Tento nástroj je důležitý na platformách, jako je například Alpine Linux, kde není k dispozici plně funkční `lldb`.</span><span class="sxs-lookup"><span data-stu-id="aea4c-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="aea4c-112">Nástroj `dotnet-dump` umožňuje spouštět příkazy SOS k analýze havárií a uvolňování paměti (GC), ale není to nativní ladicí program, takže se nepodporují například zobrazení nativních rámců zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aea4c-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="aea4c-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="aea4c-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="aea4c-114">Zobrazí verzi nástroje dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="aea4c-114">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="aea4c-115">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="aea4c-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="aea4c-116">Příkazy</span><span class="sxs-lookup"><span data-stu-id="aea4c-116">Commands</span></span>

| <span data-ttu-id="aea4c-117">Příkaz</span><span class="sxs-lookup"><span data-stu-id="aea4c-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="aea4c-118">dotnet – výpis shromažďování</span><span class="sxs-lookup"><span data-stu-id="aea4c-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="aea4c-119">dotnet – vystavení příkazu analyzovat</span><span class="sxs-lookup"><span data-stu-id="aea4c-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="aea4c-120">dotnet – výpis shromažďování</span><span class="sxs-lookup"><span data-stu-id="aea4c-120">dotnet-dump collect</span></span>

<span data-ttu-id="aea4c-121">Zachycuje výpis paměti z procesu.</span><span class="sxs-lookup"><span data-stu-id="aea4c-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="aea4c-122">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="aea4c-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="aea4c-123">Možnosti</span><span class="sxs-lookup"><span data-stu-id="aea4c-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="aea4c-124">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="aea4c-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="aea4c-125">Určuje číslo ID procesu, ze kterého se má shromáždit výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="aea4c-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="aea4c-126">Určuje typ Dumb, který určuje typy informací shromažďovaných z procesu.</span><span class="sxs-lookup"><span data-stu-id="aea4c-126">Specifies the dumb type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="aea4c-127">Existují dva typy:</span><span class="sxs-lookup"><span data-stu-id="aea4c-127">There are two types:</span></span>

  - <span data-ttu-id="aea4c-128">`Heap` – velký a poměrně obsáhlý výpis, který obsahuje seznamy modulů, seznam vláken, všechny zásobníky, informace o výjimkách, informace o popisovači a veškerou paměť s výjimkou mapovaných imagí.</span><span class="sxs-lookup"><span data-stu-id="aea4c-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="aea4c-129">`Mini` – malý výpis obsahující seznamy modulů, seznam vláken, informace o výjimce a všechny zásobníky.</span><span class="sxs-lookup"><span data-stu-id="aea4c-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="aea4c-130">Není-li tento parametr zadán, je výchozí hodnota `Heap`.</span><span class="sxs-lookup"><span data-stu-id="aea4c-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="aea4c-131">Úplná cesta a název souboru, kam se má nazapisovat shromážděný výpis paměti</span><span class="sxs-lookup"><span data-stu-id="aea4c-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="aea4c-132">Pokud není zadán:</span><span class="sxs-lookup"><span data-stu-id="aea4c-132">If not specified:</span></span>

  - <span data-ttu-id="aea4c-133">Výchozí hodnota je *.\dump_YYYYMMDD_HHMMSS.dmp* ve Windows.</span><span class="sxs-lookup"><span data-stu-id="aea4c-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="aea4c-134">Výchozí hodnota je *./core_YYYYMMDD_HHMMSS* v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="aea4c-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="aea4c-135">RRRRMMDD je rok/měsíc/den a HHMMSS je hodina/minuta za sekundu.</span><span class="sxs-lookup"><span data-stu-id="aea4c-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="aea4c-136">Povolí protokolování diagnostiky kolekce výpisu.</span><span class="sxs-lookup"><span data-stu-id="aea4c-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="aea4c-137">dotnet – vystavení příkazu analyzovat</span><span class="sxs-lookup"><span data-stu-id="aea4c-137">dotnet-dump analyze</span></span>

<span data-ttu-id="aea4c-138">Spustí interaktivní prostředí pro zkoumání výpisu paměti.</span><span class="sxs-lookup"><span data-stu-id="aea4c-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="aea4c-139">Prostředí akceptuje různé [příkazy SOS](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="aea4c-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="aea4c-140">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="aea4c-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="aea4c-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="aea4c-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="aea4c-142">Určuje cestu k souboru s výpisem paměti, která se má analyzovat.</span><span class="sxs-lookup"><span data-stu-id="aea4c-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="aea4c-143">Možnosti</span><span class="sxs-lookup"><span data-stu-id="aea4c-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="aea4c-144">Určuje [příkaz](#analyze-sos-commands) , který se má spustit v prostředí při spuštění.</span><span class="sxs-lookup"><span data-stu-id="aea4c-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="aea4c-145">Analyzovat příkazy SOS</span><span class="sxs-lookup"><span data-stu-id="aea4c-145">Analyze SOS commands</span></span>

| <span data-ttu-id="aea4c-146">Příkaz</span><span class="sxs-lookup"><span data-stu-id="aea4c-146">Command</span></span>                             | <span data-ttu-id="aea4c-147">Funkce</span><span class="sxs-lookup"><span data-stu-id="aea4c-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="aea4c-148">Zobrazí všechny dostupné příkazy.</span><span class="sxs-lookup"><span data-stu-id="aea4c-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="aea4c-149">Zobrazí zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="aea4c-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="aea4c-150">Ukončí interaktivní režim.</span><span class="sxs-lookup"><span data-stu-id="aea4c-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="aea4c-151">Poskytne trasování zásobníku pouze pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="aea4c-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="aea4c-152">Zobrazí seznam spravovaných vláken, která běží.</span><span class="sxs-lookup"><span data-stu-id="aea4c-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="aea4c-153">Zobrazí informace o počítačích asynchronního stavu na haldě shromážděné paměti.</span><span class="sxs-lookup"><span data-stu-id="aea4c-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="aea4c-154">Zobrazí podrobnosti o sestavení.</span><span class="sxs-lookup"><span data-stu-id="aea4c-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="aea4c-155">Zobrazí informace o struktuře třídy EE na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="aea4c-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="aea4c-156">Zobrazí informace o delegátovi.</span><span class="sxs-lookup"><span data-stu-id="aea4c-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="aea4c-157">Zobrazí informace o všech objektech třídy AppDomain a všech sestaveních v rámci domén.</span><span class="sxs-lookup"><span data-stu-id="aea4c-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="aea4c-158">Zobrazí informace o haldě shromážděné paměti a statistiky shromažďování informací o objektech.</span><span class="sxs-lookup"><span data-stu-id="aea4c-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="aea4c-159">Zobrazí kód v jazyce MSIL (Microsoft Intermediate Language) přidružený ke spravované metodě.</span><span class="sxs-lookup"><span data-stu-id="aea4c-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="aea4c-160">Zapíše obsah zátěžového protokolu uloženého v paměti do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="aea4c-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="aea4c-161">Zobrazí informace o struktuře MethodDesc na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="aea4c-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="aea4c-162">Zobrazí informace o struktuře modulu EE na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="aea4c-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="aea4c-163">Zobrazí informace o tabulce metod na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="aea4c-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="aea4c-164">Zobrazí informace o objektu na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="aea4c-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="aea4c-165">Zobrazí všechny spravované objekty nalezené v rámci aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aea4c-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="aea4c-166">Zobrazí informace o paměti procesu spotřebované interními datovými strukturami modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="aea4c-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="aea4c-167">Zobrazí všechny objekty, které jsou registrovány pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="aea4c-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="aea4c-168">Zobrazí informace o odkazech (neboli kořenech) na objekt na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="aea4c-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="aea4c-169">Zobrazí umístění v haldě GC argumentu předaného.</span><span class="sxs-lookup"><span data-stu-id="aea4c-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="aea4c-170">Zobrazí strukturu MethodDesc na zadané adrese v kódu JIT.</span><span class="sxs-lookup"><span data-stu-id="aea4c-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="aea4c-171">Uvolní všechny prostředky, které používá rodina příkazů `hist*`.</span><span class="sxs-lookup"><span data-stu-id="aea4c-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="aea4c-172">Inicializuje struktury SOS ze zátěžového protokolu uloženého v laděné položce.</span><span class="sxs-lookup"><span data-stu-id="aea4c-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="aea4c-173">Zobrazí přemístění zátěžového protokolu uvolňování paměti související s `<arguments>`.</span><span class="sxs-lookup"><span data-stu-id="aea4c-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="aea4c-174">Zobrazí všechny položky protokolu, které odkazují na objekt na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="aea4c-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="aea4c-175">Zobrazí informace týkající se propagace a přemístění zadaného kořenu.</span><span class="sxs-lookup"><span data-stu-id="aea4c-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="aea4c-176">Zobrazí v procesu nativní moduly.</span><span class="sxs-lookup"><span data-stu-id="aea4c-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="aea4c-177">Zobrazuje strukturu metody a strukturu EEClass pro `<argument>`.</span><span class="sxs-lookup"><span data-stu-id="aea4c-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="aea4c-178">Zobrazí libovolný objekt odvozený z třídy Exception na adrese `<argument>`.</span><span class="sxs-lookup"><span data-stu-id="aea4c-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="aea4c-179">Povolí podporu serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="aea4c-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="aea4c-180">Zobrazí informace o držiteli SyncBlock.</span><span class="sxs-lookup"><span data-stu-id="aea4c-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="aea4c-181">Nastaví nebo zobrazí aktuální ID vlákna pro příkazy SOS.</span><span class="sxs-lookup"><span data-stu-id="aea4c-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="aea4c-182">Použití `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="aea4c-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="aea4c-183">Prvním krokem je shromáždění výpisu paměti.</span><span class="sxs-lookup"><span data-stu-id="aea4c-183">The first step is to collect a dump.</span></span> <span data-ttu-id="aea4c-184">Tento krok lze přeskočit, pokud již byl vygenerován základní Výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="aea4c-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="aea4c-185">Pro každý operační systém nebo integrovanou [funkci generování výpisu](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) modulu runtime .NET Core můžete vytvořit základní výpisy.</span><span class="sxs-lookup"><span data-stu-id="aea4c-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="aea4c-186">Nyní Analyzujte základní Výpis pomocí příkazu `analyze`:</span><span class="sxs-lookup"><span data-stu-id="aea4c-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="aea4c-187">Tato akce přinese interaktivní relaci, která přijímá příkazy jako:</span><span class="sxs-lookup"><span data-stu-id="aea4c-187">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="aea4c-188">Pokud chcete zobrazit neošetřenou výjimku, která ukončila vaši aplikaci:</span><span class="sxs-lookup"><span data-stu-id="aea4c-188">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="aea4c-189">Speciální pokyny pro Docker</span><span class="sxs-lookup"><span data-stu-id="aea4c-189">Special instructions for Docker</span></span>

<span data-ttu-id="aea4c-190">Pokud používáte v Docker, vyžaduje shromažďování výpisu `SYS_PTRACE` (`--cap-add=SYS_PTRACE` nebo `--privileged`).</span><span class="sxs-lookup"><span data-stu-id="aea4c-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="aea4c-191">V obrázcích Docker systému Microsoft .NET Core SDK Linux mohou některé příkazy `dotnet-dump` vyvolat následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="aea4c-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="aea4c-192">Neošetřená výjimka: System. DllNotFoundException –: nelze načíst sdílenou knihovnu ' libdl.so ' nebo jednu z jejích závislostí.</span><span class="sxs-lookup"><span data-stu-id="aea4c-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="aea4c-193">Pokud chcete tento problém obejít, nainstalujte balíček "libc6-dev".</span><span class="sxs-lookup"><span data-stu-id="aea4c-193">To work around this problem, install the "libc6-dev" package.</span></span>