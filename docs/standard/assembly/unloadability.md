---
title: Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core
description: Zjistěte, jak používat sběratelské AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy bránící úspěchu uvolnění.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159738"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core

Počínaje rozhraním .NET Core 3.0 je podporována možnost načíst a později uvolnit sadu sestavení. V rozhraní .NET Framework byly k tomuto účelu použity vlastní domény aplikací, ale .NET Core podporuje jenom jednu výchozí doménu aplikace.

Rozhraní .NET Core 3.0 a novější <xref:System.Runtime.Loader.AssemblyLoadContext>verze podporují možnost uvolnění prostřednictvím . Sadu sestavení můžete načíst do sběratelské , `AssemblyLoadContext`spustit metody v nich nebo je `AssemblyLoadContext`pouze zkontrolovat pomocí odrazu a nakonec uvolnit . To uvolní sestavení naložené `AssemblyLoadContext`do .

Existuje jeden pozoruhodný rozdíl mezi uvolněnípomocí `AssemblyLoadContext` a používáním AppDomains. S AppDomains uvolnění je vynuceno. V době uvolnění jsou všechna vlákna spuštěná v cílové appdomain přerušena, spravované objekty COM vytvořené v cílové službě AppDomain jsou zničeny a tak dále. S `AssemblyLoadContext`, vykládka je "spolupráce". Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metody pouze iniciuje uvolnění. Vykládka končí po:

- Žádná vlákna mají metody z sestavení `AssemblyLoadContext` načtených do jejich zásobníků volání.
- Žádný z typů ze sestavení načtených do `AssemblyLoadContext`instancí těchto typů a samotných sestavení není odkazován:
  - Odkazy mimo písmeno `AssemblyLoadContext`a) s<xref:System.WeakReference> výjimkou <xref:System.WeakReference%601>slabých odkazů ( nebo ).
  - Silné popisovače systému uvolňování paměti[(GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) nebo [GCHandleType.Pinned)](xref:System.Runtime.InteropServices.GCHandleType.Pinned) `AssemblyLoadContext`z vnitřníi i vnější strany .

## <a name="use-collectible-assemblyloadcontext"></a>Použití sběratelského kontextu AssemblyLoadContext

Tato část obsahuje podrobný podrobný kurz, který ukazuje jednoduchý způsob, jak načíst `AssemblyLoadContext`aplikaci .NET Core do sběratelské položky , spustit vstupní bod a potom ji uvolnit. Kompletní ukázku najdete [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)na adrese .

### <a name="create-a-collectible-assemblyloadcontext"></a>Vytvoření sběratelského kontextu AssemblyLoadContext

Je třeba odvodit <xref:System.Runtime.Loader.AssemblyLoadContext> třídu <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> z a přetížení jeho metody. Tato metoda řeší odkazy na všechna sestavení, která jsou závislosti `AssemblyLoadContext`sestavení načtendo tohoto .

Následující kód je příkladem nejjednodušší vlastní `AssemblyLoadContext`:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak můžete vidět, `Load` metoda `null`vrátí . To znamená, že všechna sestavení závislostí jsou načtena do výchozího kontextu a nový kontext obsahuje pouze sestavení, která jsou do něj explicitně načtena.

Pokud chcete načíst některé nebo všechny závislosti `AssemblyLoadContext` do příliš, `AssemblyDependencyResolver` můžete `Load` použít v metodě. Překládá `AssemblyDependencyResolver` názvy sestavení na absolutní cesty souboru sestavení. Překladač používá soubor *.deps.json* a soubory sestavení v adresáři hlavního sestavení načteného do kontextu.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Použití vlastního sběratelského objektu AssemblyLoadContext

Tato část předpokládá, že `TestAssemblyLoadContext` se používá jednodušší verze programu.

Můžete vytvořit instanci `AssemblyLoadContext` vlastní a načíst sestavení do něj takto:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Pro každou sestavu, na kterou odkazuje `TestAssemblyLoadContext.Load` načtené sestavení, `TestAssemblyLoadContext` je metoda volána tak, aby se mohla rozhodnout, odkud sestavení získá. V našem případě `null` se vrátí k označení, že by měla být načtena do výchozího kontextu z umístění, která runtime používá k načtení sestavení ve výchozím nastavení.

