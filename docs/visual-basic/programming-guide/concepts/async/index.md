---
title: Asynchronní programování pomocí modifikátoru Async a operátoru Await
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: ff028b3cbc00d54d8caf9e727cc487f96505beea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346691"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)

Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.

Visual Studio 2012 představilo zjednodušený přístup, asynchronní programování, které využívá asynchronní podporu v .NET Framework 4,5 a vyšší a také v prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.

Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.

## <a name="BKMK_WhentoUseAsynchrony"></a>Asynchronní funkce vylepšuje rychlost odezvy.

Asynchronie je nezbytná pro aktivity, které mohou potenciálně blokovat, například pokud vaše aplikace přistupuje na web. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková činnost blokována v rámci synchronního procesu, musí čekat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.

Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z .NET Framework 4,5 a prostředí Windows Runtime obsahují metody, které podporují asynchronní programování.

|Oblast aplikace|Podpora rozhraní API, která obsahují asynchronní metody|
|----------------------|------------------------------------------------|
|Webový přístup|<xref:System.Net.Http.HttpClient><xref:Windows.Web.Syndication.SyndicationClient>|
|Práce se soubory|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader><xref:System.Xml.XmlReader>|
|Práce s obrázky|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder><xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programování WCF|[Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|
|||

Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.

Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.

Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Asynchronní metody se snáze zapisují

Klíčová slova [Async](../../../../visual-basic/language-reference/modifiers/async.md) a [await](../../../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic jsou srdcem asynchronního programování. Pomocí těchto dvou klíčových slov můžete použít prostředky v .NET Framework nebo prostředí Windows Runtime k vytvoření asynchronní metody téměř stejně snadno, jako vytváříte synchronní metodu. Asynchronní metody, které definujete pomocí `Async` a `Await` jsou označovány jako asynchronní metody.

Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé. Komentáře volají funkce, které jste přidali při tvorbě asynchronie.

Na konci tohoto tématu můžete najít úplný ukázkový soubor Windows Presentation Foundation (WPF) a můžete si stáhnout ukázku z [Async Sample: příklad z tématu "asynchronní programování s Async a await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

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

Pokud `AccessTheWebAsync` nemá žádnou práci, kterou může provést mezi voláním `GetStringAsync` a čekáním na jeho dokončení, můžete zjednodušit kód voláním a čekáním v následujícím jediném příkazu.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

Následující charakteristiky shrnují, co dělá předchozí příklad asynchronní metodou:

- Signatura metody obsahuje modifikátor `Async`.
- Název asynchronní metody končí podle konvence příponou „Async“.
- Návratový typ je jeden z následujících typů:

  - <xref:System.Threading.Tasks.Task%601>, zda má vaše metoda návratový příkaz, ve kterém je operand typu TResult.
  - <xref:System.Threading.Tasks.Task>, pokud vaše metoda nemá návratový příkaz nebo má návratový příkaz bez operandu.
  - [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , pokud píšete asynchronní obslužnou rutinu události.

  Další informace naleznete v části „Návratové typy a parametry“ dále v tomto tématu.

- Metoda obvykle zahrnuje nejméně jeden očekávaný výraz, který označuje bod, kde metoda nemůže pokračovat, dokud očekávaná asynchronní operace nebude dokončena. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.

V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.

Další informace o asynchronii v předchozích verzích .NET Framework naleznete v tématu [TPL a tradiční .NET Framework asynchronní programování](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co se stane v asynchronní metodě

Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem:

![Diagram, který zobrazuje trasování asynchronního programu.](./media/index/navigation-trace-async-program.png)

Čísla v diagramu odpovídají následujícím krokům:

1. Obslužná rutina události volá a očekává asynchronní metodu `AccessTheWebAsync`.

2. `AccessTheWebAsync` vytvoří instanci <xref:System.Net.Http.HttpClient> a zavolá <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronní metodu pro stažení obsahu webu jako řetězce.

3. Něco se stane v `GetStringAsync`, které pozastaví jeho průběh. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. Aby nedocházelo k blokování prostředků, `GetStringAsync` poskytne řízení volajícímu, `AccessTheWebAsync`.

     `GetStringAsync` vrátí <xref:System.Threading.Tasks.Task%601>, kde TResult je řetězec, a `AccessTheWebAsync` přiřadí úkol proměnné `getStringTask`. Úkol představuje nepřetržitý proces pro volání `GetStringAsync`a závazek vytvořit skutečnou řetězcovou hodnotu po dokončení práce.

4. Vzhledem k tomu, že `getStringTask` ještě nečekala, `AccessTheWebAsync` může pokračovat v jiné práci, která nezávisí na konečném výsledku z `GetStringAsync`. Tato práce je reprezentována voláním synchronní metody `DoIndependentWork`.

5. `DoIndependentWork` je synchronní metoda, která provede svou práci a vrátí jejímu volajícímu.

6. `AccessTheWebAsync` vyčerpala práci, kterou může provádět bez výsledku z `getStringTask`. `AccessTheWebAsync` další chce vypočítat a vrátit délku staženého řetězce, ale metoda nemůže tuto hodnotu vypočítat, dokud metoda nemá řetězec.

     Proto `AccessTheWebAsync` pomocí operátoru await pozastaví svůj průběh a vrátí řízení metodě, která se nazývá `AccessTheWebAsync`. `AccessTheWebAsync` vrátí volajícímu hodnotu `Task<int>` (`Task(Of Integer)` v Visual Basic). Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.

    > [!NOTE]
    > Pokud je `GetStringAsync` (a proto `getStringTask`) dokončeno před tím, než to `AccessTheWebAsync` očekává, řízení zůstane v `AccessTheWebAsync`. Náklady na pozastavení a návrat do `AccessTheWebAsync` by byly nevyužité, pokud se pojmenovaný asynchronní proces (`getStringTask`) už dokončil a AccessTheWebSync nebude nemusí čekat na konečný výsledek.

     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může provést další práci, která nezávisí na výsledku z `AccessTheWebAsync` před čekáním na výsledek nebo volající může očekávat okamžitě.   Obslužná rutina události čeká na `AccessTheWebAsync`a `AccessTheWebAsync` čeká na `GetStringAsync`.

7. `GetStringAsync` dokončí a vytvoří výsledek řetězce. Výsledek řetězce není vrácen voláním `GetStringAsync` způsobem, který byste mohli očekávat. (Nezapomeňte, že metoda již vrátila úlohu v kroku 3.) Místo toho je výsledek řetězce uložen v úkolu, který představuje dokončení metody, `getStringTask`. Operátor await načte výsledek z `getStringTask`. Příkaz přiřazení přiřadí načtený výsledek do `urlContents`.

8. Pokud má `AccessTheWebAsync` výsledek řetězce, metoda může vypočítat délku řetězce. Pak je dokončena i práce `AccessTheWebAsync` a může pokračovat obslužná rutina čekající události. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.

Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.

Další informace o toku řízení naleznete v tématu [Flow Control in Async Programs (Visual Basic)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>Asynchronní metody rozhraní API

Možná vás zajímá, kde najít metody jako `GetStringAsync`, které podporují asynchronní programování. .NET Framework 4,5 nebo vyšší obsahuje mnoho členů, kteří pracují s `Async` a `Await`. Tyto členy můžete rozpoznat pomocí přípony "Async", která je připojena k názvu člena, a návratovým typem <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Například třída `System.IO.Stream` obsahuje metody jako <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>a <xref:System.IO.Stream.WriteAsync%2A> spolu se synchronními metodami <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>a <xref:System.IO.Stream.Write%2A>.

Prostředí Windows Runtime také obsahuje řadu metod, které můžete použít s `Async` a `Await` v aplikacích pro Windows. Další informace a příklady metod naleznete v tématu [volání asynchronních rozhraní C# api v nebo Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [asynchronní programování (prostředí Windows Runtime aplikace)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))a [WhenAny: přemostění mezi .NET Framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).

## <a name="BKMK_Threads"></a>Vláken

Asynchronní metody mají být neblokující operace. Výraz `Await` v asynchronní metodě neblokuje aktuální vlákno, zatímco je spuštěn očekávaný úkol. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.

Klíčová slova `Async` a `Await` nezpůsobí vytvoření dalších vláken. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> pro přesun práce vázané na procesor do vlákna na pozadí, ale vlákno na pozadí nepomůže s procesem, který právě čeká na zpřístupnění výsledků.

Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Konkrétně tento přístup je lepší než <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na vstupně-výstupní operace, protože kód je jednodušší a nemusíte se chránit před konflikty časování. V kombinaci s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>je asynchronní programování lepší než <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor, protože asynchronní programování odděluje koordinační informace o spuštění kódu z práce, která `Task.Run` přenáší do fondu.

## <a name="BKMK_AsyncandAwait"></a>Async a await

Pokud určíte, že metoda je asynchronní metodou pomocí modifikátoru [Async](../../../../visual-basic/language-reference/modifiers/async.md) , povolíte následující dvě možnosti.

- Označená asynchronní metoda může použít [operátor await](../../../../visual-basic/language-reference/operators/await-operator.md) k určení bodů zavěšení. Operátor await sděluje kompilátoru, že s asynchronními metodami nelze za daným bodem pokračovat, dokud nebude dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.

  Pozastavení asynchronní metody ve výrazu `Await` nepředstavuje příkaz exit z metody a bloky `Finally` neběží.

- Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.

Asynchronní metoda obvykle obsahuje jeden nebo více výskytů operátoru `Await`, ale absence `Await` výrazy nezpůsobí chybu kompilátoru. Pokud asynchronní metoda nepoužívá operátor `Await` k označení bodu pozastavení, metoda se spustí jako synchronní metoda bez ohledu na modifikátor `Async`. Kompilátor u takových metod zahlásí upozornění.

`Async` a `Await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:

- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Návratové typy a parametry

V .NET Framework programování, asynchronní metoda obvykle vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. V rámci asynchronní metody je operátor `Await` použit pro úkol, který je vrácen z volání jiné asynchronní metody.

Zadejte <xref:System.Threading.Tasks.Task%601> jako návratový typ, pokud metoda obsahuje příkaz [return](../../../../visual-basic/language-reference/statements/return-statement.md) , který určuje operand typu `TResult`.

Použijte `Task` jako návratový typ, pokud metoda nemá žádný návratový příkaz nebo má návratový příkaz, který nevrací operand.

Následující příklad ukazuje, jak deklarovat a volat metodu, která vrací <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>:

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

Asynchronní metoda může být také metoda `Sub`. Tento návratový typ slouží primárně k definování obslužných rutin událostí, kde je požadován návratový typ. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.

Asynchronní metoda, která je `Sub` proceduru, nemůže být očekávána a volající nemůže zachytit žádné výjimky, které metoda vyvolá.

Asynchronní metoda nemůže deklarovat parametry [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) , ale metoda může volat metody, které mají tyto parametry.

Další informace a příklady naleznete v tématu [Async Return Types (Visual Basic)](async-return-types.md). Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Asynchronní rozhraní API v prostředí Windows Runtime programování mají jeden z následujících návratových typů, které jsou podobné úlohám:

- <xref:Windows.Foundation.IAsyncOperation%601>, který odpovídá <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, který odpovídá <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

Další informace a příklady naleznete [v tématu Calling Asynchronous API in C# nebo Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="BKMK_NamingConvention"></a>Konvence pojmenování

Podle konvence připojíte "Async" k názvům metod, které mají modifikátor `Async`.

Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například byste neměli přejmenovat běžné obslužné rutiny událostí, jako je například `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a>Související témata a ukázky (Visual Studio)

|Název|Popis|Ukázka|
|-----------|-----------------|------------|
|[Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Asynchronní Ukázka: přístup k webovému návodu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> k předchozímu návodu. Použití `WhenAll` spouští všechna stahování ve stejnou dobu.||
|[Postupy: paralelní provádění více webových požadavků pomocí modifikátoru Async a operátoru Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Asynchronní vzorek: paralelní provádění více webových požadavků](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Asynchronní návratové typy (Visual Basic)](async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||
|[Řízení toku v asynchronních programech (Visual Basic)](control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Asynchronní vzorek: tok řízení v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Vyladění aplikace v asynchronním prostředí (Visual Basic)](fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> - [zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [zrušení asynchronních úloh po určitém časovém intervalu (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [zrušení zbývajících asynchronních úloh po dokončení jedné z nich (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [spustit více asynchronních úloh a zpracovat je po dokončení (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zpracování Vícenásobný přístup v asynchronních aplikacích (Visual Basic)](handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je aktivní asynchronní operace restartována v době, kdy běží.||
|[WhenAny: přemostění mezi .NET Framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Ukazuje, jak přemostění mezi typy úloh v .NET Framework a IAsyncOperations v prostředí Windows Runtime, abyste mohli <xref:System.Threading.Tasks.Task.WhenAny%2A> používat s metodou prostředí Windows Runtime.|[Asynchronní vzorek: přemostění mezi rozhraním .NET a prostředí Windows Runtime (AsTask a WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak přemostění mezi typy úloh v .NET Framework a IAsyncOperations v prostředí Windows Runtime, abyste mohli <xref:System.Threading.CancellationTokenSource> používat s metodou prostředí Windows Runtime.|[Asynchronní vzorek: přemostění mezi rozhraním .NET a prostředí Windows Runtime (zrušení & AsTask)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Použití Async pro přístup k souborům (Visual Basic)](using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Vzor je založen na <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> typech.||
|[Asynchronní videa na Channel 9](https://channel9.msdn.com/search?term=async+&type=All)|Poskytuje odkazy na různá videa o asynchronním programování.||

## <a name="BKMK_CompleteExample"></a>Kompletní příklad

Následující kód je soubor MainWindow. XAML. vb z aplikace Windows Presentation Foundation (WPF), kterou popisuje toto téma. Ukázku si můžete stáhnout z [části Async Sample: příklad z "asynchronní programování s Async a await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

[!code-vb[async](~/samples/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Viz také:

- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
