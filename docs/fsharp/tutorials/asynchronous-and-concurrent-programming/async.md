---
title: Asynchronní programování
description: 'Přečtěte si, jak F # poskytuje čistou podporu pro asynchronii na základě programovacího modelu na úrovni jazyka odvozeného od základních konceptů programování funkcí.'
ms.date: 08/15/2020
ms.openlocfilehash: 2e5d4fb744b4443eb9caf90cc1bf01473b809127
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811766"
---
# <a name="async-programming-in-f"></a>Asynchronní programování v F\#

Asynchronní programování je mechanismus, který je nezbytný pro moderní aplikace z nejrůznějších důvodů. K dispozici jsou dva primární případy použití, ke kterým dojde ve většině vývojářů:

- Prezentující proces serveru, který může obsluhovat velký počet souběžných příchozích požadavků a současně minimalizuje systémové prostředky, které při zpracování požadavků čekají na vstupy ze systémů nebo služeb, které jsou pro tento proces externí.
- Údržba s reagujícím uživatelským rozhraním nebo hlavním vláknem při současném průběhu práce na pozadí

I když práce na pozadí často zahrnuje využití více vláken, je důležité vzít v úvahu koncepty asynchronii a multithreading samostatně. Ve skutečnosti se jedná o samostatné obavy a jedna z nich neznamená jinou. Tento článek popisuje samostatné koncepce podrobněji.

## <a name="asynchrony-defined"></a>Asynchronii – definováno

Předchozí bod – tento asynchronii je nezávislý na využití více vláken – je vysvětlovat trochu dál. Existují tři koncepty, které jsou někdy související, ale výhradně nezávisle na sobě.

- Concurrency Když je v překrývajících se časových obdobích prováděno více výpočtů.
- Paralelismu v případě, že se více výpočetních nebo několika částí jednoho výpočtu spouští přesně ve stejnou dobu.
- Asynchronii Když se jeden nebo víc výpočtů může spouštět odděleně od hlavního toku programu.

Všechny tři jsou kolmé koncepty, ale dají se snadno využít, zejména při jejich použití dohromady. Například může být nutné spustit více asynchronních výpočtů paralelně. Tato relace neznamená, že paralelismus nebo asynchronii implikuje jednu jinou.

Pokud je třeba vzít v úvahu etymology slova "Asynchronous", jsou zapojeny dvě části:

- "a", což znamená "NOT".
- "synchronní", význam "ve stejnou dobu".

Když tyto dvě výrazy zadáte společně, uvidíte, že "asynchronní" znamená ve stejnou dobu. A to je vše! V této definici neexistuje žádná nenásobení souběžnosti ani paralelismus. To platí také v praxi.

V praktických případech jsou asynchronní výpočty v F # spouštěny nezávisle na hlavním toku programu. Toto nezávislé provádění neznamená souběžnost ani paralelismus, ani neznamená, že na pozadí se vždy stane výpočet. V závislosti na povaze výpočtu a prostředí, ve kterém je výpočet prováděn, se asynchronní výpočty mohou dokonce provádět synchronně.

Hlavní poznatkem byste měli mít za to, že asynchronní výpočty jsou nezávislé na toku hlavního programu. I když je k dispozici několik záruk, kdy nebo jak se provádí asynchronní výpočty, existují některé přístupy k orchestraci a jejich plánování. Zbývající část tohoto článku se zabývá základními koncepty jazyka F # asynchronii a způsobu použití typů, funkcí a výrazů integrovaných do jazyka F #.

## <a name="core-concepts"></a>Základní koncepty

V jazyce F # je asynchronní programování na střed kolem tří základních konceptů:

- `Async<'T>`Typ, který představuje sestavitelný asynchronní výpočet.
- `Async`Funkce modulu, které umožňují naplánovat asynchronní práci, psaní asynchronních výpočtů a transformaci asynchronních výsledků.
- `async { }` [Výraz výpočtu](../../language-reference/computation-expressions.md), který poskytuje pohodlný Syntax pro sestavování a řízení asynchronních výpočtů.

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

V tomto příkladu `printTotalFileBytes` je funkce typu `string -> Async<unit>` . Volání funkce ve skutečnosti neprovede asynchronní výpočet. Místo toho vrátí objekt `Async<unit>` , který funguje jako *specifikace* práce, která má být provedena asynchronně. Volá `Async.AwaitTask` svůj text, který převede výsledek <xref:System.IO.File.ReadAllBytesAsync%2A> na příslušný typ.

