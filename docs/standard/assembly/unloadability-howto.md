---
title: Jak používat a unloadability sestavení ladění v rozhraní .NET Core
description: Další informace o použití kolekční AssemblyLoadContext pro načítání a uvolňování spravovaných sestavení a jak ladit problémy brání uvolňování úspěch.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 2929110952feb0913f21a9c69975cc605f49c646
ms.sourcegitcommit: a532e8314c3a4b5b039656567fedff9787a31957
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251485"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Jak používat a unloadability sestavení ladění v rozhraní .NET Core

Od verze .NET Core 3.0, umožňuje načtení a uvolnění později sadu sestavení je podporován. V rozhraní .NET Framework vlastní aplikaci domén byly použity pro tento účel, ale .NET Core podporuje pouze jeden výchozí doméně aplikace.

.NET core 3.0 a novější verze podporují unloadability prostřednictvím <xref:System.Runtime.Loader.AssemblyLoadContext>. Sadu sestavení lze načíst do kolekční `AssemblyLoadContext`, spouštění metody v nich nebo je právě zkontrolovat pomocí reflexe a nakonec uvolnit `AssemblyLoadContext`. Který uvolní sestavení načtená do nich `AssemblyLoadContext`.

Existuje jeden zajímavosti rozdíl mezi použitím uvolňování `AssemblyLoadContext` a pomocí objektů třídy AppDomains. Pomocí objektů třídy AppDomains je vynucena uvolnění. Všechna vlákna spuštěná v cílové doméně aplikace při jeho uvolnění budou zrušeny, spravované objekty modelu COM, které jsou vytvořeny v cílové doméně aplikace, jsou zničeny, atd. S `AssemblyLoadContext`, je "spolupráci" uvolnění z paměti. Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metoda právě zahájí uvolnění. Uvolnění dokončí po:

- Žádná vlákna mají metody ze sestavení načtena do `AssemblyLoadContext` na svých zásobníků volání.
- Žádný z typů ze sestavení načtena do `AssemblyLoadContext`, instancí těchto typů a sestavení samotné mimo `AssemblyLoadContext` odkazuje:
  - Mimo se odkazuje `AssemblyLoadContext`, kromě slabé odkazy (<xref:System.WeakReference> nebo <xref:System.WeakReference%601>).
  - Silná popisovačů (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal> nebo <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) z uvnitř i mimo `AssemblyLoadContext`.

## <a name="using-collectible-assemblyloadcontext"></a>Pomocí kolekční AssemblyLoadContext

Tato část obsahuje podrobné podrobný kurz, který ukazuje jednoduchý způsob, jak načíst aplikaci .NET Core do kolekční `AssemblyLoadContext`, provést jeho vstupního bodu a potom ho. Můžete najít úplnou ukázku v <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.

### <a name="create-a-collectible-assemblyloadcontext"></a>Vytvoření kolekční AssemblyLoadContext

Je nutné odvozovat třídu z <xref:System.Runtime.Loader.AssemblyLoadContext> a přetížení jeho <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metoda. Že metoda překládá odkazy na všechna sestavení, která jsou závislosti sestavení načtena do které `AssemblyLoadContext`.
Následující kód je příkladem nejjednodušší vlastní `AssemblyLoadContext`:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak je vidět, `Load` vrátí metoda `null`. To znamená, že všechny závislosti sestavení jsou načtena do výchozí kontext a nový kontext obsahuje jenom sestavení explicitně do něho načtené.

Pokud chcete načíst některé nebo všechny závislosti do `AssemblyLoadContext` příliš, můžete použít `AssemblyDependencyResolver` v `Load` metody. `AssemblyDependencyResolver` Překládá názvy sestavení na absolutní sestavení pomocí cesty k souborům `*.deps.json` soubor v tomto adresáři hlavní sestavení načteno do kontextu a použití souborů sestavení v tomto adresáři obsažené.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Použít vlastní kolekční AssemblyLoadContext

V této části se předpokládá jednodušší verzi `TestAssemblyLoadContext` je používán.

Můžete vytvořit instanci vlastního `AssemblyLoadContext` a načtení sestavení do něj následujícím způsobem:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Pro každého z těchto sestavení načtené sestavení odkazuje `TestAssemblyLoadContext.Load` volání metody tak, aby `TestAssemblyLoadContext` můžete rozhodnout, kde lze získat sestavení z. V našem případě vrátí `null` k označení, že se mají načíst do výchozí kontext z umístění, které modul runtime používá k načtení sestavení ve výchozím nastavení.

