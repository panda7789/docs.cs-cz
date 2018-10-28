---
title: 'Asynchronní programování v jazyce F #'
description: Zjistěte, jak F# asynchronního programování se provádí prostřednictvím programovací model na úrovni jazyka, který se snadno používá a je přirozený jazyk.
ms.date: 06/20/2016
ms.openlocfilehash: de07f1252df56e3dfec5ea7a34a283b1c9508523
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195057"
---
# <a name="async-programming-in-f"></a>Asynchronní programování v jazyce F # #

> [!NOTE]
> Některé nepřesnosti byly zjištěny v tomto článku.  Je právě přepsán.  Zobrazit [problém #666](https://github.com/dotnet/docs/issues/666) Další informace o změnách.

Asynchronní programování v F# je možné provádět prostřednictvím úrovni jazyka programovací model navržené tak, aby se snadno používá a přirozený jazyk.

Základní asynchronní programování v F# je `Async<'T>`, reprezentace práci, která se dá spouštět na spuštěný na pozadí, kde `'T` se vrátí buď typ prostřednictvím speciální `return` – klíčové slovo nebo `unit` Pokud asynchronního pracovního postupu nemá žádný výsledek určený k vrácení.

Klíčovým konceptem pochopit je, že je typ výrazu asynchronní `Async<'T>`, což je pouze na _specifikace_ práce udělat v asynchronním kontextu. Není spuštěn, dokud ho explicitně spustit s jednou počáteční funkcí (jako například `Async.RunSynchronously`). Přestože je toto různých způsobu přemýšlení o tom, jak pracovní, ukončí nebuďte úplně jednoduché v praxi.

Řekněme například, že chcete stáhnout kód HTML z dotnetfoundation.org bez blokování hlavního vlákna. Můžete provést to takto:

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

A to je všechno! Kromě použití `async`, `let!`, a `return`, to je jenom normální F# kódu.

Existuje několik syntaktické konstrukce, které stojí za zmínku:

*   `let!` vytvoří vazbu výsledek výrazu asynchronní (který se spouští v jiném kontextu).
*   `use!` funguje stejně jako `let!`, ale uvolní prostředky jeho vazby, když dostane mimo rozsah.
*   `do!` počká na asynchronní pracovní postup, který nic nevrací.
*   `return` jednoduše vrací výsledek z asynchronní výraz.
*   `return!` spustí jiný pracovní postup asynchronního a vrátí jeho návratovou hodnotu ve výsledku.

Kromě toho normální `let`, `use`, a `do` klíčová slova můžete používat společně se asynchronní verze, stejně jako normální funkce.

## <a name="how-to-start-async-code-in-f"></a>Jak můžete začít asynchronní kódF# #

Jak už bylo zmíněno dříve, asynchronní kód je specifikace práce udělat v jiném kontextu, který musí být explicitně spuštěna. Tady jsou dva základní způsoby, jak toho dosáhnout:

1.  `Async.RunSynchronously` Asynchronní pracovní postup spustit v jiném vlákně, který se await jeho výsledek.

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  `Async.Start` Asynchronní pracovní postup spustit v jiném vlákně a bude **není** await jeho výsledek.

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

Existují jiné způsoby, jak začít asynchronní workflowu, který je k dispozici pro konkrétnější scénáře. Jsou podrobně popsány [v odkazu asynchronní](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>Poznámka: na vláknech

Fráze "v jiném vlákně" je uvedeno výše, ale je důležité vědět, že **to neznamená, že asynchronní pracovní postupy jsou průčelím pro multithreading**. Pracovní postup ve skutečnosti "přejde" mezi vlákny vypůjčení pro malé množství času dělat užitečnou práci. Když pracovním postupu asynchronní efektivně "čeká" (např. čekání na síť volání vracely něco), žádné vlákno, byla půjčky v době je uvolněna až přejděte užitečnou práci na něco jiného. Tato možnost povoluje asynchronní pracovní postupy pro využití systému, ve kterém jsou spuštěné na co možná nejefektivněji a je mezi nimi vlastně hlavně silným pro scénáře vysoký počet vstupně-výstupních operací.

## <a name="how-to-add-parallelism-to-async-code"></a>Postup přidání paralelismu asynchronní kód

Někdy můžete potřebovat provádět více asynchronních úloh paralelně, shromažďovat jejich výsledky a interpretovat nějakým způsobem. `Async.Parallel` Umožňuje provést bez nutnosti použít Task Parallel Library, což by vyžadovalo museli vynucení `Task<'T>` a `Async<'T>` typy.

Následující příklad použije `Async.Parallel` si Pokud chcete stáhnout kód HTML z oblíbených lokalit čtyři paralelně, počkejte na dokončení těchto úloh a poté vytiskněte HTML, který byl stažen.

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a>Důležité informace a Rady

*   Připojte "Async" za účelem všechny funkce, které budete používat

 I když je to jenom zásady vytváření názvů, je usnadnit věci jako rozhraní API zjistitelnost. Zejména v případě, že existují synchronní a asynchronní verze stejné rutiny, je vhodné k výslovnému, což je asynchronní prostřednictvím názvu.

*   Naslouchání kompilátoru!

 F#pro kompilátor je velmi přísná, díky tomu je téměř nemožné něco jako je zneklidňují nové spuštění kódu "async" synchronně. Pokud narazíte na upozornění, který je znak, jak si myslíte, že bude kód nebude spuštěno. Pokud se vás kompilátor šťastný, váš kód spustí pravděpodobně podle očekávání.

## <a name="for-the-cvb-programmer-looking-into-f"></a>Pro C#podívat na programátorovi /VBF# #

V této části se předpokládá, seznamte se s asynchronní model v C#/VB. Pokud nemáte, [asynchronní programování v C# ](../../../csharp/async.md) je výchozím bodem.

Je zásadní rozdíl mezi C#/VB asynchronní model a F# asynchronní model.

Při volání funkce, která vrátí `Task` nebo `Task<'T>`, tato úloha už začala spuštění. Popisovač vrácený představuje asynchronní úlohu již spuštěná. Naproti tomu při volání asynchronní funkce F#, `Async<'a>` vrátil představuje úlohu, která bude **generované** v určitém okamžiku. Vysvětlení tohoto modelu je efektivní, protože to umožňuje asynchronní úlohy v F# se seskupují klidní, provádí podmíněně a pracovat s lepší intervalem ovládacího prvku.

Existuje několik dalších podobnosti a rozdíly za zmínku.

### <a name="similarities"></a>Podobnosti

*   `let!`, `use!`, a `do!` jsou podobná `await` při volání metody na asynchronní úlohy v rámci `async{ }` bloku.

 Tři klíčová slova jde použít jenom v rámci `async { }` bloku, podobný postup `await` lze vyvolat pouze uvnitř `async` metoda. Stručně řečeno `let!` je pro, pokud chcete zachytit a používat výsledku `use!` je stejný ale něco jehož prostředky by měl získat čištění po se používá, a `do!` je pro, pokud chcete čekat pro asynchronní pracovní postup s žádnou návratovou hodnotu pro dokončení než budete pokračovat.

*   F#Datový paralelismus podporuje podobným způsobem.

 I když to vše je přístupné nějak významně odlišně `Async.Parallel` odpovídá `Task.WhenAll` pro scénář záhlaví výsledky sadu asynchronních úloh po dokončení činnosti všech.

### <a name="differences"></a>Rozdíly

*   Vnořené `let!` není povolené, na rozdíl od vnořené `await`

 Na rozdíl od `await`, které mohou být vnořené po neomezenou dobu, `let!` nelze a musíte mít jeho výsledek vázán před jeho použitím do druhého `let!`, `do!`, nebo `use!`.

*   Podporu zrušení je jednodušší v F# než C#/VB.

 Podpora zrušení úlohy polovině během C#/VB vyžaduje kontrolu `IsCancellationRequested` vlastností nebo volání `ThrowIfCancellationRequested()` na `CancellationToken` objektu, který je předán do asynchronní metody.

Naproti tomu F# asynchronními pracovními postupy jsou přirozeněji zrušit. Zrušení je jednoduchý proces třech krocích.

1.  Vytvořte nový `CancellationTokenSource`.
2.  Předejte ho do výchozí funkce.
3.  Volání `Cancel` na tokenu.

Příklad:

```fsharp
open System
open System.Net
open System.Threading

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token.Token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

A to je všechno!

## <a name="further-resources"></a>Další materiály:

*   [Asynchronní pracovní postupy na webu MSDN](https://msdn.microsoft.com/library/dd233250.aspx)
*   [Asynchronní pořadí proF#](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F#Nástroje data protokolu HTTP](https://fsharp.github.io/FSharp.Data/library/Http.html)
