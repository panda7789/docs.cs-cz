---
title: Úloha asynchronního programovacího modelu (klepnutím) s modifikátorem AsyncC#a await ()
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 644830ac62a4df23f22d8f91e9b3c768dd611451
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395692"
---
# <a name="task-asynchronous-programming-model"></a>Model asynchronního programování úloh

Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.

5 zavádí zjednodušený přístup, asynchronní programování, které využívá asynchronní podporu v .NET Framework 4,5 a vyšších, .NET Core a prostředí Windows Runtime. [ C# ](../../../whats-new/csharp-version-history.md#c-version-50) Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.

Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.

## <a name="BKMK_WhentoUseAsynchrony"></a>Asynchronní funkce vylepšuje rychlost odezvy.

Asynchronii je nezbytné pro aktivity, které jsou potenciálně blokovány, například webový přístup. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková aktivita zablokovaná v synchronním procesu, musí počkat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.

Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z rozhraní .NET a prostředí Windows Runtime obsahují metody, které podporují asynchronní programování.

| Oblast aplikace    | Typy .NET s asynchronními metodami     | Typy prostředí Windows Runtime s asynchronními metodami  |
|---------------------|-----------------------------------|-------------------------------------------|
|Webový přístup|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Práce se soubory|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader> <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|
|Práce s obrázky||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder> <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programování WCF|[Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||

Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.

Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.

Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Asynchronní metody se snáze zapisují

Klíčová slova [](../../../language-reference/operators/await.md) [Async](../../../language-reference/keywords/async.md) a await C# v jsou srdcem asynchronního programování. Pomocí těchto dvou klíčových slov můžete použít prostředky v .NET Framework, .NET Core nebo v prostředí Windows Runtime k vytvoření asynchronní metody téměř stejně snadno, jako vytvoříte synchronní metodu. Asynchronní metody, které definujete pomocí klíčového slova `async`, jsou označovány jako *asynchronní metody*.

Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé.

Na konci tohoto tématu můžete najít úplný ukázkový soubor Windows Presentation Foundation (WPF) a můžete si stáhnout ukázku z [Async Sample: příklad z tématu "asynchronní programování s Async a await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/).

```csharp
async Task<int> AccessTheWebAsync()
{
    // You need to add a reference to System.Net.Http to declare client.
    var client = new HttpClient();

    // GetStringAsync returns a Task<string>. That means that when you await the
    // task you'll get a string (urlContents).
    Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com/dotnet");

    // You can do work here that doesn't rely on the string from GetStringAsync.
    DoIndependentWork();

    // The await operator suspends AccessTheWebAsync.
    //  - AccessTheWebAsync can't continue until getStringTask is complete.
    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.
    //  - Control resumes here when getStringTask is complete.
    //  - The await operator then retrieves the string result from getStringTask.
    string urlContents = await getStringTask;

    // The return statement specifies an integer result.
    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.
    return urlContents.Length;
}
```

V předchozím příkladu se můžete seznámit s několika postupy. Začněte s podpisem metody. Obsahuje modifikátor `async`. Návratový typ je `Task<int>` (další možnosti naleznete v části "návratové typy"). Název metody končí na `Async`. V těle metody `GetStringAsync` vrátí `Task<string>`. To znamená, že když `await` úkol, získáte `string` (`urlContents`).  Před čekáním na úlohu můžete provádět práci, která nespoléhá na `string` od `GetStringAsync`.

Věnujte velkou pozornost operátoru `await`. Pozastaví `AccessTheWebAsync`;

- `AccessTheWebAsync` nemůže pokračovat, dokud se nedokončí `getStringTask`.
- Mezitím se ovládací prvek vrátí volajícímu `AccessTheWebAsync`.
- Pokud je dokončeno `getStringTask`, ovládací prvky se obnoví.
- Operátor `await` potom načte výsledek `string` z `getStringTask`.

Příkaz return určuje celočíselný výsledek. Všechny metody, které čekají `AccessTheWebAsync` načte hodnotu length.

Pokud `AccessTheWebAsync` nemá žádnou práci, kterou může provést mezi voláním `GetStringAsync` a čekáním na jeho dokončení, můžete zjednodušit kód voláním a čekáním v následujícím jediném příkazu.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Následující charakteristiky shrnují, co dělá předchozí příklad asynchronní metodou:

- Signatura metody obsahuje modifikátor `async`.
- Název asynchronní metody končí podle konvence příponou „Async“.
- Návratový typ je jeden z následujících typů:

  - <xref:System.Threading.Tasks.Task%601>, pokud vaše metoda má návratový příkaz, ve kterém je operand typu `TResult`.
  - <xref:System.Threading.Tasks.Task>, pokud vaše metoda nemá návratový příkaz nebo má návratový příkaz bez operandu.
  - `void`, pokud píšete asynchronní obslužnou rutinu události.
  - Jakýkoli jiný typ, který má metodu `GetAwaiter` (počínaje C# 7,0).

  Další informace naleznete v části [návratové typy a parametry](#BKMK_ReturnTypesandParameters) .

- Metoda obvykle zahrnuje nejméně jeden výraz `await`, který označuje bod, kde metoda nemůže pokračovat, dokud se neočekává dokončená asynchronní operace. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.

V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.

Další informace o asynchronii v předchozích verzích .NET Framework naleznete v tématu [TPL a tradiční .NET Framework asynchronní programování](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co se stane v asynchronní metodě

Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem:

![Trasování asynchronního programu](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "NavigationTrace")

Čísla v diagramu odpovídají následujícím krokům, které jsou iniciovány, když uživatel klikne na tlačítko Start.

1. Obslužná rutina události volá a očekává asynchronní metodu `AccessTheWebAsync`.

2. `AccessTheWebAsync` vytvoří instanci <xref:System.Net.Http.HttpClient> a zavolá asynchronní metodu <xref:System.Net.Http.HttpClient.GetStringAsync%2A> pro stažení obsahu webu jako řetězce.

3. Něco se stane v `GetStringAsync`, které pozastaví jeho průběh. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. Aby nedocházelo k blokování prostředků, `GetStringAsync` poskytne řízení volajícímu, `AccessTheWebAsync`.

     `GetStringAsync` vrátí <xref:System.Threading.Tasks.Task%601>, kde `TResult` je řetězec a `AccessTheWebAsync` přiřadí úkol proměnné `getStringTask`. Úkol představuje nepřetržitý proces pro volání `GetStringAsync` s závazkem vytvořit skutečnou řetězcovou hodnotu po dokončení práce.

4. Vzhledem k tomu, že `getStringTask` nebyl dosud očekáván, `AccessTheWebAsync` může pokračovat v práci s dalšími úkoly, které nezávisí na konečném výsledku z `GetStringAsync`. Tato práce je reprezentována voláním synchronní metody `DoIndependentWork`.

5. `DoIndependentWork` je synchronní metoda, která provede svou práci a vrátí jejímu volajícímu.

6. `AccessTheWebAsync` vyčerpala práci, kterou může provádět bez výsledku z `getStringTask`. `AccessTheWebAsync` další chce vypočítat a vrátit délku staženého řetězce, ale metoda nemůže tuto hodnotu vypočítat, dokud metoda nemá řetězec.

     Proto `AccessTheWebAsync` používá operátor await k pozastavení průběhu a k řízení metody, která se nazývá `AccessTheWebAsync`. `AccessTheWebAsync` vrátí volajícímu hodnotu `Task<int>`. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.

    > [!NOTE]
    > Pokud je `GetStringAsync` (a tedy `getStringTask`) dokončeno před tím, než `AccessTheWebAsync` očekává, řízení zůstane v `AccessTheWebAsync`. Náklady na pozastavení a návrat do `AccessTheWebAsync` by byly vyvolány, pokud se volal asynchronní proces (`getStringTask`) již dokončen a `AccessTheWebAsync` nemusí čekat na konečný výsledek.

     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může provést další práci, která nezávisí na výsledku z `AccessTheWebAsync` před čekáním na výsledek, nebo volající může očekávat okamžitě.   Obslužná rutina události čeká na `AccessTheWebAsync` a `AccessTheWebAsync` čeká na `GetStringAsync`.

7. `GetStringAsync` se dokončí a vytvoří výsledek řetězce. Výsledek řetězce není vrácen voláním `GetStringAsync` způsobem, který byste mohli očekávat. (Nezapomeňte, že metoda již vrátila úlohu v kroku 3.) Místo toho je výsledek řetězce uložen v úkolu, který představuje dokončení metody, `getStringTask`. Operátor await načte výsledek z `getStringTask`. Příkaz přiřazení přiřadí načtený výsledek do `urlContents`.

8. Když `AccessTheWebAsync` má výsledek řetězce, metoda může vypočítat délku řetězce. Pak se dokončí i práce `AccessTheWebAsync` a může pokračovat obslužná rutina čekající události. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.
Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.

Další informace o toku řízení naleznete v tématu [Flow Control in Async ProgramsC#()](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>Asynchronní metody rozhraní API

Možná vás zajímá, kde najít metody jako `GetStringAsync`, které podporují asynchronní programování. .NET Framework 4,5 nebo vyšší a .NET Core obsahují mnoho členů, kteří pracují s `async` a `await`. Můžete je rozpoznat pomocí přípony "Async", která je připojena k názvu člena, a jejich návratovým typem <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Například třída `System.IO.Stream` obsahuje metody jako <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> a <xref:System.IO.Stream.WriteAsync%2A> vedle synchronních metod <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> a <xref:System.IO.Stream.Write%2A>.

Prostředí Windows Runtime také obsahuje řadu metod, které můžete použít s `async` a `await` v aplikacích pro Windows. Další informace najdete v tématech [dělení vlákna a asynchronní programování](/windows/uwp/threading-async/) pro vývoj UWP a [asynchronní programování (aplikace pro Windows Store)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) a [rychlý Start: volání asynchronních C# rozhraní API v nebo Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) , pokud používáte starší verze nástroje prostředí Windows Runtime.

## <a name="BKMK_Threads"></a>Vláken

Asynchronní metody mají být neblokující operace. Výraz `await` v asynchronní metodě neblokuje aktuální vlákno, zatímco je spuštěn očekávaný úkol. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.

Klíčová slova `async` a `await` nezpůsobí vytvoření dalších vláken. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. @No__t-0 můžete použít pro přesun práce vázané na procesor do vlákna na pozadí, ale vlákno na pozadí nepomůže s procesem, který právě čeká na zpřístupnění výsledků.

Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Konkrétně tento přístup je lepší než třída <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na vstupně-výstupní operace, protože kód je jednodušší a nemusíte se chránit před konflikty časování. V kombinaci s metodou <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> je asynchronní programování lepší než <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor, protože asynchronní programování odděluje koordinační informace o spuštění kódu z práce, která `Task.Run` přenáší do fondu vláken.

## <a name="BKMK_AsyncandAwait"></a>Async a await

Pokud určíte, že metoda je asynchronní metodou pomocí modifikátoru [Async](../../../language-reference/keywords/async.md) , povolíte následující dvě možnosti.

- Označená asynchronní metoda může použít [operátor await](../../../language-reference/operators/await.md) k určení bodů zavěšení. Operátor `await` instruuje kompilátor, že asynchronní metoda nemůže pokračovat za tímto bodem, dokud není dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.

     Pozastavení asynchronní metody na výrazu `await` nepředstavuje příkaz exit z metody a bloky `finally` nejsou spouštěny.

- Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.

Asynchronní metoda obvykle obsahuje jeden nebo více výskytů operátoru `await`, ale absence výrazů `await` nezpůsobí chybu kompilátoru. Pokud asynchronní metoda nepoužívá operátor `await` k označení bodu pozastavení, metoda se spustí jako synchronní metoda bez ohledu na modifikátor `async`. Kompilátor u takových metod zahlásí upozornění.

`async` a `await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Návratové typy a parametry

Asynchronní metoda obvykle vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. V rámci asynchronní metody je operátor `await` použit pro úkol, který je vrácen z volání jiné asynchronní metody.

Zadejte <xref:System.Threading.Tasks.Task%601> jako návratový typ, pokud metoda obsahuje příkaz [`return`](../../../language-reference/keywords/return.md) , který určuje operand typu `TResult`.

@No__t-0 použijete jako návratový typ, pokud metoda nemá žádný návratový příkaz nebo má návratový příkaz, který nevrací operand.

Počínaje C# 7,0 můžete také zadat jakýkoli jiný návratový typ za předpokladu, že typ obsahuje metodu `GetAwaiter`. <xref:System.Threading.Tasks.ValueTask%601> je příklad takového typu. Je k dispozici v balíčku NuGet [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) .

Následující příklad ukazuje, jak deklarovat a volat metodu, která vrací <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>:

```csharp
// Signature specifies Task<TResult>
async Task<int> GetTaskOfTResultAsync()
{
    int hours = 0;
    await Task.Delay(0);
    // Return statement specifies an integer result.
    return hours;
}

// Calls to GetTaskOfTResultAsync
Task<int> returnedTaskTResult = GetTaskOfTResultAsync();
int intResult = await returnedTaskTResult;
// or, in a single statement
int intResult = await GetTaskOfTResultAsync();

// Signature specifies Task
async Task GetTaskAsync()
{
    await Task.Delay(0);
    // The method has no return statement.
}

// Calls to GetTaskAsync
Task returnedTask = GetTaskAsync();
await returnedTask;
// or, in a single statement
await GetTaskAsync();
```

Každá vrácená úloha představuje probíhající práci. Úloha zapouzdřuje informace o stavu asynchronního procesu a posléze buď konečný výsledek z procesu, nebo výjimku, kterou proces vyvolá v případě neúspěchu.

Asynchronní metoda může mít také návratový typ `void`. Tento návratový typ slouží primárně k definování obslužných rutin událostí, kde je požadován návratový typ `void`. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.

Asynchronní metoda, která má návratový typ `void`, nemůže být očekávána a volající metody vracející typ void nemůže zachytit žádné výjimky, které metoda vyvolá.

Asynchronní metoda [nemůže deklarovat parametry](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) nebo [out](../../../language-reference/keywords/out-parameter-modifier.md) , ale metoda může volat metody, které mají tyto parametry. Podobně asynchronní metoda nemůže vrátit hodnotu odkazem, přestože může volat metody s návratovými hodnotami ref.

Další informace a příklady naleznete v tématu [Async Return TypesC#()](./async-return-types.md). Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v tématu [try-catch](../../../language-reference/keywords/try-catch.md).

Asynchronní rozhraní API v prostředí Windows Runtime programování mají jeden z následujících návratových typů, které jsou podobné úlohám:

- <xref:Windows.Foundation.IAsyncOperation%601>, který odpovídá <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, který odpovídá <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Konvence pojmenování

Podle konvence metody, které vracejí běžně neočekávané typy (např. `Task`, `Task<T>`, `ValueTask`, `ValueTask<T>`), by měly mít názvy, které končí na "Async". Metody, které spouštějí asynchronní operaci, ale nevracejí očekávaný typ, by neměly mít názvy, které končí na "Async", ale mohou začínat na "begin", "Start" nebo některé jiné operace, které tuto metodu navrhují, nevrátí ani nevyvolávají výsledek operace.

Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například byste neměli přejmenovat běžné obslužné rutiny událostí, jako je například `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a>Související témata a ukázky (Visual Studio)

|Název|Popis|Ukázka|
|-----------|-----------------|------------|
|[Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Asynchronní Ukázka: přístup k webovému návodu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá do předchozího návodu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Použití `WhenAll` spustí všechna stahování ve stejnou dobu.||
|[Postupy: paralelní provádění více webových požadavků pomocí modifikátoru Async a operátoru awaitC#()](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Asynchronní vzorek: paralelní provádění více webových požadavků](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Asynchronní návratové typyC#()](./async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||
|[Řízení toku v asynchronních programechC#()](./control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Asynchronní vzorek: tok řízení v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Vyladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> - [zrušení asynchronní úlohy nebo seznamu úkolůC#()](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [zrušit asynchronní úlohy po určitém časovém intervaluC#()](./cancel-async-tasks-after-a-period-of-time.md)<br />- [zrušit zbývající asynchronní úlohy po dokončení jedné operace (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />@no__t – 0[spustí několik asynchronních úloh a zpracuje je po dokončení (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md) .|[Asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zpracování Vícenásobný přístup v asynchronních aplikacíchC#()](./handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je aktivní asynchronní operace restartována v době, kdy běží.||
|[WhenAny: přemostění mezi .NET Framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Ukazuje, jak přemostění mezi typy úloh v .NET Framework a IAsyncOperations v prostředí Windows Runtime, aby bylo možné použít <xref:System.Threading.Tasks.Task.WhenAny%2A> s metodou prostředí Windows Runtime.|[Asynchronní vzorek: přemostění mezi rozhraním .NET a prostředí Windows Runtime (AsTask a WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak přemostění mezi typy úloh v .NET Framework a IAsyncOperations v prostředí Windows Runtime, aby bylo možné použít <xref:System.Threading.CancellationTokenSource> s metodou prostředí Windows Runtime.|[Asynchronní vzorek: přemostění mezi rozhraním .NET a prostředí Windows Runtime (zrušení & AsTask)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Použití Async pro přístup k souborůmC#()](./using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Vzor je založen na typech <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601>.||
|[Asynchronní videa na Channel 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Poskytuje odkazy na různá videa o asynchronním programování.||

## <a name="BKMK_CompleteExample"></a>Kompletní příklad

Následující kód je soubor *MainWindow.XAML.cs* z aplikace WPF, kterou popisuje tento článek. Ukázku si můžete stáhnout z [části Async Sample: příklad z "asynchronní programování s Async a await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/).

[!code-csharp[async](~/samples/async/async-and-await/cs/MainWindow.xaml.cs)]

## <a name="see-also"></a>Viz také:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Asynchronní programování](../../../async.md)
- [Asynchronní přehled](../../../../standard/async.md)
