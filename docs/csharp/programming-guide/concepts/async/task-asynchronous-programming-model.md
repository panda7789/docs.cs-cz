---
title: Asynchronní programovací model úlohy (TAP) s asynchronní a čeká (C#)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 2700f5bfaa2746c1ea6f4862bee3af60cf83d693
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78848967"
---
# <a name="task-asynchronous-programming-model"></a>Model asynchronního programování úloh

Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.

[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) zavedla zjednodušený přístup, asynchronní programování, který využívá asynchronní podporu v rozhraní .NET Framework 4.5 a vyšší, .NET Core a Prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.

Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.

## <a name="BKMK_WhentoUseAsynchrony"></a>Async zlepšuje odezvu

Asynchrony je nezbytné pro aktivity, které jsou potenciálně blokování, jako je například přístup k webu. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková aktivita blokována v synchronním procesu, musí čekat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.

Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z rozhraní .NET a prostředí Windows Runtime obsahují metody, které podporují asynchronní programování.

| Oblast aplikace    | Typy .NET s asynchronními metodami     | Typy prostředí Windows Runtime s asynchronními metodami  |
|---------------------|-----------------------------------|-------------------------------------------|
|Webový přístup|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Práce se soubory|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|
|Práce s obrázky||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programování WCF|[Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||

Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.

Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.

Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Asynchronní metody se snadněji zapisují

[Async](../../../language-reference/keywords/async.md) a [await](../../../language-reference/operators/await.md) klíčová slova v jazyce C# jsou srdcem asynchronní programování. Pomocí těchto dvou klíčových slov můžete použít prostředky v rozhraní .NET Framework, .NET Core nebo Windows Runtime k vytvoření asynchronní metody téměř stejně snadno jako vytvoření synchronní metody. Asynchronní metody, které definujete `async` pomocí klíčového slova, jsou označovány jako *asynchronní metody*.

Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé.

Úplný ukázkový soubor Windows Presentation Foundation (WPF) najdete na konci tohoto tématu a ukázku si můžete stáhnout z [ukázky asynchronní: Příklad z "Asynchronní programování s async a await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/).

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

Můžete se naučit několik postupů z předchozí ukázky. Začněte podpisem metody. Obsahuje `async` modifikátor. Návratový typ `Task<int>` je (viz "Návratové typy" část pro další možnosti). Název metody končí `Async`v . V těle metody `GetStringAsync` vrátí . `Task<string>` To znamená, `await` že když úkol dostanete `string` `urlContents`( ).  Před čekáním na úkol, můžete udělat práci, `string` která `GetStringAsync`nespoléhá na od .

Věnujte `await` velkou pozornost operátorovi. Pozastavuje `AccessTheWebAsync`se ;

- `AccessTheWebAsync`nemůže pokračovat, `getStringTask` dokud není dokončena.
- Mezitím ovládací prvek vrátí `AccessTheWebAsync`volajícímu .
- Ovládací prvek pokračuje `getStringTask` zde po dokončení.
- Operátor `await` pak načte `string` výsledek `getStringTask`z .

Příkaz return určuje výsledek celéčíslo. Všechny metody, které `AccessTheWebAsync` čekají na načíst hodnotu délky.

Pokud `AccessTheWebAsync` nemá žádnou práci, kterou může `GetStringAsync` udělat mezi voláním a čekáním na jeho dokončení, můžete zjednodušit kód voláním a čekáním v následujícím jediném příkazu.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Následující charakteristiky shrnují, co dělá předchozí příklad asynchronní metodou:

- Podpis metody obsahuje `async` modifikátor.
- Název asynchronní metody končí podle konvence příponou „Async“.
- Návratový typ je jeden z následujících typů:

  - <xref:System.Threading.Tasks.Task%601>Pokud vaše metoda má return prohlášení, ve `TResult`kterém operand má typ .
  - <xref:System.Threading.Tasks.Task>Pokud vaše metoda nemá return příkaz nebo má návratový příkaz bez operandu.
  - `void`Pokud píšete asynchronní obslužnou rutinu události.
  - Jakýkoli jiný typ, `GetAwaiter` který má metodu (počínaje C# 7.0).

  Další informace naleznete v části [Návratové typy a parametry.](#BKMK_ReturnTypesandParameters)

- Metoda obvykle obsahuje alespoň `await` jeden výraz, který označuje bod, kde metoda nemůže pokračovat, dokud není dokončena očekávaná asynchronní operace. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.

V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.

Další informace o asynchronii v předchozích verzích rozhraní .NET Framework naleznete v [tématech TPL a Traditional .NET Framework AsynchronouProgramming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co se děje v asynchronní metodě

Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem:

![Sledování asynchronního programu](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "Navigační trasování")

Čísla v diagramu odpovídají následujícím krokům, které byly zahájeny, když uživatel klepne na tlačítko "start".

1. Obslužná rutina `AccessTheWebAsync` události volá a čeká na asynchronní metodu.

2. `AccessTheWebAsync`vytvoří <xref:System.Net.Http.HttpClient> instanci <xref:System.Net.Http.HttpClient.GetStringAsync%2A> a zavolá asynchronní metodu ke stažení obsahu webu jako řetězec.

3. Něco se `GetStringAsync` stane v tom, že pozastavuje jeho pokrok. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. Chcete-li se `GetStringAsync` vyhnout blokování prostředků, `AccessTheWebAsync`dává ovládací prvek jeho volajícímu , .

     `GetStringAsync`vrátí <xref:System.Threading.Tasks.Task%601>a `TResult` , kde je `AccessTheWebAsync` řetězec, a `getStringTask` přiřadí úkol proměnné. Úkol představuje probíhající proces volání `GetStringAsync`do , se závazkem vytvořit skutečnou hodnotu řetězce po dokončení práce.

4. Vzhledem k tomu, `getStringTask` nebyl `AccessTheWebAsync` dosud očekáván, může pokračovat v jiné `GetStringAsync`práci, která nezávisí na konečný výsledek z . Tato práce je reprezentována voláním `DoIndependentWork`synchronní metody .

5. `DoIndependentWork`je synchronní metoda, která provádí svou práci a vrátí se volajícímu.

6. `AccessTheWebAsync`vyčerpala práci, kterou může provést bez `getStringTask`výsledku . `AccessTheWebAsync`Další chce vypočítat a vrátit délku staženého řetězce, ale metoda nemůže vypočítat tuto hodnotu, dokud metoda má řetězec.

     Proto `AccessTheWebAsync` používá operátor await pozastavit jeho průběh a výnos `AccessTheWebAsync`řízení metody, která volala . `AccessTheWebAsync`vrátí `Task<int>` volajícímu. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.

    > [!NOTE]
    > Pokud `GetStringAsync` (a `getStringTask`proto ) `AccessTheWebAsync` dokončí před čeká, `AccessTheWebAsync`kontrola zůstává v . Náklady na pozastavení a následné `AccessTheWebAsync` návratu k by být zbytečné, pokud`getStringTask`se nazývá `AccessTheWebAsync` asynchronní proces ( ) již dokončena a nemusí čekat na konečný výsledek.

     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může dělat jinou práci, která nezávisí na výsledku před `AccessTheWebAsync` čekáním na tento výsledek, nebo volající může čekat okamžitě.   Obslužná `AccessTheWebAsync`rutina `AccessTheWebAsync` události `GetStringAsync`čeká na a čeká na .

7. `GetStringAsync`dokončí a vytvoří výsledek řetězce. Výsledek řetězce není vrácena volání `GetStringAsync` mj. (Nezapomeňte, že metoda již vrátila úkol v kroku 3.) Místo toho výsledek řetězce je uložen v úloze, `getStringTask`která představuje dokončení metody , . Operátor await načte výsledek `getStringTask`z . Příkaz přiřazení přiřadí načtený `urlContents`výsledek společnosti .

8. Když `AccessTheWebAsync` má výsledek řetězce, metoda může vypočítat délku řetězce. Pak je `AccessTheWebAsync` také dokončena práce a obslužná rutina události čekání může pokračovat. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.
Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.

Další informace o toku řízení naleznete [v tématu Řízení toku v asynchronních programech (C#)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>Asynchronní metody rozhraní API

Možná se divíte, kde `GetStringAsync` najít metody, jako je podpora asynchronníprogramování. Rozhraní .NET Framework 4.5 nebo vyšší a .NET `async` `await`Core obsahují mnoho členů, kteří pracují s a . Můžete je rozpoznat podle přípony "Async", která je připojena k názvu člena, a podle jejich návratového <xref:System.Threading.Tasks.Task> typu nebo <xref:System.Threading.Tasks.Task%601>. `System.IO.Stream` Třída například obsahuje metody <xref:System.IO.Stream.CopyToAsync%2A>jako <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A> , a vedle <xref:System.IO.Stream.CopyTo%2A>synchronních metod , <xref:System.IO.Stream.Read%2A>a <xref:System.IO.Stream.Write%2A>.

Prostředí Windows Runtime také obsahuje mnoho `async` metod, které můžete použít s aplikacemi pro Windows a `await` v nich. Další informace naleznete v [tématech Threading and async programming](/windows/uwp/threading-async/) for UPWP development a [Asynchronní programování (aplikace pro Windows Store)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) a [Úvodní příručka: Volání asynchronních rozhraní API v jazyce C# nebo Visual Basic,](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) pokud používáte starší verze prostředí Windows Runtime.

## <a name="BKMK_Threads"></a>Vlákna

Asynchronní metody mají být neblokující operace. Výraz `await` v asynchronní metodě neblokuje aktuální vlákno, když je spuštěna očekávaná úloha. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.

Klíčová `async` `await` slova a nezpůsobí další vlákna, která mají být vytvořena. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> k přesunutí práce vázané na procesor do vlákna na pozadí, ale vlákno na pozadí nepomůže s procesem, který čeká na výsledky, které budou k dispozici.

Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Zejména tento přístup je lepší <xref:System.ComponentModel.BackgroundWorker> než třída pro operace vstupně-výstupních operací, protože kód je jednodušší a není třeba chránit před sporech. V kombinaci <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> s metodou je asynchronní programování lepší než <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor, protože `Task.Run` asynchronní programování odděluje podrobnosti koordinace spuštění kódu od práce, která se přenáší do fondu vláken.

## <a name="BKMK_AsyncandAwait"></a>asynchronní a čekají

Pokud zadáte, že metoda je asynchronní metoda pomocí [asynchronnímodifikátor,](../../../language-reference/keywords/async.md) povolte následující dvě možnosti.

- Označená asynchronní metoda může použít [await k](../../../language-reference/operators/await.md) určení bodů pozastavení. Operátor `await` říká kompilátoru, že asynchronní metoda nemůže pokračovat za tímto bodem, dokud nebude dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.

     Pozastavení asynchronní metody ve `await` výrazu nepředstavuje výstup z metody `finally` a bloky nespustí.

- Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.

Asynchronní metoda obvykle obsahuje jeden nebo `await` více výskytů operátoru, ale absence výrazů `await` nezpůsobí chybu kompilátoru. Pokud asynchronní metoda nepoužívá `await` operátor k označení bodu pozastavení, metoda se provede jako synchronní `async` metoda, navzdory modifikátoru. Kompilátor u takových metod zahlásí upozornění.

`async`a `await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Návratové typy a parametry

Asynchronní metoda obvykle <xref:System.Threading.Tasks.Task> vrátí <xref:System.Threading.Tasks.Task%601>nebo . Uvnitř asynchronní metody `await` operátor je použita na úlohu, která je vrácena z volání do jiné asynchronní metody.

Jako <xref:System.Threading.Tasks.Task%601> návratový typ zadáte, pokud [`return`](../../../language-reference/keywords/return.md) metoda obsahuje příkaz, který `TResult`určuje operand typu .

Použijete <xref:System.Threading.Tasks.Task> jako návratový typ, pokud metoda nemá žádný příkaz return nebo má příkaz return, který nevrací operand.

Počínaje C# 7.0, můžete také zadat jakýkoli jiný návratový typ, za předpokladu, že typ obsahuje metodu. `GetAwaiter` <xref:System.Threading.Tasks.ValueTask%601>je příkladem takového typu. Je k dispozici v balíčku [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet.

Následující příklad ukazuje, jak deklarovat <xref:System.Threading.Tasks.Task%601> a <xref:System.Threading.Tasks.Task>volat metodu, která vrací nebo :

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

Asynchronní metoda může `void` mít také návratový typ. Tento návratový typ se používá především k `void` definování obslužné rutiny událostí, kde je vyžadován návratový typ. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.

Asynchronní metoda, `void` která má návratový typ nelze čekat a volající metody vrácení void nemůže zachytit žádné výjimky, které metoda vyvolá.

Asynchronní metoda nemůže deklarovat [v](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) nebo [out](../../../language-reference/keywords/out-parameter-modifier.md) parametry, ale metoda může volat metody, které mají tyto parametry. Podobně asynchronní metoda nemůže vrátit hodnotu odkazem, i když může volat metody s ref return values.

Další informace a příklady naleznete [v tématu Asynchronní návratové typy (C#)](./async-return-types.md). Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v [tématu try-catch](../../../language-reference/keywords/try-catch.md).

Asynchronní rozhraní API v programování prostředí Windows Runtime mají jeden z následujících návratových typů, které jsou podobné úlohám:

- <xref:Windows.Foundation.IAsyncOperation%601>, což odpovídá<xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, což odpovídá<xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Konvence

Podle konvence by metody, které vracejí běžně počkejtelné `Task<T>` `ValueTask`typy `ValueTask<T>`(např. `Task`, , ), ) měly mít názvy, které končí "Async". Metody, které spustí asynchronní operaci, ale nevracejí počkejtatý typ by neměl mít názvy, které končí "Async", ale může začínat "Begin", "Start", nebo některé jiné sloveso navrhnout tuto metodu nevrátí nebo vyvolat výsledek operace.

Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například byste neměli přejmenovat běžné obslužné rutiny událostí, například `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a>Příbuzná témata a ukázky (Visual Studio)

|Nadpis|Popis|Ukázka|
|-----------|-----------------|------------|
|[Návod: Přístup k webu pomocí asynchronní a čeká (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Ukázka asynchroniky: Přístup k webovému návodu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> k předchozímu návodu. Použití spustí `WhenAll` všechny soubory ke stažení ve stejnou dobu.||
|[Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Ukázka asynchroniky: Souběžně provádět více webových požadavků](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Asynchronní návratové typy (C#)](./async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||
|[Tok řízení v asynchronních programech (C#)](./control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Ukázka asynchroniky: Tok řízení v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Jemné doladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> - [Zrušení asynchronní úlohy nebo seznamu úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Zrušit asynchronní úkoly po časovém období (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [Zrušit zbývající asynchronní úlohy po dokončení jedné (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Asynchronní ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zpracování reentrancy v asynchronních aplikacích (C#)](./handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je spuštěna aktivní asynchronní operace.||
|[WhenAny: Přemostění mezi rozhraním .NET Framework a prostředím Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Ukazuje, jak přemostit mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v prostředí Windows Runtime, takže můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> s metodou Prostředí Windows Runtime.|[Ukázka asynchronní: Přemostění mezi rozhraními .NET a prostředím Windows Runtime (AsTask a WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak přemostit mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v prostředí Windows Runtime, takže můžete použít <xref:System.Threading.CancellationTokenSource> s metodou Prostředí Windows Runtime.|[Ukázka asynchronní: Přemostění mezi rozhraními .NET a prostředím Windows Runtime (AsTask & Zrušení)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Použití aplikace Async pro přístup k souborům (C#)](./using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Vzor je založen <xref:System.Threading.Tasks.Task> na <xref:System.Threading.Tasks.Task%601> a typy.||
|[Asynchronní videa na kanálu 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Poskytuje odkazy na různá videa o asynchronním programování.||

## <a name="BKMK_CompleteExample"></a>Kompletní příklad

Následující kód je *MainWindow.xaml.cs* soubor z aplikace WPF, který popisuje tento článek. Ukázku si můžete stáhnout z [ukázky Async: Příklad z "Asynchronní programování s async a Await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/).

[!code-csharp[async](~/samples/snippets/standard/async/async-and-await/cs/MainWindow.xaml.cs)]

## <a name="see-also"></a>Viz také

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Asynchronní programování](../../../async.md)
- [Přehled asynchronního](../../../../standard/async.md)
