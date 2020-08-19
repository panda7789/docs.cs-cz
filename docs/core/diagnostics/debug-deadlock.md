---
title: Ladění zablokování – .NET Core
description: Kurz, který vás provede laděním problému se zámkem v .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 6f060e1ae801eb4eacbbd1fb67110f827c37f597
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557877"
---
# <a name="debug-a-deadlock-in-net-core"></a>Ladění zablokování v .NET Core

**Tento článek se týká: ✔️** .net Core 3,1 SDK a novějších verzí

V tomto kurzu se naučíte ladit scénář vzájemného zablokování. Pomocí poskytnutého příkladu ASP.NET Core úložiště zdrojového kódu [webové aplikace](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) můžete způsobit úmyslné zablokování. Koncový bod se bude nacházet v zablokování a akumulaci vláken. Naučíte se, jak můžete pomocí různých nástrojů analyzovat problém, jako jsou základní výpisy paměti, analýza výpisu jádra a trasování procesů.

V tomto kurzu provedete následující:

> [!div class="checklist"]
>
> - Prozkoumat zablokování aplikace
> - Vygenerovat základní soubor výpisu
> - Analyzovat vlákna procesů v souboru s výpisem paměti
> - Analýza zásobníky volání a synchronizačních bloků
> - Diagnostika a řešení zablokování

## <a name="prerequisites"></a>Požadavky

V tomto kurzu se používá:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze
- [Ukázka cíle ladění – webová aplikace](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pro aktivaci scénáře
- [dotnet – trasování](dotnet-trace.md) pro výpis procesů
- [dotnet – výpis](dotnet-dump.md) pro shromažďování a analýzu souboru s výpisem paměti

## <a name="core-dump-generation"></a>Generování základního výpisu paměti

Chcete-li prozkoumat neodezvu aplikace, základní Výpis paměti nebo výpis paměti vám umožní zkontrolovat stav svých vláken a všechny možné zámky, které mohou mít problémy s kolizí. Spusťte [ukázkovou aplikaci ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pomocí následujícího příkazu z ukázkového kořenového adresáře:

```dotnetcli
dotnet run
```

ID procesu zjistíte pomocí následujícího příkazu:

```dotnetcli
dotnet-trace ps
```

Poznamenejte si ID procesu z výstupu příkazu. Naše ID procesu bylo `4807` , ale bude se lišit. Přejděte na následující adresu URL, která je koncovým bodem rozhraní API na ukázkovém webu:

`https://localhost:5001/api/diagscenario/deadlock`

Požadavek rozhraní API na web přestane reagovat a nebude reagovat. Nechte žádost běžet asi 10-15 sekund. Pak vytvořte základní Výpis pomocí následujícího příkazu:

### <a name="linux"></a>[Linux](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[Windows](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a>Analyzovat základní Výpis paměti

Pokud chcete spustit základní analýzu výpisu paměti, otevřete základní Výpis pomocí následujícího `dotnet-dump analyze` příkazu. Argument je cesta k základnímu souboru výpisu, který byl shromážděn dříve.

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

Vzhledem k tomu, že se vám podíváte na možné zablokování, budete chtít, aby aktivita vlákna byla v procesu celkově nedodržena. Můžete použít `threads` příkaz, jak je znázorněno níže:

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

Výstup zobrazuje všechna vlákna aktuálně spuštěná v procesu s jejich přidruženým ID vlákna ladicího programu a ID vlákna operačního systému. Na základě výstupu existuje více než 300 vláken.

Dalším krokem je získat lepší informace o tom, co vlákna právě dělají, díky tomu, že se zásobník volání každé vlákno. `clrstack`Příkaz lze použít k výstupu zásobníky volání. Může to být buď výstup jednoho zásobník volání, nebo všechny zásobníky volání. Použijte následující příkaz pro výstup všech zásobníky volání pro všechna vlákna v procesu:

```console
clrstack -all
```

Reprezentativní část výstupu vypadá takto:

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

Pozorování zásobníky volání pro všechna 300 a vlákna ukazují vzor, ve kterém většina vláken sdílí společný zásobník volání:

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

Zásobník volání se zdá, že žádost byla doručena do naší metody zablokování, která zase provádí volání `Monitor.ReliableEnter` . Tato metoda označuje, že se vlákna pokoušejí zadat zámek monitoru. Čekají na dostupnost zámku. Je nejspíš uzamčeno jiným vláknem.

V dalším kroku se dozvíte, které vlákno ve skutečnosti udržuje zámek monitorování. Vzhledem k tomu, že monitory obvykle ukládají informace o uzamčení v tabulce blokování synchronizace, můžeme pomocí `syncblk` příkazu získat další informace:

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

Dva zajímavé sloupce jsou **MonitorHeld** a **vlastnící informace o vláknech**. Sloupec **MonitorHeld** ukazuje, zda je v rámci vlákna získán zámek monitoru a počet čekajících vláken. Sloupec **informace o vlastnícím vlákně** zobrazuje, které vlákno aktuálně vlastní zámek monitoru. Informace o vlákně mají tři různé podsloupce. Druhý Podsloupec zobrazuje ID vlákna operačního systému.

V tuto chvíli ví, že dvě různá vlákna (0x5634 a 0x51d4) obsahují zámek monitoru. V dalším kroku se podíváme na to, co dělají vlákna. Musíme ověřit, jestli jsou zablokované bez omezení, aby se zámky držely. Pojďme použít `setthread` `clrstack` příkazy a k přepnutí na každé vlákno a zobrazení zásobníky volání.

Chcete-li se podívat na první vlákno, spusťte `setthread` příkaz a vyhledejte index vlákna 0x5634 (náš index byl 28). Funkce zablokování čeká na získání zámku, ale zámek již vlastní. Je v zablokování čeká na zámek, který už drží.

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

Druhý podproces je podobný. Také se pokouší získat zámek, který již vlastní. Zbývající 300 a vlákna, které jsou všechny, čekají pravděpodobně na jeden z zámků, které způsobily zablokování.

## <a name="see-also"></a>Viz také

- [dotnet – trasování](dotnet-trace.md) pro výpis procesů
- [dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti
- [dotnet – vystavení](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti
- [dotnet/Diagnostika](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Jaké diagnostické nástroje jsou k dispozici v .NET Core](index.md)