Teď, když sestavení bylo načteno, můžete spustit metodu z něj. Spustit `Main` metody:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Po `Main` metoda vrací výsledek, můžete zahájit uvolnění buď voláním `Unload` metodu na vlastní `AssemblyLoadContext` nebo jsme se zbavili odkazu je nutné `AssemblyLoadContext`:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

To stačí pro uvolnění testovacího sestavení. Pojďme to všechno ve skutečnosti vložit do samostatné-inlineable metody zajistit, aby `TestAssemblyLoadContext`, `Assembly`, a `MethodInfo` ( `Assembly.EntryPoint`) nemůže být zachováno zásobníku slotu odkazy (zavedené reálném nebo JIT místní hodnoty). Který by mohl vést `TestAssemblyLoadContext` aktivní a zabránit uvolnění z paměti.

Kromě toho vrátí Slabý odkaz na `AssemblyLoadContext` tak, aby ho můžete použít později ke zjištění dokončení uvolnění z paměti.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Teď můžete spouštět tuto funkci k načtení, spuštění a uvolnění sestavení.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Ale uvolnění nedokončí okamžitě. Jak už jsme zmínili spoléhá na uvolňování paměti – ke shromažďování všech objektů z testovacího sestavení. V mnoha případech není potřeba počkat na dokončení uvolnění z paměti. Existují však případy, kdy je užitečné vědět, že byla dokončena uvolnění z paměti. Můžete například odstranit soubor sestavení, která byla načtena do vlastní `AssemblyLoadContext` z disku. V takovém případě můžete použít následující fragment kódu. Aktivuje serverem globálního katalogu a čeká na čekající finalizační metody ve smyčce do Slabý odkaz na vlastní `AssemblyLoadContext` je nastavena na `null`, která cílový objekt byl shromážděn. Všimněte si, že ve většině případů je vyžadována pouze jeden průchodu smyčky. U složitějších případech, kdy objekty vytvořené v kódu spuštěném však `AssemblyLoadContext` mají finalizační metody, může být potřeba další předá.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Události uvolňování

V některých případech může být nezbytné pro kód načtený do vlastní `AssemblyLoadContext` provést trochu pořádek v případě, uvolnění je inicioval. Například může potřebovat zastavit vlákna, odstraňte některé silné popisovačů GC atd. `Unloading` Událost lze použít v takových případech. K této události lze využívat obslužnou rutinu, která provádí potřebné vyčištění.

### <a name="troubleshoot-unloadability-issues"></a>Řešení potíží s unloadability

Vzhledem k kooperativní povaze uvolnění, je snadné zapomenout o odkazech na uchovávání věci v kolekční `AssemblyLoadContext` aktivní a brání uvolnění z paměti. Tady je přehled věcí, (některé z nich není zřejmé), která mohou obsahovat odkazy:

- Pravidelné odkazy uchovávat z mimo kolekční `AssemblyLoadContext`, uložené v datová oblast zásobníku nebo registru procesoru (metoda lokálních proměnných, buď explicitně vytvořeny pomocí uživatelského kódu nebo implicitně vypršením JIT), statická proměnná nebo popisovače GC silné / Připnutí a tranzitivně odkazuje na:
  - Sestavení načtena do kolekční `AssemblyLoadContext`.
  - Typ z těchto sestavení.
  - Instance typu z těchto sestavení.
- Vlákna spuštěná kód ze sestavení načtena do kolekční `AssemblyLoadContext`.
- Instance vlastní nekolekční `AssemblyLoadContext` vytvořené v rámci služby kolekční typy `AssemblyLoadContext`
- Čekající <xref:System.Threading.RegisteredWaitHandle> nastavit instancí pomocí zpětných volání metod ve vlastní `AssemblyLoadContext`

Pokyny k vyhledání datová oblast zásobníku / register procesoru kořenová objektu:

- Předání volání funkce výsledky přímo do jiné funkce mohou vytvořit kořenové, i když neexistuje žádný uživatel vytvořil místní proměnné.
- Pokud odkaz na objekt byla k dispozici v libovolném okamžiku v metodě, kompilátor JIT se možná rozhodli zachovávat odkaz v datová oblast zásobníku / procesoru zaregistrujte se na tak dlouho, dokud ji chce, aby se v aktuální funkci.

## <a name="debug-unloading-issues"></a>Ladění problémů uvolňování

Ladění problémů s uvolnění může být zdlouhavé. Může nastat situace, kde zatím nevíte, co můžete uchovávající `AssemblyLoadContext` aktivní, ale selže uvolnění z paměti.
Nejlepší zbraň a Postavte se nápovědu, která je pomocí modulu plug-in SOS WinDbg (LLDB v Unixu). Je potřeba najít, co je udržovat `LoaderAllocator` patřící do konkrétní `AssemblyLoadContext` zachování připojení.
Tento modul plug-in můžete se podívat na objektů haldy GC, jejich hierarchie a kořenové adresáře.
Načtení modulu plug-in do ladicího programu, zadejte následující příkaz v příkazovém řádku ladicího programu:

V rámci WinDbg (zdá se, že WinDbg provede automaticky při rozdělení do aplikace .NET Core):

```console
.loadby sos coreclr
```

V LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Chcete-li ladit ukázkový program, který má problémy s uvolnění si vyzkoušíme. Zdrojový kód je uveden níže. Při spuštění v rámci WinDbg, program se rozdělí do pravé ladicí program po pokusu o odeslání pro úspěch uvolnění z paměti. Potom můžete spustit hledání culprits.

Všimněte si, že pokud ladíte pomocí LLDB v systému Unix, v následujících příkladech příkazů SOS nemá `!` před nimi.

```console
!dumpheap -type LoaderAllocator
```

Tento příkaz vypíše všechny objekty s názvem typu obsahujícím `LoaderAllocator` , které jsou v haldě GC. Tady je příklad:

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

V "statistiky:" část pod kontrolu `MT` (`MethodTable`) patřící do `System.Reflection.LoaderAllocator`, což je objekt starosti. V seznamu na začátku, vyhledejte položku s `MT` porovnávání, že jedna a získejte adresu samotného objektu. V našem případě je "000002b78000ce40"

Teď, když víme adresu `LoaderAllocator` objektu, můžeme použít jiný příkaz Najít jeho kořeny uvolňování paměti

```console
!gcroot -all 0x000002b78000ce40 
```

Tento příkaz vypíše řetěz odkazů na objekty, které vedly k `LoaderAllocator` instance. V seznamu spustí s kořenem, což je entita, která zajišťuje naše `LoaderAllocator` aktivní a proto je základní problém, kterou ladíte. Kořen může být datová oblast zásobníku, registru procesoru, popisovače GC nebo statická proměnná.

Tady je příklad výstupu `gcroot` příkaz:

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

Teď je potřeba zjistit, kde se kořenovém adresáři nachází, můžete je vyřešit. Nejjednodušší případ je, když kořenový adresář je datová oblast zásobníku nebo registru procesoru. V takovém případě `gcroot` zobrazuje název funkce, jejíž snímek neobsahuje kořenový adresář a vlákna, které spouští tuto funkci. Obtížné případem je po kořen statická proměnná nebo popisovač uvolňování paměti. 

V předchozím příkladu první kořenový adresář je lokální proměnná typu `System.Reflection.RuntimeMethodInfo` uložené v rámci funkce `example.Program.Main(System.String[])` na adrese `rbp-20` (`rbp` je registru procesoru `rbp` a je hexadecimální posun z registru -20).

Druhý kořenový adresář je normální (silnou) `GCHandle` , který obsahuje odkaz na instanci `test.Test` třídy. 

Třetí kořenový adresář je připnutého `GCHandle`. Tato funkce je ve skutečnosti statické proměnné. Bohužel neexistuje žádný způsob, jak říct. Statické objekty pro typy odkazů jsou uloženy v poli spravovaných objektů ve strukturách vnitřního modulu runtime.

Dalším užitečným, která může zabránit uvolnění `AssemblyLoadContext` Pokud vlákno obsahuje blok metody z sestavení nahrán `AssemblyLoadContext` na svůj zásobník. Můžete zkontrolovat, že podle vypsání spravované zásobníky volání všech vláken:

```console
~*e !clrstack
```

Příkaz znamená "platí pro všechna vlákna `!clrstack` příkaz". Následuje výstupu tohoto příkazu pro příklad. Bohužel LLDB v systému Unix nemá žádný způsob, jak použít příkaz na všechna vlákna, takže budete muset ručně přepínání vlákna a opakující se uchýlíte `clrstack` příkazu.
Ignorovat všechna vlákna, kde ladicí program říká "Nelze procházet spravované zásobníku."

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

Jak je vidět, poslední vlákno má `test.Program.ThreadProc()`. Toto je funkce ze sestavení načtena do `AssemblyLoadContext`, a proto se uchová `AssemblyLoadContext` zachování připojení.

## <a name="example-source-with-unloadability-issues"></a>Příklad zdroje s unloadability problémy

Následující kód se používá v předchozím příkladu ladění.

### <a name="main-testing-program"></a>Hlavní testování aplikace

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program nahrán TestAssemblyLoadContext

Následující kód představuje `test.dll` předán `ExecuteAndUnload` metoda v hlavní aplikaci testování.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