Nyní, když bylo načteno sestavení, můžete z něj spustit metodu. Spusťte metodu: `Main`

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Po `Main` vrátí metoda, můžete zahájit uvolnění `Unload` buď voláním `AssemblyLoadContext` metody na vlastní nebo zbavit `AssemblyLoadContext`odkazu, který máte na :

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

To je dostačující k uvolnění testovacího sestavení. Pojďme vlastně dát to všechno do samostatné non-inlineable `TestAssemblyLoadContext`metoda `Assembly`zajistit, aby , , a `MethodInfo` `Assembly.EntryPoint`() nelze udržet naživu pomocí zásobníku slot odkazy (real- nebo JIT-představil místní). To by `TestAssemblyLoadContext` mohlo udržet naživu a zabránit vyložit.

Také vrátit slabý odkaz `AssemblyLoadContext` na tak, aby můžete použít později ke zjištění dokončení uvolnění.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Nyní můžete spustit tuto funkci k načtení, spuštění a uvolnění sestavení.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Uvolnění však není dokončena okamžitě. Jak již bylo zmíněno, spoléhá na uvolňování shromažďovat všechny objekty z testovacího sestavení. V mnoha případech není nutné čekat na dokončení uvolnění. Existují však případy, kdy je užitečné vědět, že uvolnění bylo dokončeno. Můžete například odstranit soubor sestavení, který byl načten `AssemblyLoadContext` do vlastní z disku. V takovém případě lze použít následující fragment kódu. Aktivuje uvolňování paměti a čeká na čekající finalizační metody ve `AssemblyLoadContext` `null`smyčce, dokud není nastaven slabý odkaz na vlastní , což znamená, že byl shromážděn cílový objekt. Ve většině případů je vyžadován pouze jeden průchod smyčkou. Však pro složitější případy, kde objekty `AssemblyLoadContext` vytvořené kód spuštěnv mají finalizační metody, může být zapotřebí další průchody.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Událost Uvolnění

V některých případech může být nezbytné pro `AssemblyLoadContext` kód načtendo vlastní provést některé vyčištění při zahájení uvolnění. Může například potřebovat zastavit vlákna nebo vyčistit silné úchyty GC. Událost `Unloading` lze použít v takových případech. Obslužná rutina, která provádí nezbytné vyčištění může být připojen k této události.

### <a name="troubleshoot-unloadability-issues"></a>Poradce při potížích s vyprodučností

Vzhledem k kooperativní povaze vykládky, je snadné zapomenout na odkazy, které `AssemblyLoadContext` mohou být udržet věci ve sběratelství naživu a brání vykládce. Zde je přehled entit (některé z nich non-zřejmé), které mohou obsahovat odkazy:

