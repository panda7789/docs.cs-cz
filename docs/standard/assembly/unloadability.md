---
title: Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core
description: Naučte se používat kolekční AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy zabraňující úspěšnému uvolnění.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159738"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core

Počínaje rozhraním .NET Core 3,0 je podporována možnost načíst a později uvolnit sadu sestavení. V .NET Framework se pro tento účel používaly vlastní domény aplikací, ale .NET Core podporuje jenom jednu výchozí doménu aplikace.

.NET Core 3,0 a novější verze podporují odinstalaci prostřednictvím <xref:System.Runtime.Loader.AssemblyLoadContext>. Můžete načíst sadu sestavení do kolekční `AssemblyLoadContext`, provést v nich metody nebo je pouze zkontrolovat pomocí reflexe a nakonec uvolnit `AssemblyLoadContext`. Tím se uvolní sestavení načtená do `AssemblyLoadContext`.

Existuje jeden zajímavosti rozdíl mezi uvolněním pomocí `AssemblyLoadContext` a pomocí objektů třídy AppDomains. S objekty třídy AppDomains je uvolnění vynuceno. V době nenačtení jsou všechna vlákna spuštěná v cílové doméně AppDomain přerušena. spravované objekty COM vytvořené v cílové doméně AppDomain budou zničeny a tak dále. Při `AssemblyLoadContext`je uvolnění "kooperativní". Volání metody <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> pouze inicializuje uvolnění. Uvolnění se dokončí po:

- Žádná vlákna neobsahují metody ze sestavení načtených do `AssemblyLoadContext` na jejich zásobníkech volání.
- Žádný z typů ze sestavení načtených do `AssemblyLoadContext`, instance těchto typů a samotná sestavení jsou odkazována pomocí:
  - Odkazy mimo `AssemblyLoadContext`, s výjimkou slabých odkazů (<xref:System.WeakReference> nebo <xref:System.WeakReference%601>).
  - Silné popisovače uvolňování paměti (GC) ([GCHandleType. Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) nebo [GCHandleType. připnutý](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) zevnitř i mimo `AssemblyLoadContext`.

## <a name="use-collectible-assemblyloadcontext"></a>Použití kolekční AssemblyLoadContext

Tato část obsahuje podrobný návod, který ukazuje jednoduchý způsob, jak načíst aplikaci .NET Core do kolekční `AssemblyLoadContext`, spustit její vstupní bod a pak ji uvolnit. Úplnou ukázku najdete na [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).

### <a name="create-a-collectible-assemblyloadcontext"></a>Vytvoření kolekční AssemblyLoadContext

Musíte třídu odvodit z <xref:System.Runtime.Loader.AssemblyLoadContext> a přetížit její <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodu. Tato metoda překládá odkazy na všechna sestavení, která jsou závislá na sestaveních, která jsou načtena do tohoto `AssemblyLoadContext`.

Následující kód je příkladem nejjednoduššího vlastního `AssemblyLoadContext`:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak vidíte, metoda `Load` vrátí `null`. To znamená, že všechna sestavení závislostí jsou načtena do výchozího kontextu a nový kontext obsahuje pouze sestavení, která jsou do něj explicitně načtena.

Pokud chcete některé nebo všechny závislosti načíst do `AssemblyLoadContext`, můžete použít `AssemblyDependencyResolver` v metodě `Load`. `AssemblyDependencyResolver` vyřeší názvy sestavení k absolutním cestám souborů sestavení. Překladač používá soubor *. DEPS. JSON* a soubory sestavení v adresáři hlavního sestavení načteného do kontextu.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Použít vlastní AssemblyLoadContext kolekční

V této části se předpokládá, že se používá jednodušší verze `TestAssemblyLoadContext`.

Můžete vytvořit instanci vlastního `AssemblyLoadContext` a načíst do něj sestavení následujícím způsobem:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Pro každé sestavení, na které odkazuje načtené sestavení, je volána metoda `TestAssemblyLoadContext.Load`, aby `TestAssemblyLoadContext` mohl rozhodnout, kde získat sestavení z. V našem případě vrátí `null`, aby označoval, že by měl být načten do výchozího kontextu z umístění, která modul runtime používá k načítání sestavení ve výchozím nastavení.

Nyní, když bylo sestavení načteno, lze z něj spustit metodu. Spusťte metodu `Main`:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Po návratu metody `Main` můžete iniciovat uvolnění voláním metody `Unload` na vlastní `AssemblyLoadContext` nebo odložením odkazu, který máte `AssemblyLoadContext`:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

To je dostačující pro uvolnění testovacího sestavení. Pojďme to všechno využít k samostatné nestandardní metodě, aby se zajistilo, že `TestAssemblyLoadContext`, `Assembly`a `MethodInfo` (`Assembly.EntryPoint`) se nedají udržovat naživu pomocí odkazů na slot zásobníku (lokálních hodnot Real-nebo JIT). To může zůstat `TestAssemblyLoadContext` Alive a zabránit uvolnění.

Také vrátí slabý odkaz na `AssemblyLoadContext`, aby jej bylo možné použít později ke zjištění dokončení uvolnění.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Nyní můžete tuto funkci spustit, chcete-li načíst, spustit a uvolnit sestavení.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Uvolnění se ale okamžitě nedokončilo. Jak už jsme uvedli, spoléhá se na systém uvolňování paměti ke shromáždění všech objektů z testovacího sestavení. V mnoha případech není nutné čekat na dokončení uvolnění. Existují však případy, kdy je užitečné zjistit, že uvolnění bylo dokončeno. Například může být vhodné odstranit soubor sestavení, který byl načten do vlastního `AssemblyLoadContext` z disku. V takovém případě lze použít následující fragment kódu. Aktivuje uvolňování paměti a čeká na čekající finalizační metody ve smyčce, dokud nebude slabý odkaz na vlastní `AssemblyLoadContext` nastaven na `null`, což značí, že byl cílový objekt shromážděn. Ve většině případů je zapotřebí pouze jeden průchod smyčkou. Nicméně pro složitější případy, kdy objekty vytvořené kódem běžícím v `AssemblyLoadContext` mají finalizační metody, mohou být potřeba další průchody.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Událost uvolnění

V některých případech může být nutné, aby kód byl načten do vlastního `AssemblyLoadContext` k provedení nějakého vyčištění při zahájení uvolnění. Například může být nutné zastavit vlákna nebo vyčistit silné obslužné rutiny GC. V takových případech lze použít událost `Unloading`. Obslužná rutina, která provede potřebné vyčištění, může být do této události zapojování.

### <a name="troubleshoot-unloadability-issues"></a>Řešení potíží s nezátěží

Z důvodu kooperativního charakteru uvolňování je snadné zapomenout odkazy, které mohou udržet kolekční `AssemblyLoadContext` Alive a zabránit uvolnění. Tady je souhrn entit (některé z nich není zřejmé), které můžou obsahovat odkazy:

- Běžné odkazy držené mimo kolekční `AssemblyLoadContext`, které jsou uloženy v zásobníku zásobníku nebo v registru procesoru (místní metody, buď explicitně vytvořené kódem uživatele nebo implicitně kompilátorem JIT (just-in-time)), statickou proměnnou nebo silným (připnutím) popisovač GC a umožňujícím přechod na:
  - Sestavení načtené do kolekční `AssemblyLoadContext`.
  - Typ z takového sestavení.
  - Instance typu z takového sestavení.
- Vlákna spouštějící kód ze sestavení načteného do kolekční `AssemblyLoadContext`.
- Instance vlastních typů, které nejsou kolekční `AssemblyLoadContext` vytvořené v `AssemblyLoadContext`kolekční.
- Čeká se na <xref:System.Threading.RegisteredWaitHandle> instance s zpětnými voláními nastavenými na metody v vlastní `AssemblyLoadContext`.

> [!TIP]
> Odkazy na objekty, které jsou uloženy v paticích zásobníku nebo v registrech procesorů a které by mohly zabránit vykládku `AssemblyLoadContext` mohou nastat v následujících situacích:
>
> - Když jsou výsledky volání funkce předány přímo jiné funkci, i když není k dispozici místní proměnná vytvořená uživatelem.
> - Když kompilátor JIT udržuje odkaz na objekt, který byl k dispozici v nějakém okamžiku v metodě.

## <a name="debug-unloading-issues"></a>Problémy při uvolňování ladění

Problémy ladění s uvolněním můžou být zdlouhavé. Můžete se dostat do situací, kdy nevíte, co by mohlo držet `AssemblyLoadContext` Alive, ale uvolnění se nezdařilo. Nejlepší zbraně, která vám to umožňuje, je WinDbg (LLDB v UNIX) s modulem plug-in SOS. Potřebujete najít, co udržuje `LoaderAllocator` patří do konkrétní `AssemblyLoadContext` Alive. Modul plug-in SOS vám umožní podívat se na objekty haldy GC, jejich hierarchie a kořeny.

Chcete-li načíst modul plug-in do ladicího programu, zadejte následující příkaz v příkazovém řádku ladicího programu:

V programu WinDbg (při přerušení do aplikace .NET Core se to jeví jako WinDbg):

```console
.loadby sos coreclr
```

V LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Pojďme ladit ukázkový program, který obsahuje problémy s uvolněním. Zdrojový kód je uveden níže. Při spuštění v rámci programu WinDbg se program přeruší do ladicího programu hned po pokusu o kontrolu úspěšného načtení. Pak můžete začít hledat v culprits.

> [!TIP]
> Pokud ladíte pomocí LLDB v systému UNIX, příkazy SOS v následujících příkladech nemají `!` před nimi.

```console
!dumpheap -type LoaderAllocator
```

Tento příkaz vypíše všechny objekty s názvem typu, který obsahuje `LoaderAllocator` v haldě GC. Zde naleznete příklad:

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

V níže uvedené části "Statistika:" si Projděte `MT` (`MethodTable`) patřící do `System.Reflection.LoaderAllocator`, což je objekt, o kterém se zajímá. Potom v seznamu na začátku Najděte položku s `MT` odpovídající této adrese a získejte adresu samotného objektu. V našem případě je to "000002b78000ce40".

Teď, když znáte adresu `LoaderAllocator`ho objektu, můžeme k vyhledání jeho kořenů GC použít jiný příkaz:

```console
!gcroot -all 0x000002b78000ce40
```

Tento příkaz vypíše řetěz odkazů na objekty, které vedou k instanci `LoaderAllocator`. Seznam začíná kořenovým adresářem, který je entitou, která udržuje naši `LoaderAllocator` Alive, a proto je jádrem problému. Kořenem může být slot zásobníku, registr procesoru, popisovač GC nebo statická proměnná.

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

Dalším krokem je zjistit, kde se nachází kořenový adresář, abyste ho mohli opravit. Nejjednodušším případem je, že kořen je slot zásobníku nebo registr procesoru. V takovém případě `gcroot` zobrazuje název funkce, jejíž rámec obsahuje kořen a vlákno, které tuto funkci spouští. Těžké velká písmena jsou v případě, že kořen je statická proměnná nebo popisovač GC.

V předchozím příkladu je prvním kořenem typ `System.Reflection.RuntimeMethodInfo` uložený v rámci `example.Program.Main(System.String[])` funkce na adrese `rbp-20` (`rbp` je registr registru `rbp` a-20 je hexadecimální posun od tohoto registru).

Druhý kořen je normální (silný) `GCHandle`, která obsahuje odkaz na instanci `test.Test` třídy.

Třetí kořen je připnutý `GCHandle`. Toto je vlastně statická proměnná, ale bohužel neexistuje žádný způsob, jak říct. Statické objekty pro odkazové typy jsou uloženy v poli spravovaného objektu v interních strukturách modulu runtime.

Další případ, který může zabránit uvolnění `AssemblyLoadContext`, je, když vlákno obsahuje snímek metody ze sestavení načteného do `AssemblyLoadContext` v jeho zásobníku. Můžete kontrolovat, zda jsou vyvolány spravované zásobníky volání všech vláken:

```console
~*e !clrstack
```

Příkaz znamená "použít u všech vláken `!clrstack` příkazu". Následuje výstup tohoto příkazu pro příklad. LLDB v systému UNIX bohužel nemá žádný způsob, jak použít příkaz pro všechna vlákna, takže musíte ručně přepnout vlákna a zopakovat příkaz `clrstack`. Ignorujte všechna vlákna, kde ladicí program říká, že se nepovedlo projít spravovanou sadu.

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

Jak vidíte, poslední vlákno má `test.Program.ThreadProc()`. Toto je funkce ze sestavení načtených do `AssemblyLoadContext`, takže udržuje `AssemblyLoadContext` Alive.

## <a name="example-source-with-unloadability-issues"></a>Příklad zdroje s problémy s načtením

Následující kód se používá v předchozím příkladu ladění.

### <a name="main-testing-program"></a>Hlavní testovací program

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program byl načten do TestAssemblyLoadContext

Následující kód představuje *test. dll* předaný metodě `ExecuteAndUnload` v hlavním testovacím programu.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