Dalším důležitým řádkem je volání `Async.RunSynchronously` . Jedná se o jednu z asynchronních funkcí modulu, které je třeba volat, pokud chcete skutečně provést asynchronní výpočet F #.

Jedná se o zásadní rozdíl s jazykem C# webový Basic `async` Programming. V F # lze asynchronní výpočty představit jako **studené úlohy**. Je nutné je explicitně spustit ke skutečnému provedení. To má několik výhod, protože umožňuje kombinovat a sekvencovat asynchronní práci mnohem jednodušší než v jazyce C# nebo Visual Basic.

## <a name="combine-asynchronous-computations"></a>Kombinování asynchronních výpočtů

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

Jak vidíte, `main` funkce má poměrně několik dalších volání. V koncepčním případě provede následující:

1. Transformujte argumenty příkazového řádku do `Async<unit>` výpočtů pomocí `Array.map` .
2. Vytvořte `Async<'T[]>` tyto plány a `printTotalFileBytes` při spuštění spustí výpočty paralelně.
3. Vytvořte `Async<unit>` , který spustí paralelní výpočet a ignoruje jeho výsledek.
4. Explicitně spusťte poslední výpočet s `Async.RunSynchronously` a zablokujte, dokud se nedokončí.

Při spuštění tohoto programu `printTotalFileBytes` běží paralelně pro každý argument příkazového řádku. Vzhledem k tomu, že asynchronní výpočty provádějí nezávisle na programu flow, neexistuje žádné pořadí, ve kterém tisknou své informace a dokončí provádění. Výpočty budou naplánovány paralelně, ale jejich pořadí provádění není zaručeno.

## <a name="sequence-asynchronous-computations"></a>Sekvence asynchronních výpočtů

Vzhledem k tomu `Async<'T>` , že je specifikace práce spíše než již spuštěná úloha, můžete snadno provádět komplikovanější transformace. Tady je příklad, který sekvencí sadu asynchronních výpočtů, aby se prováděly po druhém.

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

Tím se naplánuje `printTotalFileBytes` spuštění v pořadí prvků `argv` místo jejich souběžného plánování. Vzhledem k tomu, že se další položka nebude naplánovat až po dokončení posledního výpočtu, jsou výpočty sekvencované tak, že při jejich provádění nedojde k překrytí.

## <a name="important-async-module-functions"></a>Důležité funkce asynchronního modulu

Při psaní asynchronního kódu v jazyce F # obvykle budete pracovat s architekturou, která zpracovává plánování výpočtů za vás. Nejedná se však vždy o případ, takže je dobré zjistit různé počáteční funkce pro plánování asynchronní práce.

Vzhledem k tomu, že asynchronní výpočty F # jsou _specifikací_ práce, nikoli reprezentace práce, která je již spuštěna, musí být explicitně spuštěny pomocí funkce Start. Existuje mnoho [asynchronních počátečních metod](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) , které jsou užitečné v různých kontextech. V následující části jsou popsány některé nejběžnější funkce spouštění.

### <a name="asyncstartchild"></a>Async. StartChild –

Spustí podřízený výpočet v rámci asynchronního výpočtu. To umožňuje spustit více asynchronních výpočtů současně. Podřízený výpočet sdílí token zrušení s nadřazeným výpočtem. Pokud je nadřazený výpočet zrušen, je také zrušen podřízený výpočet.

Podpis:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

Kdy použít:

- Pokud chcete spustit více asynchronních výpočtů současně, nikoli v jednom okamžiku, ale nemusíte je naplánovat paralelně.
- Pokud chcete vytvořit propojení životnosti podřízeného výpočtu s nadřazeným výpočtem.

Co je potřeba sledovat:

- Spuštění více výpočetních prostředků se `Async.StartChild` neshoduje s plánováním paralelně. Pokud chcete naplánovat souběžné výpočty, použijte `Async.Parallel` .
- Zrušením nadřazeného výpočtu se spustí zrušení všech podřízených výpočtů, které začaly.

### <a name="asyncstartimmediate"></a>Async. StartImmediate –

Spustí asynchronní výpočet, který se spouští okamžitě na aktuálním vlákně operačního systému. To je užitečné, pokud potřebujete během výpočtu aktualizovat něco v volajícím vlákně. Například pokud asynchronní výpočet musí aktualizovat uživatelské rozhraní (například aktualizace indikátoru průběhu), pak `Async.StartImmediate` by se měla použít.

Podpis:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Kdy použít:

- Pokud potřebujete něco aktualizovat v volajícím vlákně uprostřed asynchronního výpočtu.

