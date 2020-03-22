---
title: Asynchronní programování pomocí modifikátoru Async a operátoru Await
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: cbcdd48571855e168f563585088f1210eb6410eb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266492"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Asynchronní programování s Async a Await (Visual Basic)

Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.

Visual Studio 2012 zavedlo zjednodušený přístup, asynchronní programování, který využívá asynchronní podporu v rozhraní .NET Framework 4.5 a vyšší, stejně jako v prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.

Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a>Async zlepšuje odezvu

Asynchronie je nezbytná pro aktivity, které mohou potenciálně blokovat, například pokud vaše aplikace přistupuje na web. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková činnost blokována v rámci synchronního procesu, musí čekat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.

Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z rozhraní .NET Framework 4.5 a prostředí Windows Runtime obsahují metody, které podporují asynchronní programování.

|Oblast aplikace|Podpora rozhraní API, která obsahují asynchronní metody|
|----------------------|------------------------------------------------|
|Webový přístup|<xref:System.Net.Http.HttpClient>, <xref:Windows.Web.Syndication.SyndicationClient>|
|Práce se soubory|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|
|Práce s obrázky|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programování WCF|[Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|
|||

Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.

Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.

Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.

## <a name="async-methods-are-easier-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a>Asynchronní metody se snadněji zapisují

[Klíčová slova Async](../../../../visual-basic/language-reference/modifiers/async.md) a [Await](../../../../visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic jsou srdcem asynchronního programování. Pomocí těchto dvou klíčových slov můžete použít prostředky v rozhraní .NET Framework nebo Windows Runtime k vytvoření asynchronní metody téměř stejně snadno jako synchronní metodu. Asynchronní metody, které definujete pomocí `Async` a `Await` jsou označovány jako asynchronní metody.

Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé. Komentáře volají funkce, které jste přidali při tvorbě asynchronie.

Úplný ukázkový soubor Windows Presentation Foundation (WPF) najdete na konci tohoto tématu a ukázku si můžete stáhnout z [ukázky asynchronní: Příklad z "Asynchronní programování s async a await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

```vb
' Three things to note about writing an Async Function:
'  - The function has an Async modifier.
'  - Its return type is Task or Task(Of T). (See "Return Types" section.)
'  - As a matter of convention, its name ends in "Async".
Async Function AccessTheWebAsync() As Task(Of Integer)
    Using client As New HttpClient()
        ' Call and await separately.
        '  - AccessTheWebAsync can do other things while GetStringAsync is also running.
        '  - getStringTask stores the task we get from the call to GetStringAsync.
        '  - Task(Of String) means it is a task which returns a String when it is done.
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://docs.microsoft.com/dotnet")
        ' You can do other work here that doesn't rely on the string from GetStringAsync.
        DoIndependentWork()
        ' The Await operator suspends AccessTheWebAsync.
        '  - AccessTheWebAsync does not continue until getStringTask is complete.
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.
        '  - Control resumes here when getStringTask is complete.
        '  - The Await operator then retrieves the String result from getStringTask.
        Dim urlContents As String = Await getStringTask
        ' The Return statement specifies an Integer result.
        ' A method which awaits AccessTheWebAsync receives the Length value.
        Return urlContents.Length

    End Using

End Function
```

Pokud `AccessTheWebAsync` nemá žádnou práci, kterou může `GetStringAsync` udělat mezi voláním a čekáním na jeho dokončení, můžete zjednodušit kód voláním a čekáním v následujícím jediném příkazu.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

Následující charakteristiky shrnují, co dělá předchozí příklad asynchronní metodou:

- Podpis metody obsahuje `Async` modifikátor.
- Název asynchronní metody končí podle konvence příponou „Async“.
- Návratový typ je jeden z následujících typů:

  - [Task(Of TResult),](xref:System.Threading.Tasks.Task%601) pokud vaše metoda má return prohlášení, ve kterém operand má typ TResult.
  - <xref:System.Threading.Tasks.Task>Pokud vaše metoda nemá return příkaz nebo má návratový příkaz bez operandu.
  - [Sub,](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) pokud píšete asynchronní obslužnou rutinu události.

  Další informace naleznete v části „Návratové typy a parametry“ dále v tomto tématu.

- Metoda obvykle zahrnuje nejméně jeden očekávaný výraz, který označuje bod, kde metoda nemůže pokračovat, dokud očekávaná asynchronní operace nebude dokončena. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.

V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.

Další informace o asynchronii v předchozích verzích rozhraní .NET Framework naleznete v [tématech TPL a Traditional .NET Framework AsynchronouProgramming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co se děje v asynchronní metodě

Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem:

![Diagram, který ukazuje sledování asynchronního programu.](./media/index/navigation-trace-async-program.png)

Čísla v diagramu odpovídají následujícím krokům:

1. Obslužná rutina `AccessTheWebAsync` události volá a čeká na asynchronní metodu.

2. `AccessTheWebAsync`vytvoří <xref:System.Net.Http.HttpClient> instanci <xref:System.Net.Http.HttpClient.GetStringAsync%2A> a zavolá asynchronní metodu ke stažení obsahu webu jako řetězec.

3. Něco se `GetStringAsync` stane v tom, že pozastavuje jeho pokrok. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. Chcete-li se `GetStringAsync` vyhnout blokování prostředků, `AccessTheWebAsync`dává ovládací prvek jeho volajícímu , .

     `GetStringAsync`vrátí [task(Of TResult),](xref:System.Threading.Tasks.Task%601) kde TResult je `AccessTheWebAsync` řetězec a přiřadí úkol `getStringTask` proměnné. Úkol představuje probíhající proces volání `GetStringAsync`do , se závazkem vytvořit skutečnou hodnotu řetězce po dokončení práce.

4. Vzhledem k tomu, `getStringTask` nebyl `AccessTheWebAsync` dosud očekáván, může pokračovat v jiné `GetStringAsync`práci, která nezávisí na konečný výsledek z . Tato práce je reprezentována voláním `DoIndependentWork`synchronní metody .

5. `DoIndependentWork`je synchronní metoda, která provádí svou práci a vrátí se volajícímu.

6. `AccessTheWebAsync`vyčerpala práci, kterou může provést bez `getStringTask`výsledku . `AccessTheWebAsync`Další chce vypočítat a vrátit délku staženého řetězce, ale metoda nemůže vypočítat tuto hodnotu, dokud metoda má řetězec.

     Proto `AccessTheWebAsync` používá operátor await pozastavit jeho průběh a výnos `AccessTheWebAsync`řízení metody, která volala . `AccessTheWebAsync`vrátí `Task(Of Integer)` volajícímu. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.

    > [!NOTE]
    > Pokud `GetStringAsync` (a `getStringTask`proto ) `AccessTheWebAsync` je dokončena před `AccessTheWebAsync`čeká, kontrola zůstává v . Náklady na pozastavení a potom `AccessTheWebAsync` návratu k by být zbytečné, pokud`getStringTask`se nazývá asynchronní proces ( ) již byla dokončena a AccessTheWebSync nemusí čekat na konečný výsledek.

     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může dělat jinou práci, která nezávisí na výsledku před `AccessTheWebAsync` čekáním na tento výsledek, nebo volající může čekat okamžitě.   Obslužná `AccessTheWebAsync`rutina `AccessTheWebAsync` události `GetStringAsync`čeká na a čeká na .

7. `GetStringAsync`dokončí a vytvoří výsledek řetězce. Výsledek řetězce není vrácena volání `GetStringAsync` mj. (Nezapomeňte, že metoda již vrátila úkol v kroku 3.) Místo toho výsledek řetězce je uložen v úloze, `getStringTask`která představuje dokončení metody , . Operátor await načte výsledek `getStringTask`z . Příkaz přiřazení přiřadí načtený `urlContents`výsledek společnosti .

8. Když `AccessTheWebAsync` má výsledek řetězce, metoda může vypočítat délku řetězce. Pak je `AccessTheWebAsync` také dokončena práce a obslužná rutina události čekání může pokračovat. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.

Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.

Další informace o toku řízení naleznete [v tématu Řízení toku v asynchronních programech (Visual Basic).](control-flow-in-async-programs.md)

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a>Asynchronní metody rozhraní API

Možná se divíte, kde `GetStringAsync` najít metody, jako je podpora asynchronníprogramování. Rozhraní .NET Framework 4.5 nebo vyšší `Async` obsahuje `Await`mnoho členů, kteří pracují s a . Tyto členy můžete rozpoznat podle přípony "Async", která je připojena k <xref:System.Threading.Tasks.Task> názvu člena a návratový typ nebo [Task(Of TResult)](xref:System.Threading.Tasks.Task%601). `System.IO.Stream` Třída například obsahuje metody <xref:System.IO.Stream.CopyToAsync%2A>jako <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A> , a vedle <xref:System.IO.Stream.CopyTo%2A>synchronních metod , <xref:System.IO.Stream.Read%2A>a <xref:System.IO.Stream.Write%2A>.

Prostředí Windows Runtime také obsahuje mnoho `Async` metod, které můžete použít s aplikacemi pro Windows a `Await` v nich. Další informace a ukázkové metody naleznete [v tématech Volání asynchronních rozhraní API v jazyce C# nebo Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [Asynchronní programování (aplikace prostředí Windows Runtime)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))a [WhenAny: Přemostění mezi rozhraním .NET Framework a prostředím Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).

## <a name="threads"></a><a name="BKMK_Threads"></a>Vlákna

Asynchronní metody mají být neblokující operace. Výraz `Await` v asynchronní metodě neblokuje aktuální vlákno, když je spuštěna očekávaná úloha. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.

Klíčová `Async` `Await` slova a nezpůsobí další vlákna, která mají být vytvořena. Asynchronní metody nevyžadují vícevláknové, protože asynchronní metoda neběží ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> k přesunutí práce vázané na procesor do vlákna na pozadí, ale vlákno na pozadí nepomůže s procesem, který čeká na výsledky, které budou k dispozici.

Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Zejména tento přístup je <xref:System.ComponentModel.BackgroundWorker> lepší než pro operace vstupně-výstupních operací, protože kód je jednodušší a není třeba chránit před sporáky. V kombinaci s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>asynchronní <xref:System.ComponentModel.BackgroundWorker> programování je lepší než pro operace vázané na procesor, protože `Task.Run` asynchronní programování odděluje podrobnosti koordinace spuštění kódu z práce, která se přenáší do fondu vláken.

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a>Asynchronní a Čekají

Pokud zadáte, že metoda je asynchronní metoda pomocí modifikátoru [Async,](../../../../visual-basic/language-reference/modifiers/async.md) povolte následující dvě možnosti.

- Označená asynchronní metoda může použít [Await](../../../../visual-basic/language-reference/operators/await-operator.md) k určení bodů pozastavení. Operátor await sděluje kompilátoru, že s asynchronními metodami nelze za daným bodem pokračovat, dokud nebude dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.

  Pozastavení asynchronní metody ve `Await` výrazu nepředstavuje výstup z metody `Finally` a bloky nespustí.

- Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.

Asynchronní metoda obvykle obsahuje jeden nebo `Await` více výskytů operátoru, ale absence výrazů `Await` nezpůsobí chybu kompilátoru. Pokud asynchronní metoda nepoužívá `Await` operátor k označení bodu pozastavení, metoda se provede jako synchronní `Async` metoda, navzdory modifikátoru. Kompilátor u takových metod zahlásí upozornění.

`Async`a `Await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:

- [Asynchronní](../../../../visual-basic/language-reference/modifiers/async.md)
- [Čekat operátora](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a>Návratové typy a parametry

V programování rozhraní .NET Framework asynchronní <xref:System.Threading.Tasks.Task> metoda obvykle vrací nebo [Task(Of TResult)](xref:System.Threading.Tasks.Task%601). Uvnitř asynchronní metody `Await` operátor je použita na úlohu, která je vrácena z volání do jiné asynchronní metody.

[Úkol(TResult)](xref:System.Threading.Tasks.Task%601) zadáte jako návratový typ, pokud metoda obsahuje [Return](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, `TResult`který určuje operand typu .

Použijete `Task` jako návratový typ, pokud metoda nemá žádný příkaz return nebo má příkaz return, který nevrací operand.

Následující příklad ukazuje, jak deklarovat a volat metodu, <xref:System.Threading.Tasks.Task>která vrací [Task(Of TResult)](xref:System.Threading.Tasks.Task%601) nebo :

```vb
' Signature specifies Task(Of Integer)
Async Function TaskOfTResult_MethodAsync() As Task(Of Integer)

    Dim hours As Integer
    ' . . .
    ' Return statement specifies an integer result.
    Return hours
End Function

' Calls to TaskOfTResult_MethodAsync
Dim returnedTaskTResult As Task(Of Integer) = TaskOfTResult_MethodAsync()
Dim intResult As Integer = Await returnedTaskTResult
' or, in a single statement
Dim intResult As Integer = Await TaskOfTResult_MethodAsync()

' Signature specifies Task
Async Function Task_MethodAsync() As Task

    ' . . .
    ' The method has no return statement.
End Function

' Calls to Task_MethodAsync
Task returnedTask = Task_MethodAsync()
Await returnedTask
' or, in a single statement
Await Task_MethodAsync()
```

Každá vrácená úloha představuje probíhající práci. Úloha zapouzdřuje informace o stavu asynchronního procesu a posléze buď konečný výsledek z procesu, nebo výjimku, kterou proces vyvolá v případě neúspěchu.

Asynchronní metoda může `Sub` být také metoda. Tento návratový typ se používá především k definování obslužné rutiny událostí, kde je vyžadován návratový typ. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.

Asynchronní metoda, která `Sub` je procedura nelze čekat a volající nemůže zachytit žádné výjimky, které metoda vyvolá.

Asynchronní metoda nemůže deklarovat [Parametry ByRef,](../../../../visual-basic/language-reference/modifiers/byref.md) ale metoda může volat metody, které mají takové parametry.

Další informace a příklady naleznete [v tématu Asynchronní návratové typy (Visual Basic)](async-return-types.md). Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v [tématu Try... Chytit... Finally prohlášení](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Asynchronní rozhraní API v programování prostředí Windows Runtime mají jeden z následujících návratových typů, které jsou podobné úlohám:

- [IAsyncOperation(Of TResult)](xref:Windows.Foundation.IAsyncOperation%601), který odpovídá [Task(Of TResult)](xref:System.Threading.Tasks.Task%601)
- <xref:Windows.Foundation.IAsyncAction>, což odpovídá<xref:System.Threading.Tasks.Task>
- [IAsyncActionWithProgress(Z TProgress)](xref:Windows.Foundation.IAsyncActionWithProgress%601)
- [IAsyncOperationWithProgress(Of TResult, TProgress)](xref:Windows.Foundation.IAsyncOperationWithProgress%602)

Další informace a příklad naleznete v [tématu Volání asynchronních api v jazyce C# nebo visual basicu](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a>Konvence

Podle konvence připojíte "Async" k názvům metod, které mají `Async` modifikátor.

Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například byste neměli přejmenovat běžné obslužné rutiny událostí, například `Button1_Click`.

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a>Příbuzná témata a ukázky (Visual Studio)

|Nadpis|Popis|Ukázka|
|-----------|-----------------|------------|
|[Návod: Přístup k webu pomocí asynchronní a čeká (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Ukázka asynchroniky: Přístup k webovému návodu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Postup: Rozšíření asynchronního návodu pomocí task.whenall (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> k předchozímu návodu. Použití spustí `WhenAll` všechny soubory ke stažení ve stejnou dobu.||
|[Postup: Vytvoření více webových požadavků paralelně pomocí asynchronní a čeká (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Ukázka asynchroniky: Souběžně provádět více webových požadavků](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Asynchronní návratové typy (Visual Basic)](async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||
|[Tok řízení v asynchronních programech (Visual Basic)](control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Ukázka asynchroniky: Tok řízení v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Jemné doladění asynchronní aplikace (Visual Basic)](fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> - [Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Zrušit asynchronní úkoly po určité době (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [Zrušit zbývající asynchronní úlohy po dokončení jedné (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Spuštění více asynchronních úloh a jejich zpracování po dokončení (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Asynchronní ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zpracování reentrancy v asynchronních aplikacích (Visual Basic)](handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je spuštěna aktivní asynchronní operace.||
|[WhenAny: Přemostění mezi rozhraním .NET Framework a prostředím Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Ukazuje, jak přemostit mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v prostředí Windows Runtime, takže můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> s metodou Prostředí Windows Runtime.|[Ukázka asynchronní: Přemostění mezi rozhraními .NET a prostředím Windows Runtime (AsTask a WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak přemostit mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v prostředí Windows Runtime, takže můžete použít <xref:System.Threading.CancellationTokenSource> s metodou Prostředí Windows Runtime.|[Ukázka asynchronní: Přemostění mezi rozhraními .NET a prostředím Windows Runtime (AsTask & Zrušení)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Použití aplikace Async pro přístup k souborům (Visual Basic)](using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Vzor je založen <xref:System.Threading.Tasks.Task> na a [Task(Of TResult)](xref:System.Threading.Tasks.Task%601) typy.||
|[Asynchronní videa na kanálu 9](https://channel9.msdn.com/search?term=async+&type=All)|Poskytuje odkazy na různá videa o asynchronním programování.||

## <a name="complete-example"></a><a name="BKMK_CompleteExample"></a>Kompletní příklad

Následující kód je mainwindow.xaml.vb soubor z windows presentation foundation (WPF) aplikace, která popisuje toto téma. Ukázku si můžete stáhnout z [ukázky Async: Příklad z "Asynchronní programování s async a Await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

[!code-vb[async](~/samples/snippets/standard/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Viz také

- [Čekat operátora](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Asynchronní](../../../../visual-basic/language-reference/modifiers/async.md)
