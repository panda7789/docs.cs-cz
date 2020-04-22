---
title: Asynchronní programování
description: Zjistěte, jak F# poskytuje čistou podporu pro asynchronii založenou na programovacím modelu na úrovni jazyka odvozeném z konceptů základního funkčního programování.
ms.date: 12/17/2018
ms.openlocfilehash: 0a7d400c9778e30d6b25798239f12b7b2b0e3d82
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021517"
---
# <a name="async-programming-in-f"></a>Asynchronní programování v F\#

Asynchronní programování je mechanismus, který je nezbytný pro moderní aplikace z různých důvodů. Existují dva případy primárního použití, se kterými se většina vývojářů setká:

- Prezentace procesu serveru, který může obsluhovat významný počet souběžných příchozích požadavků, při minimalizaci systémových prostředků obsazených při zpracování požadavků čeká na vstupy ze systémů nebo služeb mimo tento proces.
- Udržování responzivního uživatelského rozhraní nebo hlavního vlákna při souběžném průběhu práce na pozadí

Přestože práce na pozadí často zahrnuje využití více vláken, je důležité zvážit koncepty asynchronia a více vláken samostatně. Ve skutečnosti se jedná o samostatné obavy a jeden neznamená druhý. Tento článek popisuje samostatné koncepty podrobněji.

## <a name="asynchrony-defined"></a>Asynchronní definice

Předchozí bod - že asynchronie je nezávislá na využití více vláken - stojí za to vysvětlit trochu dále. Existují tři pojmy, které jsou někdy související, ale přísně nezávislé na sobě:

- Souběžnost; při provádění více výpočtů v překrývajících se časových obdobích.
- Paralelismus; při spuštění více výpočtů nebo několika částí jednoho výpočtu přesně ve stejnou dobu.
- Asynchronní; pokud jeden nebo více výpočtů lze spustit odděleně od toku hlavního programu.

Všechny tři jsou ortogognální pojmy, ale mohou být snadno splynutí, zvláště když jsou používány společně. Například může být nutné provést více asynchronních výpočtů paralelně. Tento vztah neznamená, že paralelismus nebo asynchronie implikují navzájem.

Pokud vezmete v úvahu etymologii slova "asynchronní", existují dva kusy:

- "a", což znamená "ne".
- "synchronní", což znamená "současně".

Když dáte tyto dva termíny dohromady, uvidíte, že "asynchronní" znamená "není ve stejnou dobu". A to je vše! Neexistuje žádný důsledek souběžnosti nebo paralelismu v této definici. To platí i v praxi.

V praxi jsou naplánovány asynchronní výpočty v F# nezávisle na toku hlavního programu. Toto nezávislé spuštění neznamená souběžnost nebo paralelismus, ani neznamená, že výpočtu vždy dochází na pozadí. Ve skutečnosti asynchronní výpočty lze dokonce spustit synchronně, v závislosti na povaze výpočtu a prostředí, ve kterých je prováděna výpočtu.

Hlavní stánek s jídlem, který byste měli mít, je, že asynchronní výpočty jsou nezávislé na toku hlavního programu. Přestože existuje jen málo záruky o tom, kdy a jak se provádí asynchronní výpočty, existují některé přístupy k jejich orchestraci a plánování. Zbytek tohoto článku zkoumá základní koncepty pro f# asynchrony a jak používat typy, funkce a výrazy integrované do F#.

## <a name="core-concepts"></a>Základní koncepty

V jazyce F# je asynchronní programování soustředěno na tři základní koncepty:

- Typ, `Async<'T>` který představuje kompozitovatelné asynchronní výpočty.
- Funkce `Async` modulu, které umožňují plánovat asynchronní práci, skládat asynchronní výpočty a transformovat asynchronní výsledky.
- `async { }` [Výpočetní výraz](../../language-reference/computation-expressions.md), který poskytuje pohodlnou syntaxi pro vytváření a řízení asynchronních výpočtů.

Tyto tři koncepty můžete vidět v následujícím příkladu:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

V příkladu `printTotalFileBytes` je funkce `string -> Async<unit>`typu . Volání funkce ve skutečnosti neprovede asynchronní výpočt. Místo toho `Async<unit>` vrátí, který funguje jako *specifikace* práce, která je provádět asynchronně. Volá `Async.AwaitTask` ve svém těle, který převádí výsledek <xref:System.IO.File.ReadAllBytesAsync%2A> na vhodný typ.

Další důležitou linkou `Async.RunSynchronously`je volání na . Toto je jedna z funkcí spuštění modulu Async, které budete muset volat, pokud chcete skutečně spustit asynchronní výpočty F#.