Co je potřeba sledovat:

- Kód v asynchronním výpočtu se spustí na jakémkoli vlákně, na kterém je naplánováno. To může být problematické, pokud je toto vlákno v nějakých citlivých případech, jako je například vlákno uživatelského rozhraní. V takových případech `Async.StartImmediate` je nejspíš nevhodné použít.

### <a name="asyncstartastask"></a>Async. Startastask –

Provede výpočet ve fondu vláken. Vrátí <xref:System.Threading.Tasks.Task%601> , který bude dokončen v odpovídajícím stavu po ukončení výpočtu (vytvoří výsledek, vyvolá výjimku nebo se zruší). Pokud není k dispozici žádný token zrušení, použije se výchozí token zrušení.

Podpis:

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

Kdy použít:

- Pokud potřebujete volat rozhraní .NET API, které očekává, že <xref:System.Threading.Tasks.Task%601> má představovat výsledek asynchronního výpočtu.

Co je potřeba sledovat:

- Toto volání přidělí další `Task` objekt, který může zvýšit režii v případě, že se používá často.

### <a name="asyncparallel"></a>Async. Parallel

Plánuje sekvenci asynchronních výpočtů, které se mají spustit paralelně. Stupeň paralelismu lze volitelně vyladit/omezit zadáním `maxDegreesOfParallelism` parametru.

Podpis:

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Kdy ji použít:

- Pokud potřebujete spustit sadu výpočetních prostředků současně a nemusíte přitom spoléhat na jejich pořadí spouštění.
- Pokud nepotřebujete výsledky z plánovaných výpočtů paralelně, dokud nebudou dokončeny všechny.

Co je potřeba sledovat:

- Po dokončení všech výpočtů máte přístup pouze k výslednému poli hodnot.
- Výpočty se spustí pokaždé, když skončí naplánování. Toto chování znamená, že nemůžete spoléhat na jejich pořadí provádění.

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

Vrátí asynchronní výpočet, který čeká na <xref:System.Threading.Tasks.Task%601> dokončení daného a vrátí výsledek jako `Async<'T>`

Podpis:

```fsharp
task: Task<'T> -> Async<'T>
```

Kdy použít:

- Když spotřebováváte rozhraní .NET API, které vrací <xref:System.Threading.Tasks.Task%601> v rámci asynchronního výpočtu F #.

Co je potřeba sledovat:

- Výjimky jsou zabaleny podle <xref:System.AggregateException> konvence paralelní knihovny Task a toto chování se liší od obecně nezávisle na výjimkách F #.

### <a name="asynccatch"></a>Async. catch

Vytvoří asynchronní výpočet, který spustí daný `Async<'T>` příkaz a vrátí `Async<Choice<'T, exn>>` . Pokud se `Async<'T>` úspěšně dokončí, vrátí se `Choice1Of2` Výsledná hodnota. Pokud je vyvolána výjimka před dokončením, `Choice2of2` je vrácena vyvolána výjimka. Pokud se používá v asynchronním výpočtu, který je sám složený z mnoha výpočtů, a jeden z těchto výpočtů vyvolá výjimku, Výpočet zahrnuje také úplné zastavení.

Podpis:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Kdy použít:

- Při provádění asynchronní práce, která může selhat s výjimkou a chcete tuto výjimku zpracovat v volajícím.

Co je potřeba sledovat:

- Pokud používáte kombinované nebo sekvencované asynchronní výpočty, výpočet zahrnující výpočty se úplně zastaví, pokud jeden z jeho "interních" výpočtů vyvolá výjimku.

### <a name="asyncignore"></a>Async. Ignore

Vytvoří asynchronní výpočet, který spustí daný výpočet a ignoruje jeho výsledek.

Podpis:

```fsharp
computation: Async<'T> -> Async<unit>
```

Kdy použít:

- Pokud máte asynchronní výpočet, jehož výsledek není potřeba. To je analogické `ignore` kódu pro neasynchronní kód.

Co je potřeba sledovat:

- Pokud je potřeba použít `Async.Ignore` , protože chcete použít `Async.Start` nebo jinou funkci, která vyžaduje `Async<unit>` , zvažte, jestli je výsledek zahození. Vyhněte se zahození výsledků pouze k přizpůsobení signatury typu.

### <a name="asyncrunsynchronously"></a>Async. metodu RunSynchronously nelze

Spustí asynchronní výpočet a počká na jeho výsledek na volajícím vlákně. Toto volání je blokováno.

Podpis:

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

