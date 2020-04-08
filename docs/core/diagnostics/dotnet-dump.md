---
title: dotnet-dump - .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: c78ddb6447021f61f2452c075733b7d33e051ca0
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888199"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Nástroj pro sběr`dotnet-dump`a analýzu výpisu ( )

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

> [!NOTE]
> `dotnet-dump`v macOS není podporována.

## <a name="installing-dotnet-dump"></a>Instalace`dotnet-dump`

Chcete-li nainstalovat nejnovější `dotnet-dump` verzi [balíčku NuGet](https://www.nuget.org/packages/dotnet-dump), použijte příkaz [instalace nástroje dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Synopse

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Popis

Globální `dotnet-dump` nástroj je způsob, jak shromažďovat a analyzovat výpisy windows a `lldb` linuxbez nativního ladicího programu, který se podílí jako na Linuxu. Tento nástroj je důležitý na platformách, `lldb` jako je Alpine Linux, kde plně funkční není k dispozici. Nástroj `dotnet-dump` umožňuje spustit příkazy SOS k analýze selhání a uvolňování paměti (GC), ale není nativní ladicí program, takže věci jako zobrazení nativních rámců zásobníku nejsou podporovány.

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazí verzi nástroje dotnet-dump.

- **`-h|--help`**

  Zobrazí nápovědu příkazového řádku.

## <a name="commands"></a>Příkazy

| Příkaz                                     |
| ------------------------------------------- |
| [dotnet-dump collect](#dotnet-dump-collect) |
| [dotnet-dump analýza](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet-dump collect

Zachytí výpis z procesu.

### <a name="synopsis"></a>Synopse

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Možnosti

- **`-h|--help`**

  Zobrazí nápovědu příkazového řádku.

- **`-p|--process-id <PID>`**

  Určuje číslo ID procesu, ze kterých má být shromažďováno výpis stavu paměti.

- **`--type <Heap|Mini>`**

  Určuje typ výpisu, který určuje druhy informací, které jsou shromažďovány z procesu. Existují dva typy:

  - `Heap`- Velký a relativně komplexní výpis obsahující seznamy modulů, seznamy vláken, všechny zásobníky, informace o výjimkách, zpracování informací a všechny paměti s výjimkou mapovaných obrázků.
  - `Mini`- Malý výpis obsahující seznamy modulů, seznamy vláken, informace o výjimkách a všechny zásobníky.

  Pokud není `Heap` zadán, je výchozí.

- **`-o|--output <output_dump_path>`**

  Úplná cesta a název souboru, kde by měl být zapsán shromážděný výpis.

  Pokud není specifikováno:

  - Výchozí hodnota *je .\dump_YYYYMMDD_HHMMSS.dmp v* systému Windows.
  - Výchozí hodnota *na ./core_YYYYMMDD_HHMMSS* na Linuxu.

  YYYYMMDD je rok / měsíc / den a HHMMSS je hodina / minutu / sekunda.

- **`--diag`**

  Povolí protokolování diagnostiky kolekce výpisu.

## <a name="dotnet-dump-analyze"></a>dotnet-dump analýza

Spustí interaktivní prostředí k prozkoumání výpisu. Prostředí přijímá různé [příkazy SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Synopse

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Argumenty

- **`<dump_path>`**

  Určuje cestu k souboru výpisu stavu paměti, který má být analyzovat.

### <a name="options"></a>Možnosti

- **`-c|--command <debug_command>`**

  Určuje [příkaz,](#analyze-sos-commands) který má být spuštěn v prostředí při spuštění.

### <a name="analyze-sos-commands"></a>Analýza příkazů SOS

| Příkaz                             | Funkce                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Zobrazí všechny dostupné příkazy.                                                               |
| `soshelp|help <command>`            | Zobrazí zadaný příkaz.                                                               |
| `exit|quit`                         | Ukončí interaktivní režim.                                                                       |
| `clrstack <arguments>`              | Poskytne trasování zásobníku pouze pro spravovaný kód.                                                  |
| `clrthreads <arguments>`            | Zobrazí seznam spuštěných spravovaných vláken.                                                            |
| `dumpasync <arguments>`             | Zobrazí informace o asynchronních stavových počítačích na haldě uvolněné.                |
| `dumpassembly <arguments>`          | Zobrazí podrobnosti o sestavení.                                                           |
| `dumpclass <arguments>`             | Zobrazí informace o struktuře třídy EE na zadané adrese.                     |
| `dumpdelegate <arguments>`          | Zobrazí informace o delegátovi.                                                        |
| `dumpdomain <arguments>`            | Zobrazí informace o všech doménách aplikace a všech sestaveních v doménách.                |
| `dumpheap <arguments>`              | Zobrazí informace o haldě uvolněné paměti a statistiky kolekce objektů.       |
| `dumpil <arguments>`                | Zobrazí kód v jazyce MSIL (Microsoft Intermediate Language) přidružený ke spravované metodě. |
| `dumplog <arguments>`               | Zapíše obsah zátěžového protokolu uloženého v paměti do zadaného souboru.                         |
| `dumpmd <arguments>`                | Zobrazí informace o struktuře MethodDesc na zadané adrese.                   |
| `dumpmodule <arguments>`            | Zobrazí informace o struktuře modulu EE na zadané adrese.                    |
| `dumpmt <arguments>`                | Zobrazí informace o tabulce metod na zadané adrese.                           |
| `dumpobj <arguments>`               | Zobrazí informace o objektu na zadané adrese.                                       |
| `dso|dumpstackobjects <arguments>`  | Zobrazí všechny spravované objekty nalezené v rámci aktuálního zásobníku.                    |
| `eeheap <arguments>`                | Zobrazí informace o procesní paměti spotřebované interními datovými strukturami za běhu.              |
| `finalizequeue <arguments>`         | Zobrazí všechny objekty, které jsou registrovány pro dokončení.                                             |
| `gcroot <arguments>`                | Zobrazí informace o odkazech (nebo kořenech) na objekt na zadané adrese.              |
| `gcwhere <arguments>`               | Zobrazí umístění v haldě GC předaného argumentu.                               |
| `ip2md <arguments>`                 | Zobrazí strukturu MethodDesc na zadané adrese v kódu JIT.                       |
| `histclear <arguments>`             | Uvolní všechny prostředky používané rodinou `hist*` příkazů.                                |
| `histinit <arguments>`              | Inicializuje struktury SOS ze zátěžového protokolu uloženého v laděné položce.                     |
| `histobj <arguments>`               | Zobrazí přemisťování protokolu `<arguments>`stresu při uvolňování paměti související s aplikací .              |
| `histobjfind <arguments>`           | Zobrazí všechny položky protokolu, které odkazují na objekt na zadané adrese.               |
| `histroot <arguments>`              | Zobrazí informace týkající se propagace a přemístění zadaného kořenu.        |
| `lm|modules`                        | Zobrazí nativní moduly v procesu.                                                   |
| `name2ee <arguments>`               | Zobrazí strukturu MethodTable a Strukturu EEClass pro `<argument>`.                |
| `pe|printexception <arguments>`     | Zobrazí libovolný objekt odvozený z třídy Exception na adrese `<argument>`.             |
| `setsymbolserver <arguments>`       | Povolí podporu symbolového serveru.                                                             |
| `syncblk <arguments>`               | Zobrazí informace o držáku SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Nastaví nebo zobrazí aktuální ID vlákna pro příkazy SOS.                                  |

## <a name="using-dotnet-dump"></a>Použití metody `dotnet-dump`

Prvním krokem je shromáždit skládku. Tento krok lze přeskočit, pokud již byl vygenerován výpis jádra. Operační systém nebo [vestavěná funkce generování výpisu stavu .NET](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) Core může každý vytvořit výpisy jádra.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Nyní analyzujte výpis `analyze` jádra pomocí příkazu:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Tato akce vyvolá interaktivní relaci, která přijímá příkazy jako:

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

Zobrazení neošetřené výjimky, která vaši aplikaci zabila:

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

## <a name="special-instructions-for-docker"></a>Zvláštní pokyny pro Docker

Pokud používáte v Dockeru, `SYS_PTRACE` kolekce`--cap-add=SYS_PTRACE` výpisu vyžaduje možnosti (nebo). `--privileged`

Na inacích Linux Dockeru microsoft `dotnet-dump` .NET Core SDK mohou některé příkazy vyvolat následující výjimku:

> Neošetřená výjimka: System.DllNotFoundException: Nelze načíst sdílenou knihovnu "libdl.so" nebo výjimku jedné z jejích závislostí.

Chcete-li tento problém vyřešit, nainstalujte balíček "libc6-dev".
