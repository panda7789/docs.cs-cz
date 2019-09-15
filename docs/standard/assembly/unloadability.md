---
title: Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core
description: Naučte se používat kolekční AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy zabraňující úspěšnému uvolnění.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 52cd864393342e2bc31f872b9d09cb484c2c8463
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972989"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core

Počínaje rozhraním .NET Core 3,0 je podporována možnost načíst a později uvolnit sadu sestavení. V .NET Framework se pro tento účel používaly vlastní domény aplikací, ale .NET Core podporuje jenom jednu výchozí doménu aplikace.

.NET Core 3,0 a novější verze podporují odinstalaci prostřednictvím <xref:System.Runtime.Loader.AssemblyLoadContext>. Můžete načíst sadu sestavení do kolekční `AssemblyLoadContext`, provést v nich metody nebo je pouze zkontrolovat pomocí reflexe a nakonec `AssemblyLoadContext`uvolnit. Tím se uvolní sestavení, `AssemblyLoadContext`která jsou načtena do.

Existuje jeden zajímavosti rozdíl mezi uvolňováním pomocí `AssemblyLoadContext` a používáním doménových aplikací. S objekty třídy AppDomains je uvolnění vynuceno. V době nenačtení jsou všechna vlákna spuštěná v cílové doméně AppDomain přerušena. spravované objekty COM vytvořené v cílové doméně AppDomain budou zničeny atd. S `AssemblyLoadContext`, uvolnění je "kooperativní". <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> Volání metody pouze inicializuje uvolnění. Uvolnění se dokončí po:

- Žádná vlákna neobsahují metody ze sestavení načtených `AssemblyLoadContext` do v jejich zásobníkech volání.
- Žádný z typů ze sestavení načtených do `AssemblyLoadContext`, instance těchto typů a sestavení nacházející se mimo rozhraní `AssemblyLoadContext` , na které odkazuje:
  - Odkazy mimo `AssemblyLoadContext`, s výjimkou slabých odkazů (<xref:System.WeakReference> nebo <xref:System.WeakReference%601>).
  - Silné popisovače GC (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal> nebo <xref:System.Runtime.InteropServices.GCHandleType>)zuvnitřivně.<xref:System.Runtime.InteropServices.GCHandleType.Pinned> `AssemblyLoadContext`

## <a name="use-collectible-assemblyloadcontext"></a>Použití kolekční AssemblyLoadContext

Tato část obsahuje podrobný návod, který ukazuje jednoduchý způsob, jak načíst aplikaci .NET Core do kolekční `AssemblyLoadContext`, spustit její vstupní bod a pak ji uvolnit. Úplnou ukázku najdete na adrese [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).

### <a name="create-a-collectible-assemblyloadcontext"></a>Vytvoření kolekční AssemblyLoadContext

Musíte třídu odvodit z <xref:System.Runtime.Loader.AssemblyLoadContext> metody a přetížit její <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodu. Tato metoda překládá odkazy na všechna sestavení, která jsou závislá na sestaveních `AssemblyLoadContext`, která jsou v takovém načtena.
Následující kód je příkladem nejjednoduššího vlastního `AssemblyLoadContext`:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak vidíte, `Load` metoda vrátí `null`. To znamená, že všechna sestavení závislostí jsou načtena do výchozího kontextu a nový kontext obsahuje pouze sestavení, která jsou do něj explicitně načtena.

Pokud chcete některé nebo všechny závislosti načíst do `AssemblyLoadContext` , můžete `AssemblyDependencyResolver` použít v `Load` metodě. Přeloží názvy sestavení na absolutní cesty k souborům sestavení pomocí souboru *. DEPS. JSON* , který je obsažen v adresáři hlavního sestavení načten do kontextu a pomocí souborů sestavení v tomto adresáři. `AssemblyDependencyResolver`

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Použít vlastní AssemblyLoadContext kolekční

V této části se předpokládá, že se `TestAssemblyLoadContext` používá zjednodušená verze.

Můžete vytvořit instanci vlastního `AssemblyLoadContext` a načíst sestavení do tohoto sestavení následujícím způsobem:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Pro každé sestavení odkazované načteným sestavením `TestAssemblyLoadContext.Load` je metoda volána, aby bylo `TestAssemblyLoadContext` možné rozhodnout, odkud se má sestavení získat. V našem případě se vrátí `null` k indikaci, že by měl být načten do výchozího kontextu z umístění, která modul runtime používá k načtení sestavení ve výchozím nastavení.