Kdy ji použít:

- Pokud ho potřebujete, používejte ho jenom jednou v aplikaci – v vstupním bodě pro spustitelný soubor.
- Pokud nezáleží na výkonu a chcete spustit sadu dalších asynchronních operací najednou.

Co je potřeba sledovat:

- Volání `Async.RunSynchronously` blokuje volající vlákno, dokud se spuštění nedokončí.

### <a name="asyncstart"></a>Async. Start

Spustí asynchronní výpočet ve fondu vláken, který vrací `unit` . Nečeká na výsledek. Vnořené výpočty spuštěné s `Async.Start` jsou spouštěny nezávisle na nadřazeném výpočtu, který je volal. Jejich životnost není svázána s žádným nadřazeným výpočtem. Pokud je nadřazená výpočetní operace zrušena, nejsou zrušeny žádné podřízené výpočty.

Podpis:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Použijte pouze v těchto případech:

- Máte asynchronní výpočet, který nepřinese výsledek nebo vyžaduje zpracování jednoho.
- Po dokončení asynchronního výpočtu nemusíte znát.
- Nezáleží na tom, na kterém vlákně běží asynchronní výpočty.
- Nemusíte znát ani podávat informace o výjimkách vyplývajících z úkolu.

Co je potřeba sledovat:

- Výjimky vyvolané výpočty se `Async.Start` nešíří pro volajícího. Zásobník volání bude zcela zrušeno.
- Jakákoli práce (například volání `printfn` ) začala `Async.Start` nezpůsobí, že se projeví v hlavním vlákně provádění programu.

## <a name="interoperate-with-net"></a>Spolupráce s .NET

Možná pracujete s knihovnou .NET nebo základem kódu jazyka C#, který používá asynchronní programování typu [Async/await](../../../standard/async.md). Vzhledem k tomu, že jazyk C# a většina knihoven .NET používají <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> jako základní abstrakce typy a a nikoli `Async<'T>` , je nutné příčně překročit hranici mezi těmito dvěma přístupy na asynchronii.

### <a name="how-to-work-with-net-async-and-taskt"></a>Jak pracovat s .NET Async a `Task<T>`

Práce s asynchronními knihovnami .NET a základy kódu, které používají <xref:System.Threading.Tasks.Task%601> (asynchronní výpočty, které mají návratové hodnoty), jsou jednoduché a mají integrovanou podporu F #.

Funkci lze použít `Async.AwaitTask` k očekávání asynchronního výpočtu rozhraní .NET:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Funkci lze použít `Async.StartAsTask` k předání asynchronního výpočtu volajícímu .NET:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Jak pracovat s .NET Async a `Task`

Chcete-li pracovat s rozhraními API, která používají <xref:System.Threading.Tasks.Task> (to znamená asynchronní výpočty rozhraní .NET, které nevracejí hodnotu), bude pravděpodobně nutné přidat další funkci, která převede `Async<'T>` na <xref:System.Threading.Tasks.Task> :

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Už existuje `Async.AwaitTask` , který přijímá <xref:System.Threading.Tasks.Task> jako vstup. S touto a dříve definovanou `startTaskFromAsyncUnit` funkcí můžete začít a očekávat <xref:System.Threading.Tasks.Task> typy z asynchronního výpočtu F #.

## <a name="relationship-to-multi-threading"></a>Vztah k více vláknům

I když je vlákno v rámci tohoto článku zmíněno, je třeba pamatovat si dva důležité věci:

1. Neexistuje žádné spřažení mezi asynchronním výpočtem a vláknem, pokud není explicitně spuštěno v aktuálním vlákně.
1. Asynchronní programování v jazyce F # není abstrakcí pro multithreading.

Například výpočet může být v závislosti na povaze práce spuštěn ve vlastním vlákně volajícího. Výpočet může také "Přejít" mezi vlákny a jejich vypůjčení po krátkou dobu, aby bylo možné provádět užitečnou práci v obdobích "čekání" (například při přenosu síťového hovoru).

Přestože jazyk F # poskytuje některé možnosti, jak spustit asynchronní výpočet v aktuálním vlákně (nebo explicitně ne na aktuálním vlákně), asynchronii obecně není přidružena k určité strategii vláken.

## <a name="see-also"></a>Viz také

- [Asynchronní programovací model F #](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Asynchronní Průvodce F # v jet. com](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [Průvodce asynchronním programováním v F # pro zábavu a zisk](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Asynchronní v jazycích C# a F #: asynchronní možná úskalí v jazyce C #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
