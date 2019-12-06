---
title: Asynchronní programování vF#
description: Naučte F# se, jak poskytuje čistou podporu pro asynchronii na základě programovacího modelu na úrovni jazyka odvozeného od konceptů základních funkcí programování.
ms.date: 12/17/2018
ms.openlocfilehash: 583b0f5154e6ad8875b21503cfb78f70a069ff7b
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837100"
---
# <a name="async-programming-in-f"></a>Asynchronní programování v F\#

Asynchronní programování je mechanismus, který je nezbytný pro moderní aplikace z nejrůznějších důvodů. K dispozici jsou dva primární případy použití, ke kterým dojde ve většině vývojářů:

- Prezentující proces serveru, který může obsluhovat velký počet souběžných příchozích požadavků a současně minimalizuje systémové prostředky, které při zpracování požadavků čekají na vstupy ze systémů nebo služeb, které jsou pro tento proces externí.
- Údržba s reagujícím uživatelským rozhraním nebo hlavním vláknem při současném průběhu práce na pozadí

I když práce na pozadí často zahrnuje využití více vláken, je důležité vzít v úvahu koncepty asynchronii a multithreading samostatně. Ve skutečnosti se jedná o samostatné obavy a jedna z nich neznamená jinou. Jak je uvedeno v tomto článku, popište to podrobněji.

## <a name="asynchrony-defined"></a>Asynchronii – definováno

Předchozí bod – tento asynchronii je nezávislý na využití více vláken – je vysvětlovat trochu dál. Existují tři koncepty, které jsou někdy související, ale výhradně nezávisle na sobě.

- Concurrency Když je v překrývajících se časových obdobích prováděno více výpočtů.
- Paralelismu v případě, že se více výpočetních nebo několika částí jednoho výpočtu spouští přesně ve stejnou dobu.
- Asynchronii Když se jeden nebo víc výpočtů může spouštět odděleně od hlavního toku programu.

Všechny tři jsou kolmé koncepty, ale dají se snadno využít, zejména při jejich použití dohromady. Například může být nutné spustit více asynchronních výpočtů paralelně. To neznamená, že paralelismus nebo asynchronii implikuje jednu jinou.

Pokud je třeba vzít v úvahu etymology slova "Asynchronous", jsou zapojeny dvě části:

- "a", což znamená "NOT".
- "synchronní", význam "ve stejnou dobu".

Když tyto dvě výrazy zadáte společně, uvidíte, že "asynchronní" znamená ve stejnou dobu. A to je vše! V této definici neexistuje žádná nenásobení souběžnosti ani paralelismus. To platí také v praxi.

V praktických případech jsou asynchronní výpočty v F# nástroji naplánované k provádění nezávisle na hlavním toku programu. To neznamená souběžnost ani paralelismus, ani neznamená, že na pozadí se vždy stane výpočet. V závislosti na povaze výpočtu a prostředí, ve kterém je výpočet prováděn, se asynchronní výpočty mohou dokonce provádět synchronně.

Hlavní poznatkem byste měli mít za to, že asynchronní výpočty jsou nezávislé na toku hlavního programu. I když je k dispozici několik záruk, kdy nebo jak se provádí asynchronní výpočty, existují některé přístupy k orchestraci a jejich plánování. Zbývající část tohoto článku se zabývá základními koncepty pro F# asynchronii a používání typů, funkcí a výrazů integrovaných do F#.

## <a name="core-concepts"></a>Základní koncepty

V F#nástroji je asynchronní programování na střed kolem tří základních konceptů:

- Typ `Async<'T>`, který představuje sestavitelný asynchronní výpočet.
- Funkce modulu `Async`, které umožňují naplánovat asynchronní práci, vytváření asynchronních výpočtů a transformaci asynchronních výsledků.
- [Výraz výpočtu](../../language-reference/computation-expressions.md)`async { }`, který poskytuje pohodlný Syntax pro sestavování a řízení asynchronních výpočtů.

V následujícím příkladu vidíte tyto tři koncepty:

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

V tomto příkladu je funkce `printTotalFileBytes` typu `string -> Async<unit>`. Volání funkce ve skutečnosti neprovede asynchronní výpočet. Místo toho vrátí `Async<unit>`, který funguje jako * specifikace práce, která má být provedena asynchronně. Bude volat `Async.AwaitTask` v jeho těle, který převede výsledek <xref:System.IO.File.WriteAllBytesAsync%2A> na odpovídající typ při jeho volání.

Další důležitou linkou je volání `Async.RunSynchronously`. Jedná se o jednu z asynchronních funkcí modulu, které je třeba volat, pokud chcete skutečně provést F# asynchronní výpočet.

