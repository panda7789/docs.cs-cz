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
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Vypsat shromažďování a nástroj pro analýzu (`dotnet-dump`)

**Tento článek se týká: ✓** .net Core 3,0 SDK a novějších verzí

> [!NOTE]
> `dotnet-dump` není v macOS podporováno.

## <a name="installing-dotnet-dump"></a>Instalace `dotnet-dump`

Chcete-li nainstalovat nejnovější vydanou verzi [balíčku NuGet](https://www.nuget.org/packages/dotnet-dump)`dotnet-dump`, použijte příkaz pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Stručný obsah

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Popis

Globální nástroj `dotnet-dump` je způsob, jak shromažďovat a analyzovat výpisy Windows a Linux bez jakéhokoli nativního ladicího programu, jako je `lldb` v systému Linux. Tento nástroj je důležitý na platformách, jako je například Alpine Linux, kde není k dispozici plně funkční `lldb`. Nástroj `dotnet-dump` umožňuje spouštět příkazy SOS k analýze havárií a uvolňování paměti (GC), ale není to nativní ladicí program, takže se nepodporují například zobrazení nativních rámců zásobníku.

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazí verzi nástroje dotnet-Counters.

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

## <a name="commands"></a>Příkazy

| Příkaz                                     |
| ------------------------------------------- |
| [dotnet – výpis shromažďování](#dotnet-dump-collect) |
| [dotnet – vystavení příkazu analyzovat](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet – výpis shromažďování

Zachycuje výpis paměti z procesu.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Možnosti

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

- **`-p|--process-id <PID>`**

  Určuje číslo ID procesu, ze kterého se má shromáždit výpis paměti.

- **`--type <Heap|Mini>`**

  Určuje typ Dumb, který určuje typy informací shromažďovaných z procesu. Existují dva typy:

  - `Heap` – velký a poměrně obsáhlý výpis, který obsahuje seznamy modulů, seznam vláken, všechny zásobníky, informace o výjimkách, informace o popisovači a veškerou paměť s výjimkou mapovaných imagí.
  - `Mini` – malý výpis obsahující seznamy modulů, seznam vláken, informace o výjimce a všechny zásobníky.

  Není-li tento parametr zadán, je výchozí hodnota `Heap`.

- **`-o|--output <output_dump_path>`**

  Úplná cesta a název souboru, kam se má nazapisovat shromážděný výpis paměti

  Pokud není zadán:

  - Výchozí hodnota je *.\dump_YYYYMMDD_HHMMSS.dmp* ve Windows.
  - Výchozí hodnota je *./core_YYYYMMDD_HHMMSS* v systému Linux.

  RRRRMMDD je rok/měsíc/den a HHMMSS je hodina/minuta za sekundu.

- **`--diag`**

  Povolí protokolování diagnostiky kolekce výpisu.

## <a name="dotnet-dump-analyze"></a>dotnet – vystavení příkazu analyzovat

Spustí interaktivní prostředí pro zkoumání výpisu paměti. Prostředí akceptuje různé [příkazy SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Arguments

- **`<dump_path>`**

  Určuje cestu k souboru s výpisem paměti, která se má analyzovat.

### <a name="options"></a>Možnosti

- **`-c|--command <debug_command>`**

  Určuje [příkaz](#analyze-sos-commands) , který se má spustit v prostředí při spuštění.

### <a name="analyze-sos-commands"></a>Analyzovat příkazy SOS

| Příkaz                             | Funkce                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Zobrazí všechny dostupné příkazy.                                                               |
| `soshelp|help <command>`            | Zobrazí zadaný příkaz.                                                               |
| `exit|quit`                         | Ukončí interaktivní režim.                                                                       |
| `clrstack <arguments>`              | Poskytne trasování zásobníku pouze pro spravovaný kód.                                                  |
| `clrthreads <arguments>`            | Zobrazí seznam spravovaných vláken, která běží.                                                            |
| `dumpasync <arguments>`             | Zobrazí informace o počítačích asynchronního stavu na haldě shromážděné paměti.                |
| `dumpassembly <arguments>`          | Zobrazí podrobnosti o sestavení.                                                           |
| `dumpclass <arguments>`             | Zobrazí informace o struktuře třídy EE na zadané adrese.                     |
| `dumpdelegate <arguments>`          | Zobrazí informace o delegátovi.                                                        |
| `dumpdomain <arguments>`            | Zobrazí informace o všech objektech třídy AppDomain a všech sestaveních v rámci domén.                |
| `dumpheap <arguments>`              | Zobrazí informace o haldě shromážděné paměti a statistiky shromažďování informací o objektech.       |
| `dumpil <arguments>`                | Zobrazí kód v jazyce MSIL (Microsoft Intermediate Language) přidružený ke spravované metodě. |
| `dumplog <arguments>`               | Zapíše obsah zátěžového protokolu uloženého v paměti do zadaného souboru.                         |
| `dumpmd <arguments>`                | Zobrazí informace o struktuře MethodDesc na zadané adrese.                   |
| `dumpmodule <arguments>`            | Zobrazí informace o struktuře modulu EE na zadané adrese.                    |
| `dumpmt <arguments>`                | Zobrazí informace o tabulce metod na zadané adrese.                           |
| `dumpobj <arguments>`               | Zobrazí informace o objektu na zadané adrese.                                       |
| `dso|dumpstackobjects <arguments>`  | Zobrazí všechny spravované objekty nalezené v rámci aktuálního zásobníku.                    |
| `eeheap <arguments>`                | Zobrazí informace o paměti procesu spotřebované interními datovými strukturami modulu runtime.              |
| `finalizequeue <arguments>`         | Zobrazí všechny objekty, které jsou registrovány pro dokončení.                                             |
| `gcroot <arguments>`                | Zobrazí informace o odkazech (neboli kořenech) na objekt na zadané adrese.              |
| `gcwhere <arguments>`               | Zobrazí umístění v haldě GC argumentu předaného.                               |
| `ip2md <arguments>`                 | Zobrazí strukturu MethodDesc na zadané adrese v kódu JIT.                       |
| `histclear <arguments>`             | Uvolní všechny prostředky, které používá rodina příkazů `hist*`.                                |
| `histinit <arguments>`              | Inicializuje struktury SOS ze zátěžového protokolu uloženého v laděné položce.                     |
| `histobj <arguments>`               | Zobrazí přemístění zátěžového protokolu uvolňování paměti související s `<arguments>`.              |
| `histobjfind <arguments>`           | Zobrazí všechny položky protokolu, které odkazují na objekt na zadané adrese.               |
| `histroot <arguments>`              | Zobrazí informace týkající se propagace a přemístění zadaného kořenu.        |
| `lm|modules`                        | Zobrazí v procesu nativní moduly.                                                   |
| `name2ee <arguments>`               | Zobrazuje strukturu metody a strukturu EEClass pro `<argument>`.                |
| `pe|printexception <arguments>`     | Zobrazí libovolný objekt odvozený z třídy Exception na adrese `<argument>`.             |
| `setsymbolserver <arguments>`       | Povolí podporu serveru symbolů.                                                             |
| `syncblk <arguments>`               | Zobrazí informace o držiteli SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Nastaví nebo zobrazí aktuální ID vlákna pro příkazy SOS.                                  |

## <a name="using-dotnet-dump"></a>Použití `dotnet-dump`

Prvním krokem je shromáždění výpisu paměti. Tento krok lze přeskočit, pokud již byl vygenerován základní Výpis paměti. Pro každý operační systém nebo integrovanou [funkci generování výpisu](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) modulu runtime .NET Core můžete vytvořit základní výpisy.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Nyní Analyzujte základní Výpis pomocí příkazu `analyze`:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Tato akce přinese interaktivní relaci, která přijímá příkazy jako:

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

Pokud chcete zobrazit neošetřenou výjimku, která ukončila vaši aplikaci:

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

## <a name="special-instructions-for-docker"></a>Speciální pokyny pro Docker

Pokud používáte v Docker, vyžaduje shromažďování výpisu `SYS_PTRACE` (`--cap-add=SYS_PTRACE` nebo `--privileged`).

V obrázcích Docker systému Microsoft .NET Core SDK Linux mohou některé příkazy `dotnet-dump` vyvolat následující výjimku:

> Neošetřená výjimka: System. DllNotFoundException –: nelze načíst sdílenou knihovnu ' libdl.so ' nebo jednu z jejích závislostí.

Pokud chcete tento problém obejít, nainstalujte balíček "libc6-dev".
