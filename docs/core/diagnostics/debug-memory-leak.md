---
title: Ladění kurzu nevracení paměti
description: Naučte se ladit nevracení paměti v .NET Core.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: ff684f9b9402cb8b7b648e792a1d37ddcc96b399
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924887"
---
# <a name="debug-a-memory-leak-in-net-core"></a>Ladění nevracení paměti v .NET Core

**Tento článek se týká:** ✔️ .net Core 3,1 SDK a novějších verzí

Tento kurz demonstruje nástroje pro analýzu nevracení paměti .NET Core.

V tomto kurzu se používá ukázková aplikace, která je navržená pro úmyslně nevracení paměti. Ukázka je poskytována jako cvičení. Můžete analyzovat aplikaci, která neúmyslně nevrací paměť.

V tomto kurzu provedete následující:

> [!div class="checklist"]
>
> - Projděte si využití spravované paměti pomocí [čítače dotnet-Counters](dotnet-counters.md).
> - Vygenerujte soubor s výpisem paměti.
> - Analyzujte využití paměti pomocí souboru s výpisem paměti.

## <a name="prerequisites"></a>Požadavky

V tomto kurzu se používá:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.
- [dotnet – trasování](dotnet-trace.md) pro výpis procesů
- [dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti
- [dotnet – vypíše stav](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti.
- [Ukázková cílová aplikace ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) , která se má diagnostikovat

V tomto kurzu se předpokládá, že je nainstalovaná ukázka a nástroje, které jsou připravené k použití.

## <a name="examine-managed-memory-usage"></a>Prověření využití spravované paměti

Než začnete shromažďovat diagnostická data, která nám pomůžou hlavní příčinu tohoto scénáře, musíte se ujistit, že se skutečně zobrazuje nevracení paměti (nárůst paměti). K potvrzení můžete použít nástroj [dotnet-Counters](dotnet-counters.md) .

Otevřete okno konzoly a přejděte do adresáře, do kterého jste stáhli, a vraťte se do [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Spusťte cíl:

```dotnetcli
dotnet run
```

V samostatné konzole Najděte ID procesu pomocí nástroje [dotnet-Trace](dotnet-trace.md) Tool:

```console
dotnet-trace ps
```

Výstup by měl vypadat přibližně takto:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Teď pomocí nástroje [dotnet-Counters](dotnet-counters.md) ověřte využití spravované paměti. `--refresh-interval`Určuje počet sekund mezi aktualizacemi:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

Živý výstup by měl vypadat přibližně takto:

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

Zaměřit se na tento řádek:

```console
    GC Heap Size (MB)                                  4
```

Můžete zjistit, že paměť spravované haldy je 4 MB, a to hned po spuštění.

Teď stiskněte adresu URL `https://localhost:5001/api/diagscenario/memleak/20000` .

Pozor, aby využití paměti bylo nárůst na 30 MB.

```console
    GC Heap Size (MB)                                 30
```

Sledováním využití paměti můžete bezpečně vyslovit, že se paměť zvětšuje nebo nevrací. Dalším krokem je shromáždění správných dat pro analýzu paměti.

### <a name="generate-memory-dump"></a>Generovat výpis paměti

Při analýze možné nevracení paměti potřebujete přístup k haldě paměti aplikace. Pak můžete analyzovat obsah paměti. Při prohlížení vztahů mezi objekty vytvoříte teorie, proč se paměť neuvolňuje. Běžný zdroj dat diagnostiky je výpis paměti ve Windows nebo ekvivalentní základní Výpis stavu systému Linux. Chcete-li vygenerovat výpis paměti aplikace .NET Core, můžete použít nástroj [dotnet-dump)](dotnet-dump.md) .

Pomocí dříve spuštěného [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) spusťte následující příkaz, který vygeneruje výpis jádra pro Linux:

```dotnetcli
dotnet-dump collect -p 4807
```

Výsledkem je základní Výpis paměti umístěný ve stejné složce.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Restartování neúspěšného procesu

Po shromáždění výpisu paměti by měly být k dispozici dostatečné informace pro diagnostiku neúspěšného procesu. Pokud se neúspěšný proces na provozním serveru běží, je teď to ideální čas pro krátkodobou nápravu, protože proces se restartuje.

V tomto kurzu jste teď hotovi s [ukázkovým cílem ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) a můžete ho zavřít. Přejděte do terminálu, který spustil server, a stiskněte klávesy <kbd>CTRL + C</kbd>.

### <a name="analyze-the-core-dump"></a>Analyzovat základní Výpis paměti

Teď, když máte vygenerovaný základní Výpis, použijte k analýze výpisu nástroj [dotnet-dump](dotnet-dump.md) :

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Kde `core_20190430_185145` je název základního výpisu, který chcete analyzovat.

> [!NOTE]
> Pokud se zobrazí chyba s stížností, že se *libdl.so* nedá najít, možná budete muset nainstalovat balíček *libc6-dev* . Další informace najdete v tématu [předpoklady pro .NET Core v systému Linux](../install/dependencies.md?pivots=os-linux).

Zobrazí se výzva, kde můžete zadat SOS příkazy. Obvykle první věc, kterou chcete sledovat, je celkový stav spravované haldy:

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

Tady vidíte, že většinu objektů jsou `String` nebo `Customer` objekty.

Příkaz můžete použít `dumpheap` znovu s tabulkou metod (MT) a získat tak seznam všech `String` instancí:

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

Nyní můžete použít `gcroot` příkaz na `System.String` instanci, abyste viděli, jak a proč je objekt rootem. Být pacient, protože tento příkaz trvá několik minut s haldou 30 MB:

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

Můžete vidět, že `String` je přímo držen `Customer` objektem a nepřímo drženým `CustomerCache` objektem.

Můžete pokračovat v oddálení objektů a prohlédnout si, že většina `String` objektů dodržuje podobný vzor. V tomto okamžiku šetření poskytlo dostatečné informace pro identifikaci hlavní příčiny ve vašem kódu.

Tento obecný postup vám umožní identifikovat zdroj nevracení velkých pamětí.

## <a name="clean-up-resources"></a>Vyčištění prostředků

V tomto kurzu jste spustili ukázkový webový server. Tento server by měl být vypnutý, jak je vysvětleno v části [restartování procesu selhání](#restart-the-failed-process) .

Můžete také odstranit soubor s výpisem paměti, který byl vytvořen.

## <a name="see-also"></a>Viz také

- [dotnet – trasování](dotnet-trace.md) pro výpis procesů
- [dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti
- [dotnet – vystavení](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti
- [dotnet/Diagnostika](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Ladění vysokého výkonu procesoru v .NET Core](debug-highcpu.md)