To je zásadní rozdíl s C#/Visual `async` Basic styl programování. V F#, asynchronní výpočty lze považovat za **studené úkoly**. Musí být explicitně zahájeny skutečně spustit. To má některé výhody, protože umožňuje kombinovat a sekvenční asynchronní práci mnohem snadněji než v jazyce C# nebo Visual Basic.

## <a name="combine-asynchronous-computations"></a>Kombinování asynchronních výpočtů

Zde je příklad, který navazuje na předchozí kombinací výpočtů:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

Jak můžete vidět, `main` funkce má poměrně málo dalších hovorů. Koncepčně provádí následující akce:

1. Transformujte argumenty příkazového `Async<unit>` řádku na `Array.map`výpočty pomocí .
2. Vytvořte, `Async<'T[]>` který naplánuje `printTotalFileBytes` a spouští výpočty paralelně při spuštění.
3. Vytvořte, `Async<unit>` který spustí paralelní výpočtu a ignorovat jeho výsledek.
4. Explicitně spustit poslední výpočtu s `Async.RunSynchronously` a blokovat, dokud nebude dokončena.

Při spuštění tohoto `printTotalFileBytes` programu běží paralelně pro každý argument příkazového řádku. Vzhledem k tomu, že asynchronní výpočty spustit nezávisle na toku programu, neexistuje žádné pořadí, ve kterém vytisknout své informace a dokončit provádění. Výpočty budou naplánovány paralelně, ale jejich pořadí provádění není zaručeno.

## <a name="sequence-asynchronous-computations"></a>Sekvenční asynchronní výpočty

Vzhledem k tomu, `Async<'T>` že je specifikace práce, nikoli již spuštěná úloha, můžete snadno provádět složitější transformace. Zde je příklad, který sekvencí sadu asynchronních výpočtů tak, aby spustit jeden po druhém.

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

To bude `printTotalFileBytes` naplánovat spuštění v pořadí `argv` prvků spíše než jejich plánování paralelně. Vzhledem k tomu, že další položka nebude naplánována až po dokončení provádění posledního výpočtu, jsou výpočty seřazeny tak, aby nedošlo k překrytí jejich provádění.

## <a name="important-async-module-functions"></a>Důležité funkce modulu Async

Při psaní asynchronního kódu v F#, obvykle budete pracovat s rámcem, který zpracovává plánování výpočtů za vás. To však není vždy případ, takže je dobré se naučit různé počáteční funkce naplánovat asynchronní práci.

Vzhledem k tomu, že f# asynchronní výpočty jsou _specifikace_ práce spíše než reprezentace práce, která je již provádí, musí být explicitně spuštěna s počáteční funkce. Existuje mnoho [funkcí spuštění asynchronního](https://msdn.microsoft.com/library/ee370232.aspx) spuštění, které jsou užitečné v různých kontextech. Následující část popisuje některé běžné funkce spuštění.

### <a name="asyncstartchild"></a>Async.StartChild

Spustí podřízený výpočetní v rámci asynchronní ho výpočtu. To umožňuje souběžné provádění více asynchronních výpočtů. Podřízený výpočet sdílí token zrušení s nadřazeným výpočtem. Pokud je nadřazený výpočetní byl zrušen, podřízený výpočt je také zrušena.

Podpis:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

Kdy použít:

- Pokud chcete spustit více asynchronních výpočtů současně, nikoli jeden po druhém, ale nemít je naplánováno paralelně.
- Pokud chcete spojit životnost podřízeného výpočtu s nadřazeným výpočtem.

Na co si dát pozor:

- Spuštění více výpočtů `Async.StartChild` s není totéž jako jejich paralelní plánování. Chcete-li naplánovat výpočty paralelně, `Async.Parallel`použijte .
- Zrušení nadřazeného výpočtu spustí zrušení všech podřízených výpočtů, které bylo spuštěno.

### <a name="asyncstartimmediate"></a>Async.StartOkamžité

Spustí asynchronní výpočt, který začíná okamžitě v aktuálním vlákně operačního systému. To je užitečné, pokud potřebujete aktualizovat něco na volající vlákno během výpočtu. Například pokud asynchronní výpočtu musí aktualizovat uI (například aktualizace indikátoru průběhu), pak `Async.StartImmediate` by měl být použit.

Podpis:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Kdy použít:

- Když potřebujete aktualizovat něco na volající vlákno uprostřed asynchronní ho výpočtu.

Na co si dát pozor:

- Kód v asynchronním výpočtu bude spuštěn na libovolné vlákno, které se stane, že je naplánováno. To může být problematické, pokud je toto vlákno nějakým způsobem citlivé, například vlákno uživatelského rozhraní. V takových `Async.StartImmediate` případech, je pravděpodobné, že nevhodné k použití.