Toto je zásadní rozdíl se stylem C#/VB `async` programování. V F#asynchronních výpočtech se můžete představit jako **studené úlohy**. Je nutné je explicitně spustit ke skutečnému provedení. To má několik výhod, protože umožňuje kombinovat a sekvencovat asynchronní práci mnohem jednodušší než v C#/VB.

## <a name="combining-asynchronous-computations"></a>Kombinování asynchronních výpočtů

Tady je příklad, který sestaví na předchozím základě kombinováním výpočtů:

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

Jak vidíte, funkce `main` obsahuje ještě několik dalších volání. V koncepčním případě provede následující:

1. Transformujte argumenty příkazového řádku na `Async<unit>` výpočtů pomocí `Array.map`.
2. Vytvořte `Async<'T[]>`, který plánuje a spouští `printTotalFileBytes` výpočty paralelně při spuštění.
3. Vytvořte `Async<unit>`, který spustí paralelní výpočet a ignoruje jeho výsledek.
4. Explicitně spusťte poslední výpočet pomocí `Async.RunSynchronously` a zablokujte ho, dokud se nedokončí.

Když se tento program spustí, `printTotalFileBytes` běží paralelně pro každý argument příkazového řádku. Vzhledem k tomu, že asynchronní výpočty provádějí nezávisle na programu flow, neexistuje žádné pořadí, ve kterém tisknou své informace a dokončí provádění. Výpočty budou naplánovány paralelně, ale jejich pořadí provádění není zaručeno.

## <a name="sequencing-asynchronous-computations"></a>Sekvence asynchronních výpočtů

Vzhledem k tomu, že `Async<'T>` je specifikace práce, nikoli už spuštěná úloha, můžete snadno provádět komplikovanější transformace. Tady je příklad, který sekvencí sadu asynchronních výpočtů, aby se prováděly po druhém.

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

Tím se naplánuje `printTotalFileBytes` provést v pořadí prvků `argv` místo jejich souběžného naplánování. Vzhledem k tomu, že se další položka nebude naplánovat až po dokončení posledního výpočtu, jsou výpočty sekvencované tak, že při jejich provádění nedojde k překrytí.

## <a name="important-async-module-functions"></a>Důležité funkce asynchronního modulu

Při psaní asynchronního kódu v F# , obvykle budete pracovat s architekturou, která zpracovává plánování výpočtů za vás. Nejedná se však vždy o případ, takže je dobré zjistit různé počáteční funkce pro plánování asynchronní práce.

Vzhledem F# k tomu, že asynchronní výpočty jsou _specifikace_ práce, nikoli reprezentace práce, která je již spuštěna, musí být explicitně spuštěny pomocí počáteční funkce. Existuje mnoho [asynchronních spouštěcích funkcí](https://msdn.microsoft.com/library/ee370232.aspx) , které jsou užitečné v různých kontextech. V následující části jsou popsány některé nejběžnější funkce spouštění.

### <a name="asyncstartchild"></a>Async. StartChild –

Spustí podřízený výpočet v rámci asynchronního výpočtu. To umožňuje spustit více asynchronních výpočtů současně. Podřízený výpočet sdílí token zrušení s nadřazeným výpočtem. Pokud je nadřazený výpočet zrušen, je také zrušen podřízený výpočet.

Podpis:

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

Ideální v těchto situacích:

- Pokud chcete spustit více asynchronních výpočtů současně, nikoli v jednom okamžiku, ale nemusíte je naplánovat paralelně.
- Pokud chcete vytvořit propojení životnosti podřízeného výpočtu s nadřazeným výpočtem.

Co je potřeba sledovat:

- Spuštění více výpočtů s `Async.StartChild` není stejné jako při jejich plánování paralelně. Pokud chcete naplánovat souběžné výpočty, použijte `Async.Parallel`.
- Zrušením nadřazeného výpočtu se spustí zrušení všech podřízených výpočtů, které začaly.

### <a name="asyncstartimmediate"></a>Async. StartImmediate –

Spustí asynchronní výpočet počínaje okamžitě na aktuálním vlákně operačního systému. To je užitečné, pokud potřebujete během výpočtu aktualizovat něco v volajícím vlákně. Například pokud asynchronní výpočet musí aktualizovat uživatelské rozhraní (například aktualizace indikátoru průběhu), je třeba použít `Async.StartImmediate`.

Podpis:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Ideální v těchto situacích:

- Pokud potřebujete něco aktualizovat v volajícím vlákně uprostřed asynchronního výpočtu.

Co je potřeba sledovat:

- Kód v asynchronním výpočtu se spustí na jakémkoli vlákně, na kterém je naplánováno. To může být problematické, pokud je toto vlákno v nějakých citlivých případech, jako je například vlákno uživatelského rozhraní. V takových případech je `Async.StartImmediate` nejspíš nevhodné použít.

