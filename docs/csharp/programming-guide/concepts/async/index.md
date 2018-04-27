---
title: Asynchronní programování pomocí modifikátoru async a operátoru await (C#)
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
caps.latest.revision: 5
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 70dd5606ba81619658eda24f8c4bfd4970d29308
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="asynchronous-programming-with-async-and-await-c"></a>Asynchronní programování pomocí modifikátoru async a operátoru await (C#)
Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.  
  
[C# 5](../../../whats-new/index.md#previous-versions) zavedená zjednodušenou metodu, asynchronní programování, které využívá asynchronní podpora v rozhraní .NET Framework 4.5 a vyšší, .NET Core a prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.  
  
Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Asynchronní zlepšuje odezvu  
 Asynchrony je nezbytné pro aktivity, které jsou potenciálně blokování, například webový přístup. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud tuto činnost je blokován v synchronní procesu, čekat, bude celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.  
  
 Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z rozhraní .NET a prostředí Windows Runtime obsahovat metody, které podporují asynchronní programování.  
  
| Oblast aplikace    | Typy .NET u asynchronních metod     | Typy prostředí Windows Runtime s asynchronní metody  |
|---------------------|-----------------------------------|-------------------------------------------|
|Webový přístup|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Práce se soubory|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|  
|Práce s obrázky||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|Programování WCF|[Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.  
  
 Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.  
  
 Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Asynchronní metody jsou psát  
 [Asynchronní](../../../../csharp/language-reference/keywords/async.md) a [await](../../../../csharp/language-reference/keywords/await.md) klíčová slova v jazyce C# jsou srdcem asynchronní programování. Pomocí těchto dvou klíčová slova, můžete prostředky v rozhraní .NET Framework, .NET Core nebo prostředí Windows Runtime téměř jako snadno, jako je vytváření synchronní metoda vytvoření asynchronní metodu. Asynchronní metody, které definujete pomocí `async` – klíčové slovo se označují jako *asynchronní metody*.  
  
 Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé. Komentáře volají funkce, které jste přidali při tvorbě asynchronie.  
  
 Úplný příklad souboru Windows Presentation Foundation (WPF) na konci tohoto tématu můžete najít a si můžete stáhnout ukázkový z [asynchronní ukázka: příklad z "Asynchronní programování s Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    HttpClient client = new HttpClient();  
  
    // GetStringAsync returns a Task<string>. That means that when you await the  
    // task you'll get a string (urlContents).  
    Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
  
 Pokud `AccessTheWebAsync` nemá veškerou práci, kterou můžete provést mezi voláním `GetStringAsync` a čeká na její dokončení, můžete zjednodušit kód voláním a čeká na v následující jeden příkaz.  
  
```csharp  
string urlContents = await client.GetStringAsync();  
```  
 
Následující charakteristiky představují shrnutí, co dělá předchozí příklad asynchronní metodou.  
  
-   Podpis metody zahrnuje `async` modifikátor.  
  
-   Název asynchronní metody končí podle konvence příponou „Async“.  
  
-   Návratový typ je jeden z následujících typů:  
  
    -   <xref:System.Threading.Tasks.Task%601> Pokud vaše metoda má příkaz return, ve kterém má operand typu `TResult`.  
  
    -   <xref:System.Threading.Tasks.Task> Pokud vaše metoda má žádný příkaz return nebo příkaz return s žádné operand.  
  
    -   `void` Pokud píšete asynchronní obslužnou rutinu.  

    -   Jiný typ, který má `GetAwaiter` – metoda (počínaje 7.0 C#).
  
     Další informace najdete v tématu [parametry a vrátí typy](#BKMK_ReturnTypesandParameters) části.  
  
-   Metoda obvykle zahrnuje nejméně jeden očekávaný výraz, který označuje bod, kde metoda nemůže pokračovat, dokud očekávaná asynchronní operace nebude dokončena. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.  
  
 V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.  
  
 Další informace o asynchrony v předchozích verzích rozhraní .NET Framework najdete v tématu [TPL a tradiční rozhraní .NET Framework asynchronní programování](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co se stane, že v asynchronní metody  
 Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem.  
  
 ![Sledování aplikace asynchronní](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Čísla v diagramu odpovídají následujícím krokům.  
  
1.  Volá obslužnou rutinu události a čeká `AccessTheWebAsync` asynchronní metody.  
  
2.  `AccessTheWebAsync` vytvoří <xref:System.Net.Http.HttpClient> instance a volání <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronní metody pro stažení obsahu webu, jako řetězec.  
  
3.  Něco se stane, že v `GetStringAsync` který pozastaví jejím průběhu. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. K zabránění blokování prostředky, `GetStringAsync` vypočítá ovládacího prvku do jeho volajícího `AccessTheWebAsync`.  
  
     `GetStringAsync` Vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je řetězec, a `AccessTheWebAsync` přiřadí úlohu, aby `getStringTask` proměnné. Úloha představuje proces probíhající pro volání `GetStringAsync`, s závazek k vytvoření hodnotu konkrétní řetězec po dokončení práce.  
  
4.  Protože `getStringTask` nebyl ještě očekávaná `AccessTheWebAsync` můžete pokračovat v dalších práci, kterou nezávisí na konečný výsledek z `GetStringAsync`. Pracovní je reprezentována volání synchronní metoda `DoIndependentWork`.  
  
5.  `DoIndependentWork` je synchronní metoda, která nemá svou práci a vrátí jeho volajícího.  
  
6.  `AccessTheWebAsync` nemá dostatek práci, kterou můžete provést bez výsledek z `getStringTask`. `AccessTheWebAsync` Další chce výpočtu a vrátí délku stažené řetězec, ale metoda nemůže tuto hodnotu vypočítat, dokud metoda obsahuje řetězec.  
  
     Proto `AccessTheWebAsync` používá operátor await pozastavit jeho průběh a yield – ovládací prvek na metodu, která volá `AccessTheWebAsync`. `AccessTheWebAsync` Vrátí `Task<int>` volajícímu. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.  
  
    > [!NOTE]
    >  Pokud `GetStringAsync` (a proto `getStringTask`) dokončení před `AccessTheWebAsync` čeká se pořád řízení `AccessTheWebAsync`. Nákladů na pozastavení a vrátilo se do `AccessTheWebAsync` by dojít ke znehodnocení části Pokud volané asynchronní proces (`getStringTask`) je již dokončena a `AccessTheWebSync` nemusí čekat na konečný výsledek.  
  
     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může provádět další činnosti, které nezávisí na výsledku z `AccessTheWebAsync` před čeká na tento výsledek nebo volající může await okamžitě.   Obslužné rutiny události se čeká na `AccessTheWebAsync`, a `AccessTheWebAsync` čeká `GetStringAsync`.  
  
7.  `GetStringAsync` dokončí a vytvoří výsledek řetězec. Není řetězec výsledek vrácený volání `GetStringAsync` takovým způsobem, který by se dalo očekávat. (Nezapomeňte, že metoda již vrátí úlohu v kroku 3.) Místo toho řetězec výsledek je uložen v úloha, která představuje dokončení metody, `getStringTask`. Operátor await načte výsledek z `getStringTask`. Příkaz přiřazení přiřadí načtené výsledek, který má `urlContents`.  
  
8.  Když `AccessTheWebAsync` řetězec výsledek, obsahuje metodu můžete vypočítat délka řetězce. Potom práci při `AccessTheWebAsync` je také dokončení, a můžete pokračovat v čekání na popisovač události. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.    
Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.  
  
Další informace o toku řízení najdete v tématu [řízení toku v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Rozhraní API asynchronní metody  
 Možná se ptáte kde najít metody, jako `GetStringAsync` tuto podporu asynchronní programování. Rozhraní .NET Framework 4.5 nebo vyšší a .NET Core obsahují mnoho členů, které pracují s `async` a `await`. Můžete je rozpoznat příponou "Asynchronní", který se připojí k název člena a jejich návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Například `System.IO.Stream` třída obsahuje metody, jako například <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, a <xref:System.IO.Stream.WriteAsync%2A> spolu s synchronních metod <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, a <xref:System.IO.Stream.Write%2A>.  
  
 Prostředí Windows Runtime také obsahuje mnoho způsobů, které můžete použít s `async` a `await` v aplikacích pro Windows. Další informace najdete v tématu [zřetězení a asynchronní programování](/windows/uwp/threading-async/) pro vývoj UWP a [asynchronní programování (aplikace pro Windows Store)](/previous-versions/windows/apps/hh464924(v=win.10)) a [rychlý start: volání asynchronní rozhraní API v jazyce C# nebo Visual Basic](/previous-versions/windows/apps/hh452713(v=win.10)) Pokud používáte starší verze prostředí Windows Runtime.  
  
##  <a name="BKMK_Threads"></a> Vláken  
Asynchronní metody mají být neblokující operace. `await` Výrazu v asynchronní metody neblokuje aktuální vlákno spuštěného awaited úloh. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.  
  
`async` a `await` klíčová slova nejsou způsobit další vláken, který se má vytvořit. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> přesunout vázané na procesor pracovní vlákna na pozadí, ale na pozadí nemá přístup z více vláken usnadní proces, který se právě čeká na výsledky k dispozici.  
  
Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Konkrétně tento přístup je lepší, než <xref:System.ComponentModel.BackgroundWorker> třídy pro vázané na vstupně-výstupní operace, protože kód je jednodušší a nemusíte chránit proti časování. V kombinaci s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda, je lepší, než asynchronní programování <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor protože asynchronní programování odděluje podrobnosti koordinaci spuštěním kódu z práce `Task.Run` přenese fondu.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async a operátoru await  
 Pokud určíte, že je metoda asynchronní metody pomocí [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor, povolte následující dvě možnosti.  
  
-   Můžete použít označený asynchronní metody [await](../../../../csharp/language-reference/keywords/await.md) k určení bodů pozastavení. `await` Operátor říká kompilátoru za tento bod nemůže pokračovat asynchronní metody, dokud awaited asynchronní proces nebude hotový. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.  
  
     Pozastavení použití asynchronní metody na `await` výrazu není tvoří výstupu z metody, a `finally` nespouštět bloky.  
  
-   Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.  
  
Asynchronní metody obvykle obsahuje jeden nebo více výskytů `await` operátor, ale chybí `await` výrazy není způsobit chyby kompilátoru. Pokud asynchronní metody nepoužívá `await` operátor označit bod pozastavení metoda provádí synchronní metoda stejně bez ohledu `async` modifikátor. Kompilátor u takových metod zahlásí upozornění.  
  
 `async` a `await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:  
  
-   [async](../../../../csharp/language-reference/keywords/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Parametry a návratové typy  
Asynchronní metody obvykle vrátí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Uvnitř použití asynchronní metody `await` operátor se použije pro úlohu, která je vrácena z volání jiného asynchronní metody.  
  
Zadáte <xref:System.Threading.Tasks.Task%601> jako návratový typ, pokud obsahuje metodu [vrátit](../../../../csharp/language-reference/keywords/return.md) příkaz, který určuje operand typu `TResult`. 
  
Používáte <xref:System.Threading.Tasks.Task> jako návratový typ, pokud metoda má žádný příkaz return nebo který nevrací operand příkaz return.  

Od verze 7.0 C#, můžete také určit další návratový typ, za předpokladu, že daný typ obsahuje `GetAwaiter` metoda. <xref:System.Threading.Tasks.ValueTask%601> je příkladem takového typu. Je k dispozici v [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) balíček NuGet.
  
 Následující příklad ukazuje, jak deklarace a volání metody, která vrací <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> TaskOfTResult_MethodAsync()  
{  
    int hours;  
    // . . .  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to TaskOfTResult_MethodAsync  
Task<int> returnedTaskTResult = TaskOfTResult_MethodAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await TaskOfTResult_MethodAsync();  
  
// Signature specifies Task  
async Task Task_MethodAsync()  
{  
    // . . .  
    // The method has no return statement.    
}  
  
// Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync();  
await returnedTask;  
// or, in a single statement  
await Task_MethodAsync();  
```  
  
Každá vrácená úloha představuje probíhající práci. Úloha zapouzdřuje informace o stavu asynchronního procesu a posléze buď konečný výsledek z procesu, nebo výjimku, kterou proces vyvolá v případě neúspěchu.  
  
Asynchronní metody může mít `void` návratovým typem. Tato vrátí typ se používá hlavně k definování obslužné rutiny událostí, kde `void` návratový typ je požadovaná. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.  
  
Asynchronní metody, který má `void` vrátí typ nemůže být očekáváno a volající metody vrácení void nelze zachytit všechny výjimky, které vyvolá metoda.  
  
Asynchronní metody nelze deklarovat [v](../../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ale metodu můžete volat metody, které mají tyto parametry. Asynchronní metody Podobně nelze vrátit hodnotu odkazu, i když ho můžete volat metody s ref návratové hodnoty. 
  
Další informace a příklady naleznete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Další informace o tom, jak zachycení výjimek v asynchronní metody najdete v tématu [try-catch –](../../../../csharp/language-reference/keywords/try-catch.md). 
  
Asynchronní rozhraní API v prostředí Windows Runtime programování mít jednu z následujících návratové typy, které jsou podobné úlohy:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, která odpovídá <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, která odpovídá <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a> Zásady vytváření názvů  
 Podle konvence připojit "Asynchronní" na názvy metod, které mají `async` modifikátor.  
  
 Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například by nemělo přejmenovat běžné obslužné rutiny událostí, například `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Související témata a ukázky (Visual Studio)  
  
|Název|Popis|Ukázka|  
|-----------|-----------------|------------|  
|[Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Ukázka asynchronního: Přístup k webové názorný postup](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do předchozího návodu. Použití `WhenAll` spustí všechny soubory ke stažení ve stejnou dobu.||  
|[Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Ukázka asynchronního: Paralelní provádění vícenásobných webových dotazů](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||  
|[Řízení toku v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Ukázka asynchronního: Řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Vyladění s modifikátorem Async aplikace (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> -   [Zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Zrušení asynchronních úloh po uplynutí časového intervalu (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Zrušení zbývajících asynchronních úloh po dokončení (C#) jedné z nich](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Ukázka asynchronního: Jemnou ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je aktivní asynchronní operace restartována po jejím spuštění.||  
|[WhenAny: Přemostění rozhraní .NET Framework a prostředí Windows Runtime](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|Ukazuje, jak přemostění mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Ukázka asynchronního: Přemostění rozhraní .NET a prostředí Windows Runtime (metody AsTask a WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak přemostění mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby můžete použít <xref:System.Threading.CancellationTokenSource> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Ukázka asynchronního: Přemostění rozhraní .NET a prostředí Windows Runtime (metody AsTask & zrušení)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Použití modifikátoru Async pro přístup k souborům (C#)](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||  
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Je na základě vzoru <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> typy.||  
|[Asynchronní videa na kanálu 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Poskytuje odkazy na různá videa o asynchronním programování.||  
  
##  <a name="BKMK_CompleteExample"></a> Úplný příklad  
 Následující kód je soubor MainWindow.xaml.cs z aplikace Windows Presentation Foundation (WPF), která toto téma popisuje. Si můžete stáhnout ukázkový z [asynchronní ukázka: příklad z "Asynchronní programování s Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http;  
using System.Net.Http;  
  
namespace AsyncFirstExample  
{  
    public partial class MainWindow : Window  
    {  
        // Mark the event handler with async so you can use await in it.  
        private async void StartButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Call and await separately.  
            //Task<int> getLengthTask = AccessTheWebAsync();  
            //// You can do independent work here.  
            //int contentLength = await getLengthTask;  
  
            int contentLength = await AccessTheWebAsync();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            HttpClient client = new HttpClient();  
  
            // GetStringAsync returns a Task<string>. That means that when you await the  
            // task you'll get a string (urlContents).  
            Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 41564.  
```  
  
## <a name="see-also"></a>Viz také  
 [async](../../../../csharp/language-reference/keywords/async.md)  
 [await](../../../../csharp/language-reference/keywords/await.md)  
 [Asynchronní programování](../../../../csharp/async.md)  
 [Async – přehled](../../../../standard/async.md)  