### <a name="asyncstartastask"></a>Async.StartAsTask

Provede výpočtu ve fondu vláken. Vrátí, <xref:System.Threading.Tasks.Task%601> který bude dokončen v odpovídajícím stavu po ukončení výpočtu (vytvoří výsledek, vyvolá výjimku nebo získá zrušena). Pokud není k dispozici žádný token zrušení, použije se výchozí token zrušení.

Podpis:

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

Kdy použít:

- Když potřebujete volat do rozhraní .NET API, které očekává, <xref:System.Threading.Tasks.Task%601> že bude představovat výsledek asynchronního výpočtu.

Na co si dát pozor:

- Toto volání přidělí další `Task` objekt, který může zvýšit režii, pokud se používá často.

### <a name="asyncparallel"></a>Async.Paralelní

Naplánuje posloupnost asynchronních výpočtů, které mají být provedeny paralelně. Stupeň paralelismu lze volitelně vyladit/omezit zadáním parametru. `maxDegreesOfParallelism`

Podpis:

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Kdy ji použít:

- Pokud potřebujete spustit sadu výpočtů současně a nespoléhali se na jejich pořadí provádění.
- Pokud nepožadujete výsledky z výpočtů naplánovaných paralelně, dokud nebudou všechny dokončeny.

Na co si dát pozor:

- K výslednému poli hodnot lze získat přístup pouze po dokončení všech výpočtů.
- Výpočty budou spuštěny vždy, když skončí naplánované. Toto chování znamená, že se nemůžete spoléhat na jejich pořadí jejich provedení.

### <a name="asyncsequential"></a>Async.Sekvenční

Naplánuje posloupnost asynchronních výpočtů, které mají být provedeny v pořadí, v jakém jsou předány. První výpočtbude proveden, pak další a tak dále. Souběžně nebudou prováděny žádné výpočty.

Podpis:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Kdy ji použít:

- Pokud potřebujete provést více výpočtů v pořadí.

Na co si dát pozor:

- K výslednému poli hodnot lze získat přístup pouze po dokončení všech výpočtů.
- Výpočty budou spuštěny v pořadí, v jakém jsou předány této funkci, což může znamenat, že před vrácením výsledků uplyne více času.

### <a name="asyncawaittask"></a>Async.AwaitTask

Vrátí asynchronní výpočt, který čeká na <xref:System.Threading.Tasks.Task%601> dokončení daného a vrátí jeho výsledek jako`Async<'T>`

Podpis:

```fsharp
task: Task<'T> -> Async<'T>
```

Kdy použít:

- Při náročné rozhraní .NET API, <xref:System.Threading.Tasks.Task%601> které vrací v rámci F# asynchronní výpočtu.

Na co si dát pozor:

- Výjimky jsou zabaleny v <xref:System.AggregateException> následující konvence task paralelní knihovny a toto chování se liší od jak F# async obecně povrchy výjimky.

### <a name="asynccatch"></a>Async.Catch

Vytvoří asynchronní výpočt, který provede daný `Async<'T>`, vrácení `Async<Choice<'T, exn>>`. Pokud daný `Async<'T>` dokončí úspěšně, pak `Choice1Of2` a je vrácena s výslednou hodnotou. Pokud je vyvolána výjimka před dokončením, pak je vrácena `Choice2of2` s vyzdviženou výjimkou. Pokud se používá na asynchronní výpočtu, který se skládá z mnoha výpočtů a jeden z těchto výpočtů vyvolá výjimku, zahrnující výpočetní bude zcela zastavena.

Podpis:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Kdy použít:

- Při provádění asynchronní práce, která může selhat s výjimkou a chcete zpracovat tuto výjimku v volajícím.

Na co si dát pozor:

- Při použití kombinované nebo sekvencované asynchronní výpočty, zahrnující výpočtu se plně zastaví, pokud jeden z jeho "vnitřní" výpočty vyvolá výjimku.

### <a name="asyncignore"></a>Asynchronní.Ignorovat

Vytvoří asynchronní výpočt, který spustí daný výpočetní a ignoruje jeho výsledek.

Podpis:

```fsharp
computation: Async<'T> -> Async<unit>
```

Kdy použít:

- Pokud máte asynchronní výpočty, jejichž výsledek není potřeba. To je obdobou `ignore` kódu pro neasynchronní kód.

Na co si dát pozor:

- Pokud je `Async.Ignore` nutné použít, `Async.Start` protože chcete použít `Async<unit>`nebo jinou funkci, která vyžaduje , zvažte, zda je zahození výsledku v pořádku. Vyhněte se zahození výsledků jen tak, aby se vešly podpis typu.

### <a name="asyncrunsynchronously"></a>Async.RunSynchronously