### <a name="asyncstartastask"></a>Async. Startastask –

Spustí výpočet ve fondu vláken. Vrátí <xref:System.Threading.Tasks.Task%601>, který bude dokončen v odpovídajícím stavu po ukončení výpočtu (vytvoří výsledek, vyvolá výjimku nebo se zruší). Pokud není k dispozici žádný token zrušení, použije se výchozí token zrušení.

Podpis:

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

Ideální v těchto situacích:

- Pokud potřebujete zavolat do rozhraní .NET API, které očekává <xref:System.Threading.Tasks.Task%601> pro reprezentaci výsledku asynchronního výpočtu.

Co je potřeba sledovat:

- Toto volání přidělí další objekt `Task`, což může zvýšit režii v případě, že se často používá.

### <a name="asyncparallel"></a>Async. Parallel

Plánuje sekvenci asynchronních výpočtů, které se mají spustit paralelně. Stupeň paralelismu lze volitelně vyladit/omezit zadáním parametru `maxDegreesOfParallelism`.

Podpis:

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Kdy ji použít:

- Pokud potřebujete spustit sadu výpočetních prostředků současně a nemusíte přitom spoléhat na jejich pořadí spouštění.
- Pokud nepotřebujete výsledky z plánovaných výpočtů paralelně, dokud nebudou dokončeny všechny.

Co je potřeba sledovat:

- Po dokončení všech výpočtů máte přístup pouze k výslednému poli hodnot.
- Výpočty se budou spouštět, ale skončí naplánovaných. To znamená, že nemůžete spoléhat na jejich pořadí provádění.

### <a name="asyncsequential"></a>Async. sekvenční

Naplánuje sekvenci asynchronních výpočtů, které se mají provést v pořadí, v jakém jsou předány. První výpočet se spustí, potom klikněte na další atd. Žádné výpočty se nespustí paralelně.

Podpis:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Kdy ji použít:

- Pokud potřebujete spustit více výpočtů v daném pořadí.

Co je potřeba sledovat:

- Po dokončení všech výpočtů máte přístup pouze k výslednému poli hodnot.
- Výpočty se spustí v pořadí, v jakém jsou předány této funkci, což může znamenat, že uplyne další doba před vrácením výsledků.

### <a name="asyncawaittask"></a>Async. Awaittask –

Vrátí asynchronní výpočet, který čeká na dokončení daného <xref:System.Threading.Tasks.Task%601> a vrátí jeho výsledek jako `Async<'T>`.

Podpis:

```fsharp
task: Task<'T>  -> Async<'T>
```

Ideální v těchto situacích:

- Když spotřebováváte rozhraní .NET API, které vrací <xref:System.Threading.Tasks.Task%601> v rámci F# asynchronního výpočtu.

Co je potřeba sledovat:

- Výjimky jsou zabaleny v <xref:System.AggregateException> následující po konvenci paralelní knihovny Tasks, a to se liší od F# toho, jak obvykle výjimky asynchronních povrchů.

### <a name="asynccatch"></a>Async. catch

Vytvoří asynchronní výpočet, který spustí daný `Async<'T>`a vrátí `Async<Choice<'T, exn>>`. Pokud se daná `Async<'T>` úspěšně dokončí, vrátí se výsledná hodnota `Choice1Of2`. Pokud je výjimka vyvolána před dokončením, je vrácena `Choice2of2` s vyvolanou výjimkou. Pokud se používá v asynchronním výpočtu, který je sám složený z mnoha výpočtů, a jeden z těchto výpočtů vyvolá výjimku, Výpočet zahrnuje také úplné zastavení.

Podpis:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Ideální v těchto situacích:

- Při provádění asynchronní práce, která může selhat s výjimkou a chcete tuto výjimku zpracovat v volajícím.

Co je potřeba sledovat:

- Pokud používáte kombinované nebo sekvencované asynchronní výpočty, výpočet zahrnující výpočty se úplně zastaví, pokud jeden z jeho "interních" výpočtů vyvolá výjimku.

### <a name="asyncignore"></a>Async. Ignore

Vytvoří asynchronní výpočet, který spustí daný výpočet a ignoruje jeho výsledek.

Podpis:

```fsharp
computation: Async<'T> -> Async<unit>
```

Ideální v těchto situacích:

- Pokud máte asynchronní výpočet, jehož výsledek není potřeba. To se podobá kódu `ignore` pro neasynchronní kód.

Co je potřeba sledovat:

- Pokud je nutné použít tuto funkci, protože chcete použít `Async.Start` nebo jinou funkci, která vyžaduje `Async<unit>`, zvažte, zda je zahození výsledku v pořádku. Vypuštění výsledků, které se nehodí pro podpis typu, by nemělo být obecně provedeno.