- Pravidelné odkazy držené mimo sběratelskou `AssemblyLoadContext` položku, které jsou uloženy v zásobníku slotu nebo registru procesoru (místní metoda, buď explicitně vytvořené uživatelským kódem nebo implicitně kompilátorem just-in-time (JIT), statickou proměnnou nebo silným popisovačem GC (připnutí) a přechodně odkazujícím na:
  - Sestava naložená do `AssemblyLoadContext`sběratelského .
  - Typ z takového sestavení.
  - Instance typu z takového sestavení.
- Vlákna spuštěnkód ze sestavení načtendo `AssemblyLoadContext`sběratelské .
- Instance vlastních nesběratelských `AssemblyLoadContext` typů vytvořených uvnitř `AssemblyLoadContext`sběratelského souboru .
- Čekající <xref:System.Threading.RegisteredWaitHandle> instance s zpětná volání nastavená `AssemblyLoadContext`na metody ve vlastní .

> [!TIP]
> Odkazy na objekty, které jsou uloženy v zásobníku sloty `AssemblyLoadContext` nebo registrů procesorů a které by mohly zabránit uvolnění může dojít v následujících situacích:
>
> - Při volání funkce výsledky jsou předány přímo do jiné funkce, i když neexistuje žádná uživatelská vytvořená místní proměnná.
> - Při kompilátoru JIT udržuje odkaz na objekt, který byl k dispozici v určitém okamžiku v metodě.

## <a name="debug-unloading-issues"></a>Ladění problémů s uvolněním

Ladění problémy s uvolněním může být únavné. Můžete se dostat do situací, kdy nevíte, `AssemblyLoadContext` co může být držení naživu, ale vyložit selže. Nejlepší zbraň na pomoc s tím je WinDbg (LLDB na Unix) s PLUGIN SOS. Musíte najít to, co `LoaderAllocator` drží majetek `AssemblyLoadContext` k určitému živu. Modul plug-in SOS umožňuje podívat se na objekty haldy GC, jejich hierarchie a kořeny.

Chcete-li načíst plugin do ladicího programu, zadejte do příkazového řádku ladicího programu následující příkaz:

V WinDbg (zdá se, windbg dělá, že automaticky při vloupání do .NET Core aplikace):

```console
.loadby sos coreclr
```

V LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Pojďme ladit ukázkový program, který má problémy s uvolněním. Zdrojový kód je uveden níže. Při spuštění pod WinDbg, program přejde do ladicího programu hned po pokusu o kontrolu úspěchu uvolnění. Pak můžete začít hledat viníky.

> [!TIP]
> Pokud ladíte pomocí LLDB na Unixu, příkazy SOS v `!` následujících příkladech nemají před sebou.

```console
!dumpheap -type LoaderAllocator
```

Tento příkaz vypíše všechny objekty `LoaderAllocator` s názvem typu, které jsou v haldě GC. Zde naleznete příklad:

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

V části "Statistika:" níže `MT` `MethodTable`zkontrolujte ( `System.Reflection.LoaderAllocator`), který patří do , což je objekt, na kterém nám záleží. Potom v seznamu na začátku najděte `MT` položku s odpovídající, že jeden a získat adresu samotného objektu. V našem případě je to "000002b78000ce40".

Nyní, když známe adresu `LoaderAllocator` objektu, můžeme použít jiný příkaz k nalezení jeho kořenů GC:

```console
!gcroot -all 0x000002b78000ce40
```

Tento příkaz vypíše řetězec odkazů na `LoaderAllocator` objekty, které vedou k instanci. Seznam začíná kořenem, což je entita, která udržuje naše `LoaderAllocator` naživu, a proto je jádrem problému. Kořen může být zásobníku slot, registr procesoru, popisovač GC nebo statické proměnné.

Zde je příklad výstupu příkazu: `gcroot`

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

Dalším krokem je zjistit, kde je kořen umístěn, abyste ho mohli opravit. Nejjednodušší případ je, když kořen je zásobníku slot nebo registr procesoru. V takovém případě `gcroot` zobrazí název funkce, jejíž rámec obsahuje kořen a vlákno provádění této funkce. Obtížný případ je, když kořen je statická proměnná nebo popisovač GC.

V předchozím příkladu je první kořen `System.Reflection.RuntimeMethodInfo` místní hosti typu `example.Program.Main(System.String[])` uloženého v rámci funkce na adrese `rbp-20` (`rbp` je registr procesoru `rbp` a -20 je šestnáctkový posun od tohoto registru).

Druhý kořen je normální (silný), `GCHandle` který obsahuje odkaz `test.Test` na instanci třídy.

Třetí kořen je připnutý `GCHandle`. Tenhle je vlastně statická proměnná, ale bohužel, neexistuje žádný způsob, jak říct. Statika pro typy odkazů jsou uloženy v poli spravovaného objektu v interních runtime strukturách.

Jiný případ, který může `AssemblyLoadContext` zabránit uvolnění je, když vlákno má rámec metody `AssemblyLoadContext` ze sestavy načtendo jeho zásobníku. Můžete zkontrolovat, že dumpingem spravované zásobníky volání všech vláken:

```console
~*e !clrstack
```

Příkaz znamená "použít pro všechna `!clrstack` vlákna příkaz". Následuje výstup tohoto příkazu pro příklad. Bohužel, LLDB na Unixu nemá žádný způsob, jak použít příkaz pro všechna vlákna, `clrstack` takže musíte ručně přepnout vlákna a opakovat příkaz. Ignorujte všechna vlákna, kde ladicí program říká "Nelze procházet spravované zásobníku".

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

Jak můžete vidět, poslední `test.Program.ThreadProc()`vlákno má . Toto je funkce ze sestavení `AssemblyLoadContext`načtendo , `AssemblyLoadContext` a tak udržuje naživu.

## <a name="example-source-with-unloadability-issues"></a>Příklad zdroje s problémy s vykládkou

Následující kód se používá v předchozím příkladu ladění.

### <a name="main-testing-program"></a>Hlavní testovací program

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program načtený do kontextu TestAssemblyLoadContext

Následující kód představuje *test.dll* předán `ExecuteAndUnload` metodě v hlavním testovacím programu.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