Spustí asynchronní výpočtu a čeká na jeho výsledek na volající vlákno. Tento hovor blokuje.

Podpis:

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

Kdy ji použít:

- Pokud ji potřebujete, použijte ji pouze jednou v aplikaci - na vstupním místě pro spustitelný soubor.
- Když se nestaráte o výkon a chcete provést sadu dalších asynchronních operací najednou.

Na co si dát pozor:

- Volání `Async.RunSynchronously` blokuje volající vlákno, dokud nebude dokončeno spuštění.

### <a name="asyncstart"></a>Async.Start

Spustí asynchronní výpočtve fondu vláken, který `unit`vrátí . Nečeká na jeho výsledek. Vnořené výpočty `Async.Start` zahájené s jsou spuštěny nezávisle na nadřazeném výpočtu, který je nazval. Jejich životnost není vázána na žádné nadřazené výpočty. Pokud je nadřazený výpočetní byl zrušen, žádné podřízené výpočty jsou zrušeny.

Podpis:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Používejte pouze v případě, že:

- Máte asynchronní výpočt, který neposkytuje výsledek nebo vyžaduje zpracování jednoho.
- Nemusíte vědět, kdy je dokončen asynchronní výpočt.
- Je vám jedno, které vlákno asynchronní výpočty běží na.
- Nemusíte znát nebo hlásit výjimky vyplývající z úkolu.

Na co si dát pozor:

- Výjimky vyvolané výpočty, které `Async.Start` byly spuštěny, se volajícímu nešíří. Zásobník volání bude zcela odvinut.
- Jakákoli práce (například volání) `printfn`spuštěná s `Async.Start` nezpůsobí, že k efektu dojde v hlavním vlákně spuštění programu.

## <a name="interoperate-with-net"></a>Spolupracujte s rozhraním .NET

Pravděpodobně pracujete s knihovnou .NET nebo základnou kódu Jazyka C#, který používá asynchronní programování [asynchronního stylu async/await-style.](../../../standard/async.md) Vzhledem k tomu, že C# a <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> většina knihoven .NET používají `Async<'T>`a typy jako jejich základní abstrakce spíše než , je nutné překročit hranici mezi těmito dvěma přístupy k asynchronii.

### <a name="how-to-work-with-net-async-and-taskt"></a>Jak pracovat s asynchronní rozhraní .NET a`Task<T>`

Práce s asynchronními knihovnami .NET a základy kódu, které používají <xref:System.Threading.Tasks.Task%601> (tj. asynchronní výpočty, které mají vrácené hodnoty), je přímočará a má integrovanou podporu s F#.

`Async.AwaitTask` Funkci můžete použít k čekání na asynchronní výpočty .NET:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

`Async.StartAsTask` Pomocí této funkce můžete předat asynchronní výpočt volajícímu .NET:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Jak pracovat s asynchronní rozhraní .NET a`Task`

Chcete-li pracovat s <xref:System.Threading.Tasks.Task> rozhraními API, která používají `Async<'T>` <xref:System.Threading.Tasks.Task>(tj. asynchronní výpočty rozhraní .NET, které nevracejí hodnotu), bude pravděpodobně nutné přidat další funkci, která převede na :

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Již existuje, `Async.AwaitTask` který přijímá <xref:System.Threading.Tasks.Task> jako vstup. Pomocí tohoto a `startTaskFromAsyncUnit` dříve definované funkce můžete <xref:System.Threading.Tasks.Task> spustit a čekat typy z výpočtu asynchronní F#.

## <a name="relationship-to-multi-threading"></a>Vztah k vícevláknovým

Ačkoli závitování je uvedeno v tomto článku, existují dvě důležité věci, které je třeba mít na paměti:

1. Neexistuje žádná spřažení mezi asynchronní výpočtu a podprocesu, pokud explicitně spuštěna v aktuálním vlákně.
1. Asynchronní programování v Jazyce F# není abstrakce pro více vláken.

Například výpočtu může skutečně spustit na jeho volajícího vlákno, v závislosti na povaze práce. Výpočtmůže také "přeskočit" mezi vlákny, výpůjčky je na malé množství času dělat užitečnou práci mezi obdobími "čekání" (například když je volání sítě v tranzitu).

Přestože F# poskytuje některé schopnosti spustit asynchronní výpočtu v aktuálním vlákně (nebo explicitně není v aktuálním vlákně), asynchrony obecně není spojena s konkrétní strategie podprocesu.

## <a name="see-also"></a>Viz také

- [Asynchronní programovací model Jazyka F#](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet.com 's F# Asynchronní průvodce](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F# pro zábavu a zisk je asynchronní programování průvodce](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Async v C# a F#: Asynchronní gotchas v C #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