### <a name="asyncrunsynchronously"></a>Async. metodu RunSynchronously nelze

Spustí asynchronní výpočet a počká na jeho výsledek na volajícím vlákně. Toto volání je blokováno.

Podpis:

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

Kdy ji použít:

- Pokud ho potřebujete, používejte ho jenom jednou v aplikaci – v vstupním bodě pro spustitelný soubor.
- Pokud nezáleží na výkonu a chcete spustit sadu dalších asynchronních operací najednou.

Co je potřeba sledovat:

- Volání `Async.RunSynchronously` blokuje volající vlákno, dokud se spuštění nedokončí.

### <a name="asyncstart"></a>Async. Start

Spustí asynchronní výpočet ve fondu vláken, který vrací `unit`. Nečeká na výsledek. Vnořené výpočty zahájené s `Async.Start` jsou zcela spouštěny nezávisle na nadřazeném výpočtu, který je volal. Jejich životnost není svázána s žádným nadřazeným výpočtem. Pokud je nadřazený výpočet zrušený, žádné podřízené výpočty se neruší.

Podpis:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Použijte pouze v těchto případech:

- Máte asynchronní výpočet, který nepřinese výsledek nebo vyžaduje zpracování jednoho.
- Po dokončení asynchronního výpočtu nemusíte znát.
- Nezáleží na tom, na kterém vlákně běží asynchronní výpočty.
- Nemusíte znát ani podávat informace o výjimkách vyplývajících z úkolu.

Co je potřeba sledovat:

- Výjimky vyvolané výpočty zahájenými pomocí `Async.Start` nejsou šířeny volajícímu. Zásobník volání bude zcela zrušeno.
- Všechny ovlivněné práce (například volání `printfn`) spuštěné s `Async.Start` nezpůsobí, že se projeví v hlavním vlákně provádění programu.

## <a name="interoperating-with-net"></a>Spolupráce s .NET

Možná pracujete s knihovnou .NET nebo C# základem kódu, který používá asynchronní programování typu [Async/await](../../../standard/async.md). Vzhledem C# k tomu, že většina knihoven .net používá <xref:System.Threading.Tasks.Task%601> a <xref:System.Threading.Tasks.Task> typy jako základní abstrakce namísto `Async<'T>`, je nutné překročit hranici mezi těmito dvěma přístupy do asynchronii.

### <a name="how-to-work-with-net-async-and-taskt"></a>Jak pracovat s .NET Async a `Task<T>`

Práce s asynchronními knihovnami a základem kódu .NET, které používají <xref:System.Threading.Tasks.Task%601> (tj. asynchronní výpočty, které mají návratové hodnoty), jsou jednoduché a mají F#integrovanou podporu s.

Můžete použít funkci `Async.AwaitTask` pro čekání na asynchronní výpočet rozhraní .NET:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Můžete použít funkci `Async.StartAsTask` k předání asynchronního výpočtu volajícímu .NET:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Jak pracovat s .NET Async a `Task`

Chcete-li pracovat s rozhraními API, která používají <xref:System.Threading.Tasks.Task> (tj. asynchronní výpočty .NET, které nevracejí hodnotu), bude pravděpodobně nutné přidat další funkci, která převede `Async<'T>` na <xref:System.Threading.Tasks.Task>:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Již existuje `Async.AwaitTask`, který jako vstup přijímá <xref:System.Threading.Tasks.Task>. S tímto a dříve definovanou funkcí `startTaskFromAsyncUnit` můžete začít a očekávat <xref:System.Threading.Tasks.Task> typy z F# asynchronního výpočtu.

## <a name="relationship-to-multithreading"></a>Vztah k multithreadingu

I když je vlákno v rámci tohoto článku zmíněno, je třeba pamatovat si dva důležité věci:

1. Neexistuje žádné spřažení mezi asynchronním výpočtem a vláknem, pokud není explicitně spuštěno v aktuálním vlákně.
1. Asynchronní programování v F# není abstrakce pro multithreading.

Například výpočet může být v závislosti na povaze práce spuštěn ve vlastním vlákně volajícího. Výpočet může také "Přejít" mezi vlákny a jejich vypůjčení po krátkou dobu, aby bylo možné provádět užitečnou práci v obdobích "čekání" (například při přenosu síťového hovoru).

I F# když poskytuje některé možnosti, jak spustit asynchronní výpočet v aktuálním vlákně (nebo explicitně ne na aktuálním vlákně), asynchronii obecně není přidružená k určité strategii vláken.

## <a name="see-also"></a>Viz také:

- [F# Asynchronní programovací model](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [F# Asynchronní Průvodce jet. com](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F#Průvodce asynchronním programováním pro zábavu a zisk](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Asynchronní v C# a F#: asynchronní možná úskalí vC#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
