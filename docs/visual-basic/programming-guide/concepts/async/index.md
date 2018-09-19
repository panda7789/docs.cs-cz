---
title: Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: 0c4ee6d7bd6d0b160d5f2ed0ab0021601b3aced2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991600"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)
Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.  
  
 Visual Studio 2012 zavádí zjednodušený postup pro asynchronní programování, který využívá asynchronní podpory v rozhraní .NET Framework 4.5 a vyšší stejně jako v prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.  
  
 Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Asynchronní programování zlepšuje odezvu  
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
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Je snazší psát asynchronní metody  
 [Asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) a [Await](../../../../visual-basic/language-reference/modifiers/async.md) základem asynchronního programování jsou klíčová slova v jazyce Visual Basic. Pomocí těchto dvou klíčových slov můžete použít zdroje v rozhraní .NET Framework nebo prostředí Windows Runtime k vytvoření asynchronní metody téměř stejně snadno, jako vytváříte synchronní metody. Asynchronní metody, které definujete pomocí `Async` a `Await` jsou označovány jako asynchronní metody.  
  
 Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé. Komentáře volají funkce, které jste přidali při tvorbě asynchronie.  
  
 Úplný ukázkový soubor Windows Presentation Foundation (WPF) na konci tohoto tématu můžete najít a si můžete stáhnout ukázku z [asynchronní vzorek: příklad z "Asynchronní programování s Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```vb  
' Three things to note in the signature:  
'  - The method has an Async modifier.   
'  - The return type is Task or Task(Of T). (See "Return Types" section.)  
'    Here, it is Task(Of Integer) because the return statement returns an integer.  
'  - The method name ends in "Async."  
Async Function AccessTheWebAsync() As Task(Of Integer)  
  
    ' You need to add a reference to System.Net.Http to declare client.  
    Dim client As HttpClient = New HttpClient()  
  
    ' GetStringAsync returns a Task(Of String). That means that when you await the  
    ' task you'll get a string (urlContents).  
    Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
    ' You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork()  
  
    ' The Await operator suspends AccessTheWebAsync.  
    '  - AccessTheWebAsync can't continue until getStringTask is complete.  
    '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    '  - Control resumes here when getStringTask is complete.   
    '  - The Await operator then retrieves the string result from getStringTask.  
    Dim urlContents As String = Await getStringTask  
  
    ' The return statement specifies an integer result.  
    ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    Return urlContents.Length  
End Function  
```  
  
 Pokud `AccessTheWebAsync` nemá žádnou práci, kterou lze provádět mezi voláním `GetStringAsync` a čekáním na její dokončení, můžete zjednodušit kód voláním a čekáním následujícím jediným příkazem.  
  
```vb  
Dim urlContents As String = Await client.GetStringAsync()  
```  
  
 Následující charakteristiky představují shrnutí, co dělá předchozí příklad asynchronní metodou.  
  
-   Podpis metody zahrnuje `Async` modifikátor.  
  
-   Název asynchronní metody končí podle konvence příponou „Async“.  
  
-   Návratový typ je jeden z následujících typů:  
  
    -   <xref:System.Threading.Tasks.Task%601> Pokud vaše metoda disponuje návratovým příkazem, ve kterém je operand typu TResult.  
  
    -   <xref:System.Threading.Tasks.Task> Pokud vaše metoda nemá návratový stav nebo vrátila příkaz bez operandu.  
  
    -   [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) Pokud píšete asynchronní obslužnou rutinu události.  
  
     Další informace naleznete v části „Návratové typy a parametry“ dále v tomto tématu.  
  
-   Metoda obvykle zahrnuje nejméně jeden očekávaný výraz, který označuje bod, kde metoda nemůže pokračovat, dokud očekávaná asynchronní operace nebude dokončena. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.  
  
 V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.  
  
 Další informace o asynchronii v předchozích verzích rozhraní .NET Framework najdete v tématu [TPL a tradiční rozhraní .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co se děje v asynchronní metodě  
 Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem.  
  
 ![Trasování aplikace asynchronní](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Čísla v diagramu odpovídají následujícím krokům.  
  
1.  Obslužná rutina události zavolá a očekává `AccessTheWebAsync` asynchronní metody.  
  
2.  `AccessTheWebAsync` vytvoří <xref:System.Net.Http.HttpClient> instance a volání <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronní metody ke stahování obsahu webu jako řetězec.  
  
3.  Něco se stane v `GetStringAsync` , která způsobí zastavení průběhu. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. Chcete-li zabránit zablokování, `GetStringAsync` vrací řízení volajícímu, `AccessTheWebAsync`.  
  
     `GetStringAsync` Vrátí <xref:System.Threading.Tasks.Task%601> tam, kde TResult je řetězec, a `AccessTheWebAsync` přiřadí úlohu `getStringTask` proměnné. Úloha představuje trvalý proces pro volání `GetStringAsync`, se závazkem vyrábět aktuální řetězcovou hodnotu po dokončení práce.  
  
4.  Protože `getStringTask` ještě nebyla očekávána, metoda `AccessTheWebAsync` můžete pokračovat v další práci, která nezávisí na konečném výsledku `GetStringAsync`. Daná práce je reprezentována voláním synchronní metody `DoIndependentWork`.  
  
5.  `DoIndependentWork` je synchronní metoda, která provede svou práci a vrátí výsledek volajícímu.  
  
6.  `AccessTheWebAsync` nemá dostatek práce, kterou můžete provést bez výsledku z `getStringTask`. `AccessTheWebAsync` dále potřebuje vypočítat a vrátit délku staženého řetězce, ale metoda nemůže hodnotu vypočítat, dokud se tato metoda má řetězec.  
  
     Proto `AccessTheWebAsync` používá operátor await k pozastavení jeho průběhu a výnosu z ovládacího prvku v metodě, která volá `AccessTheWebAsync`. `AccessTheWebAsync` Vrátí `Task<int>` (`Task(Of Integer)` v jazyce Visual Basic) na volajícího. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.  
  
    > [!NOTE]
    >  Pokud `GetStringAsync` (a tedy `getStringTask`) dokončena dříve, než `AccessTheWebAsync` čeká na jeho ovládací prvek zůstane v `AccessTheWebAsync`. Prostředky na zastavení a vrácení k `AccessTheWebAsync` by byly ztraceny, pokud volaný asynchronní proces (`getStringTask`) již dokončen a AccessTheWebSync nebude muset čekat na konečný výsledek.  
  
     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může provádět další operace, které nejsou závislé na výsledku `AccessTheWebAsync` před čeká na výsledek, nebo volající může použít funkci await okamžitě.   Obslužná rutina události čeká na všesměrově `AccessTheWebAsync`, a `AccessTheWebAsync` čeká `GetStringAsync`.  
  
7.  `GetStringAsync` dokončí a vytvoří výsledek řetězce. Výsledek řetězce není vrácený voláním na `GetStringAsync` způsobem, který by se dalo očekávat. (Mějte na paměti, že metoda již vrátila úlohu v kroku 3.) Místo toho je výsledek řetězce uložen v úkolu, který představuje dokončení metody, `getStringTask`. Operátor await načítá výsledek z `getStringTask`. Přiřazovací příkaz přiřadí načtený výsledek do `urlContents`.  
  
8.  Když `AccessTheWebAsync` má řetězec výsledek, metoda může vypočítat délku řetězce. Pak je práce `AccessTheWebAsync` kompletní a můžete pokračovat v obslužné rutině události čekání. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.  
  
 Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.  
  
 Další informace o toku řízení naleznete v tématu [tok řízení v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Rozhraní API asynchronní metody  
 Možná se ptáte kde nalézt metody jako `GetStringAsync` , které podporují asynchronní programování. Rozhraní .NET Framework 4.5 nebo novější obsahuje mnoho členů, které pracují s `Async` a `Await`. Tyto členy můžete rozpoznat podle přípony "Async", která je připojena k názvu členu a návratovému typu <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Například `System.IO.Stream` třída obsahuje metody, jako například <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, a <xref:System.IO.Stream.WriteAsync%2A> vedle synchronních metod <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, a <xref:System.IO.Stream.Write%2A>.  
  
 Modul Runtime Windows také obsahuje mnoho metod, které můžete použít s `Async` a `Await` v aplikacích pro Windows. Další informace a příklad metody naleznete v tématu [volání asynchronního rozhraní API v jazyce C# nebo Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [asynchronní programování (aplikace pro Windows Runtime)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)), a [WhenAny: přemostění rozhraní .NET Framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).  
  
##  <a name="BKMK_Threads"></a> Vlákna  
 Asynchronní metody mají být neblokující operace. `Await` Výrazu v asynchronní metodě nebude blokovat aktuální vlákno, zatímco očekávaná úloha běží. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.  
  
 `Async` a `Await` klíčová slova nezpůsobí další vlákna, který se má vytvořit. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> pro přesun práce vázané na procesor do vlákna na pozadí, ale na pozadí vlákno nepomůže s procesem, který pouze čeká na zpřístupnění výsledků.  
  
 Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Konkrétně tento přístup je obecně lepší než <xref:System.ComponentModel.BackgroundWorker> pro vstupně-výstupní operace vzhledem k tomu, že kód je jednodušší a nemusíte pro ochranu proti na konflikty časování. V kombinaci s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, je asynchronní programování lepší než <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor protože asynchronní programování odděluje koordinaci podrobností od spouštění kódu z práce, která `Task.Run` přenosů do fondu vláken.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async a operátoru Await  
 Pokud určíte, že metoda je metodou asynchronní pomocí [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor, povolíte tím následující dvě možnosti.  
  
-   Označená asynchronní metoda může použít [Await](../../../../visual-basic/language-reference/operators/await-operator.md) k určení místa pozastavení možnost. Operátor await sděluje kompilátoru, že s asynchronními metodami nelze za daným bodem pokračovat, dokud nebude dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.  
  
     Pozastavení asynchronní metody na `Await` výraz nebude představovat východ z metody, a `Finally` bloky při spuštění.  
  
-   Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.  
  
 Asynchronní metoda obvykle obsahuje jeden nebo více výskytů `Await` operátoru, ale absence `Await` výrazy nezpůsobí chybu kompilátoru. Pokud asynchronní metoda nepoužívá `Await` operátor označení bodu pozastavení, metoda provede jako synchronní metoda funguje, bez ohledu `Async` modifikátor. Kompilátor u takových metod zahlásí upozornění.  
  
 `Async` a `Await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:  
  
-   [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Typy vrácených hodnot a parametrů  
 Při programování rozhraní .NET Framework asynchronní metoda obvykle vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. V asynchronní metodě `Await` operátor je použít pro úlohu, která je vrácena z volání do jiné asynchronní metody.  
  
 Zadáte <xref:System.Threading.Tasks.Task%601> jako návratový typ, pokud metoda obsahuje [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který určuje typ operandu `TResult`.  
  
 Použijete `Task` jako návratový typ, pokud metoda nemá žádný návratový příkaz nebo má návratový příkaz, který nevrací operand.  
  
 Následující příklad ukazuje, jak deklarovat a volat metodu, která se vrátí <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.  
  
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
  
 Asynchronní metoda může být také `Sub` metody. Tento návratový typ se používá především k definování obslužných rutin událostí, kde je požadován typ vrácené. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.  
  
 Asynchronní metoda, která `Sub` procedura nemůže být očekávána a volající nemůže zachytit žádné výjimky, které metoda vyvolá.  
  
 Asynchronní metoda nemůže deklarovat [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametry, ale metoda může volat metody, které mají tyto parametry.  
  
 Další informace a příklady najdete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md). Další informace o tom, jak zachytávat výjimky v asynchronních metodách, naleznete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Asynchronní rozhraní API v programování v prostředí Windows Runtime některou z následujících návratových typů, které jsou podobné úkolům:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, který odpovídá <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, který odpovídá <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
  
 Další informace a příklad najdete v tématu [volání asynchronního rozhraní API v jazyce C# nebo Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).  
  
##  <a name="BKMK_NamingConvention"></a> Zásady vytváření názvů  
 Podle úmluvy připojte "Async" názvy metod, které mají `Async` modifikátor.  
  
 Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například byste neměli přejmenovat běžné obslužné rutiny událostí, jako například `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Související témata a ukázky (Visual Studio)  
  
|Název|Popis|Ukázka|  
|-----------|-----------------|------------|  
|[Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Asynchronní vzorek: Přístup k webovému návodu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> k předchozímu návodu. Použití `WhenAll` zahájí všechna stahování současně.||  
|[Postupy: paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Asynchronní vzorek: Paralelní provádění vícenásobných webových](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||  
|[Tok řízení v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Asynchronní vzorek: Tok řízení v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Doladění aplikace s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> -   [Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Zrušení asynchronních úloh po určitou dobu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Zrušení zbývajících asynchronních úloh po jedné z nich kompletní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je aktivní asynchronní operace restartována po jejím spuštění.||  
|[WhenAny: Přemostění rozhraní .NET Framework a prostředí Windows Runtime](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|Ukazuje, jak propojit typy úloh v rozhraní .NET Framework a iasyncoperations v rámci [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby vám <xref:System.Threading.Tasks.Task.WhenAny%2A> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Asynchronní vzorek: Přemostění mezi rozhraním .NET a prostředí Windows Runtime (AsTask a WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|  
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak propojit typy úloh v rozhraní .NET Framework a iasyncoperations v rámci [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby vám <xref:System.Threading.CancellationTokenSource> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Asynchronní vzorek: Přemostění mezi rozhraním .NET a prostředí Windows Runtime (AsTask a zrušení)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Použití modifikátoru Async pro přístup k souborům (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||  
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Vzorek je založen na <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> typy.||  
|[Videa o asynchronním programování na kanálu Channel 9](https://channel9.msdn.com/search?term=async+&type=All)|Poskytuje odkazy na různá videa o asynchronním programování.||  
  
##  <a name="BKMK_CompleteExample"></a> Kompletní příklad  
 Následující kód je soubor MainWindow.xaml.vb z aplikace Windows Presentation Foundation (WPF), která toto téma popisuje. Můžete stáhnout ukázku z [asynchronní vzorek: příklad z "Asynchronní programování s Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```vb  
' Add an Imports statement and a reference for System.Net.Http  
Imports System.Net.Http  
  
Class MainWindow  
  
    ' Mark the event handler with async so you can use Await in it.  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Call and await separately.  
        'Task<int> getLengthTask = AccessTheWebAsync();  
        '' You can do independent work here.  
        'int contentLength = await getLengthTask;  
  
        Dim contentLength As Integer = Await AccessTheWebAsync()  
  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
    End Sub  
  
    ' Three things to note in the signature:  
    '  - The method has an Async modifier.   
    '  - The return type is Task or Task(Of T). (See "Return Types" section.)  
    '    Here, it is Task(Of Integer) because the return statement returns an integer.  
    '  - The method name ends in "Async."  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' You need to add a reference to System.Net.Http to declare client.  
        Dim client As HttpClient = New HttpClient()  
  
        ' GetStringAsync returns a Task(Of String). That means that when you await the  
        ' task you'll get a string (urlContents).  
        Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' You can do work here that doesn't rely on the string from GetStringAsync.  
        DoIndependentWork()  
  
        ' The Await operator suspends AccessTheWebAsync.  
        '  - AccessTheWebAsync can't continue until getStringTask is complete.  
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
        '  - Control resumes here when getStringTask is complete.   
        '  - The Await operator then retrieves the string result from getStringTask.  
        Dim urlContents As String = Await getStringTask  
  
        ' The return statement specifies an integer result.  
        ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
        Return urlContents.Length  
    End Function  
  
    Sub DoIndependentWork()  
        ResultsTextBox.Text &= "Working . . . . . . ." & vbCrLf  
    End Sub  
End Class  
  
' Sample Output:  
  
' Working . . . . . . .  
  
' Length of the downloaded string: 41763.  
```  
  
## <a name="see-also"></a>Viz také:

- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)  
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
