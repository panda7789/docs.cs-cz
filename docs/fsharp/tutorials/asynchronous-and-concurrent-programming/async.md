---
title: 'Asynchronní programování v F #'
description: 'Zjistěte, jak se provádí F # – programování asynchronních prostřednictvím úroveň jazyka programovací model, který je snadno použitelný a přirozený jazyk.'
keywords: Rozhraní .NET, .NET core
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: c3fde46e804b7acac78d3ce5454a3c6f806e24e7
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="async-programming-in-f"></a>Asynchronní programování v F # #

> [!NOTE]
> Některé nepřesnosti byly zjištěny v tomto článku.  Je se přepisuje.  V tématu [problém #666](https://github.com/dotnet/docs/issues/666) Další informace o změnách.

Asynchronní programování v F # lze provést prostřednictvím modelu programovací jazyk úrovni navržený tak, aby se snadno používá a přirozený jazyk.

Základní asynchronní programování v F # je `Async<'T>`, znázornění práce, které se aktivuje spuštění na pozadí, kde `'T` je buď typu vrácen prostřednictvím speciální `return` – klíčové slovo nebo `unit` pokud asynchronní pracovní postup neobsahuje žádné výsledek určený k vrácení.

Klíče koncept pochopit je, že je typ výraz asynchronní `Async<'T>`, která je jenom na _specifikace_ práce v asynchronním kontextu. Nebude provedena, dokud ji explicitně spustit s jedním z výchozí funkce (například `Async.RunSynchronously`). Přestože je toto jiný způsob přemýšlení o pracuje, ukončí až se v praxi poměrně jednoduché.

Řekněme například, že chcete stáhnout HTML z dotnetfoundation.org bez blokování hlavního vlákna. Můžete ji provést takto:

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

A je to! Kromě zajištění dostatečného použití `async`, `let!`, a `return`, jedná se jenom normální F # – kód.

Existuje několik syntaktické konstrukce, které jsou vhodné poznamenat:

*   `let!` vytvoří vazbu výsledek asynchronní výrazu (který se spouští v jiném kontextu).
*   `use!` funguje stejným způsobem jako `let!`, ale uvolní její vázané prostředky, když probíhá mimo rozsah.
*   `do!` počká asynchronní pracovního postupu, které nic nevrací.
*   `return` jednoduše vrací výsledek z výrazu asynchronní.
*   `return!` Spustí jiného pracovního postupu asynchronní a v důsledku vrátí hodnoty.

Kromě toho normální `let`, `use`, a `do` klíčová slova můžete používat společně se asynchronních verzích, stejně jako v normálním funkce.

## <a name="how-to-start-async-code-in-f"></a>Postup spuštění asynchronní kódu v jazyce F # #

Jak už bylo zmíněno dříve, je asynchronní kód specifikace pracovní provést v jiném kontextu, které musí být explicitně spuštěna. K tomu dva primární způsoby:

1.  `Async.RunSynchronously` bude na jiné vlákno spustit pracovní postup async a operátoru await její výsledek.

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

2.  `Async.Start` Asynchronní pracovní postup spustit na jiné vlákno a bude **není** await její výsledek.

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

Spuštění asynchronních workflow, který je k dispozici pro více konkrétních scénářů i jinými způsoby. Které jsou podrobně popsány [v referenci asynchronní](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>Poznámka: na vláken

Fráze "na jiné vlákno" uvedená výše, ale je důležité vědět, že **to neznamená, že asynchronní pracovní postupy jsou průčelí za pro multithreading**. Pracovní postup ve skutečnosti "skáče" mezi vlákny, úvěrové je pro malé množství času užitečné práci. Když pracovním postupu asynchronní efektivně "čeká" (například čekání na něco vrátit volání sítě), všechny vlákno, byla úvěrové v době uvolněno až přejděte užitečné práce na něco jiného. To umožňuje použít systém, který běží na co možná nejefektivněji asynchronní pracovní postupy a jsou pak zejména silné pro scénáře vysoký počet vstupně-výstupní operace.

## <a name="how-to-add-parallelism-to-async-code"></a>Postup přidání paralelismus asynchronní kódu

Někdy můžete potřebovat k provedení více asynchronních úloh paralelně, shromažďování jejich výsledky a je interpretovat nějakým způsobem. `Async.Parallel` Můžete to provést bez nutnosti použít Task Parallel Library, které by zahrnovat museli coerce `Task<'T>` a `Async<'T>` typy.

Následující příklad použije `Async.Parallel` Pokud chcete stáhnout HTML ze čtyř oblíbených lokalit paralelně, počkejte na dokončení těchto úloh a poté vytiskněte HTML, který byl stažen.

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

## <a name="important-info-and-advice"></a>Důležité informace a Rady, jak

*   Připojte "Asynchronní" konec všechny funkce, které budete používat

 I když je to právě zásady vytváření názvů, je snazší takové věci, jako možnosti rozpoznání rozhraní API. Zejména, pokud jsou synchronní a asynchronní verze stejné rutiny, je vhodné explicitně stavu, která je asynchronní prostřednictvím název.

*   Naslouchání kompilátoru!

 Pro kompilátor jazyka F # je velmi přísná, což téměř znemožní dělat něco troubling jako spustit "asynchronní" kód synchronně. Pokud narazíte na upozornění, která je znak, jak si myslíte, že se bude kód nebude spouštění. Pokud se vám kompilátor radostí, váš kód bude s největší pravděpodobností spustit podle očekávání.

## <a name="for-the-cvb-programmer-looking-into-f"></a>Pro programátory C# / VB. vyhledávání do F # #

V této části se předpokládá, když jste se seznámili s modelem asynchronní v jazyce C# nebo VB. Pokud nemáte, [asynchronní programování v jazyce C#](../../../csharp/async.md) je výchozím bodem.

Je zásadní rozdíl mezi C# / VB. asynchronní modelu a modelu asynchronní F #.

Při volání funkce, která vrátí hodnotu `Task` nebo `Task<'T>`, této úlohy je již spuštěno provádění. Vrátí popisovač představuje asynchronní úlohu již spuštěna. Naproti tomu při volání funkce asynchronní v F # `Async<'a>` vrátil představuje úlohu, u které bude **generované** v určitém okamžiku. Vysvětlení tohoto modelu je výkonný, protože umožňuje pro asynchronní úlohy v jazyce F # k zřetězen dohromady snadnější, provést podmíněně a spustit s jemnějšího intervalem ovládacího prvku.

Existuje několik podobnosti a rozdíly vhodné poznamenat.

### <a name="similarities"></a>Podobnosti

*   `let!`, `use!`, a `do!` se podobá `await` při volání metody úlohu asynchronní uvnitř `async{ }` bloku.

 Tři klíčová slova lze použít pouze v rámci `async { }` bloku, podobně jako postupy `await` jde volat jenom uvnitř `async` metoda. Stručně řečeno `let!` je pro, když chcete zaznamenat a použít výsledek, `use!` je něco jehož prostředky by měly získat čištění po se používají stejné ale a `do!` je pro, pokud chcete pro čekání asynchronní pracovní postup s žádnou návratovou hodnotu na dokončení než budete pokračovat.

*   F # podporuje datový paralelismus podobným způsobem.

 I když ho pracuje velmi odlišně `Async.Parallel` odpovídá `Task.WhenAll` pro scénáře podmínka mimo výsledky sadu asynchronních úloh po dokončení se všechny.

### <a name="differences"></a>Rozdíly

*   Vnořené `let!` není povolena, na rozdíl od vnořené `await`

 Na rozdíl od `await`, které mohou být použity po neomezenou dobu, `let!` nelze a musíte mít jeho výsledek vázaný před jeho použitím uvnitř jiného `let!`, `do!`, nebo `use!`.

*   Podpora zrušení je jednodušší v jazyce F # než v jazyce C# nebo VB.

 Podpora zrušení úloh polovině prostřednictvím jeho spuštění v C# / VB. vyžaduje kontrolu `IsCancellationRequested` vlastnost nebo volání `ThrowIfCancellationRequested()` na `CancellationToken` objekt, který je předán do asynchronní metody.

F # asynchronní pracovní postupy jsou naopak více přirozeně zrušit. Zrušení je jednoduchý proces třech krocích.

1.  Vytvořte novou `CancellationTokenSource`.
2.  Předejte ji do počáteční funkce.
3.  Volání `Cancel` na tokenu.

Příklad:

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

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

A je to!

## <a name="further-resources"></a>Další prostředky:

*   [Asynchronní pracovní postupy na webu MSDN](https://msdn.microsoft.com/library/dd233250.aspx)
*   [Asynchronní pořadí pro F #](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [Nástroje F # dat protokolu HTTP](https://fsharp.github.io/FSharp.Data/library/Http.html)
