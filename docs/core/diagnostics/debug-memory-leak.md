---
title: Ladění kurzu nevracení paměti
description: Zjistěte, jak ladit nevracení paměti v .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737732"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Kurz: Ladění nevracení paměti v rozhraní .NET Core

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

Tento kurz ukazuje nástroje pro analýzu nevracení paměti .NET Core.

Tento kurz používá ukázkovou aplikaci, která je určena k úmyslnému úniku paměti. Vzorek je poskytován jako cvičení. Můžete analyzovat aplikaci, která je neúmyslně nevracení paměti příliš.

V tomto kurzu provedete následující:

> [!div class="checklist"]
>
> - Zkontrolujte využití spravované paměti pomocí [čítačů dotnet](dotnet-counters.md).
> - Vygenerujte soubor s výpisem stavu paměti.
> - Analyzujte využití paměti pomocí souboru s výpisem stavu paměti.

## <a name="prerequisites"></a>Požadavky

Kurz používá:

- [Sada .NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.
- [dotnet-trace](dotnet-trace.md) do seznamu procesů.
- [dotnet-čítače](dotnet-counters.md) pro kontrolu využití spravované paměti.
- [dotnet-dump](dotnet-dump.md) shromažďovat a analyzovat soubor s výpisem stavu paměti.
- [Ukázka ladění cílové](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) aplikace diagnostikovat.

Kurz předpokládá, že ukázka a nástroje jsou nainstalovány a připraveny k použití.

## <a name="examine-managed-memory-usage"></a>Zkontrolujte využití spravované paměti

Než začnete shromažďovat diagnostická data, která nám pomáhají způsobit tento scénář, musíte se ujistit, že skutečně vidíte nevracení paměti (růst paměti). Můžete použít [nástroj dotnet-čítače](dotnet-counters.md) k potvrzení.

Otevřete okno konzoly a přejděte do adresáře, do kterého jste stáhli a rozbalili [ukázkový ladicí cíl](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Spusťte cíl:

```dotnetcli
dotnet run
```

Ze samostatné konzoly vyhledejte ID procesu pomocí nástroje [dotnet-trace:](dotnet-trace.md)

```console
dotnet-trace ps
```

Výstup by měl být podobný:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Nyní zkontrolujte využití spravované paměti pomocí nástroje [dotnet-counters.](dotnet-counters.md) Určuje `--refresh-interval` počet sekund mezi aktualizacemi:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

Živý výstup by měl být podobný:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

Zaměření na tento řádek:

```console
    GC Heap Size (MB)                                  4
```

Můžete vidět, že spravované haldy paměti je 4 MB hned po spuštění.

Nyní stiskněte adresu `http://localhost:5000/api/diagscenario/memleak/20000`URL .

Všimněte si, že využití paměti se rozrostla na 30 MB.

```console
    GC Heap Size (MB)                                 30
```

Sledováním využití paměti, můžete bezpečně říci, že paměť roste nebo nevracení. Dalším krokem je shromáždit správná data pro analýzu paměti.

### <a name="generate-memory-dump"></a>Generovat výpis stavu paměti

Při analýze možných nevracení paměti potřebujete přístup k haldě paměti aplikace. Pak můžete analyzovat obsah paměti. Při pohledu na vztahy mezi objekty vytváříte teorie o tom, proč není paměť uvolněna. Běžný diagnostický zdroj dat je výpis stavu paměti v systému Windows nebo ekvivalentní výpis jádra v systému Linux. Chcete-li generovat výpis aplikace .NET Core, můžete použít nástroj [dotnet-dump).](dotnet-dump.md)

Pomocí [dříve spuštěného ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) vygenerujte výpis jádra Linuxu následujícím příkazem:

```dotnetcli
dotnet-dump collect -p 4807
```

Výsledkem je výpis jádra umístěný ve stejné složce.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Restartování neúspěšného procesu

Jakmile je výpis shromážděn, měli byste mít dostatek informací k diagnostice neúspěšného procesu. Pokud je neúspěšný proces spuštěn na produkčním serveru, je nyní ideální čas pro krátkodobou nápravu restartováním procesu.

V tomto kurzu jste nyní hotovi s [cíl ladění ukázkové](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) a můžete jej zavřít. Přejděte na terminál, který `Control-C`spustil server, a stiskněte klávesu .

### <a name="analyze-the-core-dump"></a>Analýza výpisu jádra

Nyní, když máte generovaný výpis jádra, použijte nástroj [dotnet-dump)](dotnet-dump.md) k analýze výpisu:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Kde `core_20190430_185145` je název výpisu jádra, který chcete analyzovat.

> [!NOTE]
> Pokud se zobrazí chyba, která si stěžuje, že *libdl.so* nebyl a nebyl nalezen, bude pravděpodobně nutné nainstalovat balíček *libc6-dev.* Další informace naleznete [v tématu Požadavky pro .NET Core na Linuxu](../linux-prerequisites.md).

Zobrazí se výzva, kde můžete zadat příkazy SOS. Obvykle první věc, kterou chcete podívat na je celkový stav spravované haldy:

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

Zde můžete vidět, že `String` většina objektů jsou buď nebo `Customer` objekty.

`dumpheap` Příkaz můžete použít znovu s tabulkou metody (MT) `String` k získání seznamu všech instancí:

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

Nyní můžete použít `gcroot` příkaz `System.String` na instanci vidět, jak a proč je objekt zakořeněný. Buďte trpěliví, protože tento příkaz trvá několik minut s haldou 30 MB:

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

Můžete vidět, `String` že je přímo `Customer` držen objektem a `CustomerCache` nepřímo v držení objektu.

Můžete pokračovat dumping z objektů `String` vidět, že většina objektů sledovat podobný vzor. V tomto okamžiku šetření za předpokladu, dostatečné informace k identifikaci hlavní příčinu ve vašem kódu.

Tento obecný postup umožňuje identifikovat zdroj hlavní nevracení paměti.

## <a name="clean-up-resources"></a>Vyčištění prostředků

V tomto kurzu jste spustili ukázkový webový server. Tento server měl být vypnut, jak je vysvětleno v části [Restartovat proces, který se nezdařil.](#restart-the-failed-process)

Můžete také odstranit soubor s výpisem stavu paměti, který byl vytvořen.

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu.

Stále zveřejňujeme další diagnostické kurzy. Můžete si přečíst koncept verze v úložišti [dotnet/diagnostics.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

Tento kurz se zabýval základy klíčových diagnostických nástrojů .NET. Informace o pokročilém použití naleznete v následující referenční dokumentaci:

* [dotnet-trace](dotnet-trace.md) do seznamu procesů.
* [dotnet-čítače](dotnet-counters.md) pro kontrolu využití spravované paměti.
* [dotnet-dump](dotnet-dump.md) shromažďovat a analyzovat soubor s výpisem stavu paměti.