Nyní, když bylo sestavení načteno, lze z něj spustit metodu. `Main` Spusťte metodu:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Až se `Main` metoda vrátí, můžete iniciovat uvolnění `Unload` voláním metody ve vlastním `AssemblyLoadContext` nebo odložení reference, kterou máte `AssemblyLoadContext`:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

To je dostačující pro uvolnění testovacího sestavení. Pojďme to všechno využít k samostatné `TestAssemblyLoadContext`nestandardní metodě, aby se zajistilo, že se, `Assembly`a ( `Assembly.EntryPoint`a `MethodInfo` ) nedají udržovat naživu pomocí odkazů na slot zásobníku (lokálních hodnot Real-nebo JIT). To může zůstat `TestAssemblyLoadContext` ponecháno a zabránit uvolnění.

Také vrátí slabý odkaz na `AssemblyLoadContext` , aby jej bylo možné použít později ke zjištění dokončení uvolnění.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Nyní můžete tuto funkci spustit, chcete-li načíst, spustit a uvolnit sestavení.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Uvolnění se ale okamžitě nedokončilo. Jak už jsme uvedli, spoléhá se na uvolňování paměti ke shromáždění všech objektů z testovacího sestavení. V mnoha případech není nutné čekat na dokončení uvolnění. Existují však případy, kdy je užitečné zjistit, že uvolnění bylo dokončeno. Například může být vhodné odstranit soubor sestavení, který byl načten do vlastního `AssemblyLoadContext` z disku. V takovém případě lze použít následující fragment kódu. Aktivuje GC a čeká na čekající finalizační metody ve smyčce, dokud není slabý odkaz na vlastní `AssemblyLoadContext` nastavený na `null`, což značí, že byl cílový objekt shromážděn. Všimněte si, že ve většině případů je zapotřebí pouze jeden průchod smyčkou. Nicméně pro složitější případy, kdy objekty vytvořené kódem spuštěným v `AssemblyLoadContext` nástroji mají finalizační metody, mohou být potřeba další průchody.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Událost uvolnění

V některých případech může být nutné, aby kód byl načten do vlastního `AssemblyLoadContext` pro provedení nějakého vyčištění při zahájení uvolnění. Například může být nutné zastavit vlákna, vyčistit některé silné popisovače GC atd. V takových případech je možné událostpoužít.`Unloading` Obslužná rutina, která provede potřebné vyčištění, může být do této události zapojování.

### <a name="troubleshoot-unloadability-issues"></a>Řešení potíží s nezátěží

Z důvodu kooperativního charakteru uvolňování je snadné zapomenout odkazy na kolekční `AssemblyLoadContext` Alive a zabránit uvolnění. Tady je souhrn věcí (některé z nich nejsou zřejmé), které můžou obsahovat odkazy:

- Regulární odkazy držené mimo kolekční `AssemblyLoadContext`, uložené v zásobníku zásobníku nebo v registru procesoru (místní metody, buď explicitně vytvořené pomocí uživatelského kódu nebo implicitně kompilátorem JIT), statickou proměnnou nebo silným nebo připnutím popisovače GC a průjezdně směřující na:
  - Sestavení načtené do kolekční `AssemblyLoadContext`.
  - Typ z takového sestavení.
  - Instance typu z takového sestavení.
- Vlákna spouštějící kód ze sestavení načteného do kolekční `AssemblyLoadContext`.
- Instance vlastních typů bez kolekční `AssemblyLoadContext` vytvořených v kolekční`AssemblyLoadContext`
- Nedokončené <xref:System.Threading.RegisteredWaitHandle> instance s zpětnými voláními nastavenými na metody ve vlastních`AssemblyLoadContext`

Tipy pro vyhledání zásobníku zásobníku/procesoru registrace objektu:

- Předávání výsledků volání funkcí přímo do jiné funkce může vytvořit kořen, i když není k dispozici žádná uživatelská proměnná, která je vytvořena uživatelem.
- Pokud byl odkaz na objekt k dispozici v jakémkoli bodě metody, mohla by kompilátor JIT se rozhodnout zachovat odkaz v zásobníku zásobníku nebo procesoru, pokud to vyžaduje v aktuální funkci.

## <a name="debug-unloading-issues"></a>Problémy při uvolňování ladění

Problémy ladění s uvolněním můžou být zdlouhavé. Můžete se dostat do situací, kdy si nejste jisti, co může `AssemblyLoadContext` držet aktivní, ale uvolnění se nezdařilo.
Nejlepší zbraně, která vám to umožňuje, je WinDbg (LLDB v UNIX) s modulem plug-in SOS. Potřebujete zjistit, co patří do konkrétního `LoaderAllocator` `AssemblyLoadContext` typu Alive.
Tento modul plug-in vám umožní podívat se na objekty haldy GC, jejich hierarchie a kořeny.
Chcete-li načíst modul plug-in do ladicího programu, zadejte následující příkaz v příkazovém řádku ladicího programu:

V programu WinDbg (při přerušení do aplikace .NET Core se to jeví jako WinDbg):

```console
.loadby sos coreclr
```

V LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Zkusíme ladit vzorový program, který má problémy s uvolněním. Zdrojový kód je uveden níže. Při spuštění v rámci programu WinDbg se program přeruší do ladicího programu hned po pokusu o kontrolu úspěšného načtení. Pak můžete začít hledat v culprits.

Všimněte si, že pokud provádíte ladění pomocí LLDB v systému UNIX, příkazy SOS v následujících příkladech `!` nemají před nimi žádné z nich.

```console
!dumpheap -type LoaderAllocator
```

Tento příkaz vypíše všechny objekty s názvem typu obsahujícím `LoaderAllocator` v haldě GC. Tady je příklad:

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

V níže uvedené části "Statistika:" se podívejte na `MT` (`MethodTable`) patřící do `System.Reflection.LoaderAllocator`, což je objekt, o kterém se zajímá. Pak v seznamu na začátku Najděte položku s `MT` odpovídajícím záznamem a získejte adresu samotného objektu. V našem případě je to "000002b78000ce40"

Teď, když znáte adresu `LoaderAllocator` objektu, můžeme použít jiný příkaz k vyhledání jeho kořenových adresářů GC.

```console
!gcroot -all 0x000002b78000ce40 
```

Tento příkaz vypíše řetěz odkazů na objekty, které vedou k `LoaderAllocator` instanci. Seznam začíná kořenovým adresářem, který je entitou, která udržuje `LoaderAllocator` naši službu Alive, a proto je jádrem problému, který ladíte. Kořenem může být slot zásobníku, registr procesoru, popisovač GC nebo statická proměnná.

Tady je příklad výstupu `gcroot` příkazu:

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

Nyní potřebujete zjistit, kde se nachází kořenový adresář, abyste ho mohli opravit. Nejjednodušším případem je, že kořen je slot zásobníku nebo registr procesoru. V takovém případě `gcroot` zobrazuje název funkce, jejíž rámec obsahuje kořen a vlákno, které tuto funkci spouští. Těžké velká písmena jsou v případě, že kořen je statická proměnná nebo popisovač GC. 

V předchozím příkladu je první kořen místní typ `System.Reflection.RuntimeMethodInfo` uložený v rámci funkce `example.Program.Main(System.String[])` na adrese `rbp-20` (`rbp` je registr `rbp` procesoru a-20 je hexadecimální posun od tohoto registru).

Druhý kořen je normální (silný) `GCHandle` , který obsahuje odkaz na instanci `test.Test` třídy. 

Třetí kořen je připnutý `GCHandle`. Tato jedna z nich je ve skutečnosti statická proměnná. Bohužel neexistuje žádný způsob, jak říct. Statické objekty pro odkazové typy jsou uloženy v poli spravovaného objektu v interních strukturách modulu runtime.

Další případ, který může zabránit uvolnění objektu `AssemblyLoadContext` , je, když vlákno má snímek metody ze sestavení načtené `AssemblyLoadContext` do zásobníku. Můžete kontrolovat, zda jsou vyvolány spravované zásobníky volání všech vláken:

```console
~*e !clrstack
```

Příkaz znamená "použít u všech vláken `!clrstack` příkazu". Následuje výstup tohoto příkazu pro příklad. LLDB v systému UNIX bohužel nemá žádný způsob, jak použít příkaz pro všechna vlákna, takže budete muset vytvořit ruční přepnutí vláken a opakování `clrstack` příkazu.
Ignorujte všechna vlákna, kde ladicí program říká, že se nepovedlo projít spravovaný zásobník.

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

Jak vidíte, poslední vlákno má `test.Program.ThreadProc()`. Toto je funkce ze sestavení načtených do `AssemblyLoadContext`, takže `AssemblyLoadContext` udržuje Alive.

## <a name="example-source-with-unloadability-issues"></a>Příklad zdroje s problémy s načtením

Následující kód se používá v předchozím příkladu ladění.

### <a name="main-testing-program"></a>Hlavní testovací program

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program byl načten do TestAssemblyLoadContext

Následující kód představuje *test. dll* předaný `ExecuteAndUnload` metodě v hlavním testovacím programu.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
