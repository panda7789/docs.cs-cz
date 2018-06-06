---
title: Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: 5a0d2d40b815037e6eb3ed47c500c135ad116aaf
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753523"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)
Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.  
  
 Visual Studio 2012 zavedly zjednodušenou metodu, asynchronní programování, které využívá asynchronní podpora v rozhraní .NET Framework 4.5 a vyšší stejně jako v prostředí Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.  
  
 Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Asynchronní zlepšuje odezvu  
 Asynchronie je nezbytná pro aktivity, které mohou potenciálně blokovat, například pokud vaše aplikace přistupuje na web. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková činnost blokována v rámci synchronního procesu, musí čekat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.  
  
 Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. Uvedená rozhraní API z rozhraní .NET Framework 4.5 a prostředí Windows Runtime obsahovat metody, které podporují asynchronní programování.  
  
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
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Asynchronní metody jsou psát  
 [Asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) a [Await](../../../../visual-basic/language-reference/modifiers/async.md) klíčová slova v jazyce Visual Basic jsou srdcem asynchronní programování. Pomocí těchto dvou klíčová slova, můžete prostředky v rozhraní .NET Framework nebo prostředí Windows Runtime téměř jako snadno, jako je vytváření synchronní metoda vytvoření asynchronní metodu. Asynchronní metody, které definujete pomocí `Async` a `Await` se označují jako asynchronní metody.  
  
 Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé. Komentáře volají funkce, které jste přidali při tvorbě asynchronie.  
  
 Úplný příklad souboru Windows Presentation Foundation (WPF) na konci tohoto tématu můžete najít a si můžete stáhnout ukázkový z [asynchronní ukázka: příklad z "Asynchronní programování s Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
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
  
 Pokud `AccessTheWebAsync` nemá veškerou práci, kterou můžete provést mezi voláním `GetStringAsync` a čeká na její dokončení, můžete zjednodušit kód voláním a čeká na v následující jeden příkaz.  
  
```vb  
Dim urlContents As String = Await client.GetStringAsync()  
```  
  
 Následující charakteristiky představují shrnutí, co dělá předchozí příklad asynchronní metodou.  
  
-   Podpis metody zahrnuje `Async` modifikátor.  
  
-   Název asynchronní metody končí podle konvence příponou „Async“.  
  
-   Návratový typ je jeden z následujících typů:  
  
    -   <xref:System.Threading.Tasks.Task%601> Pokud vaše metoda má ve kterém má operand typu TResult příkaz return.  
  
    -   <xref:System.Threading.Tasks.Task> Pokud vaše metoda má žádný příkaz return nebo příkaz return s žádné operand.  
  
    -   [Sub –](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) Pokud píšete asynchronní obslužnou rutinu.  
  
     Další informace naleznete v části „Návratové typy a parametry“ dále v tomto tématu.  
  
-   Metoda obvykle zahrnuje nejméně jeden očekávaný výraz, který označuje bod, kde metoda nemůže pokračovat, dokud očekávaná asynchronní operace nebude dokončena. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.  
  
 V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.  
  
 Další informace o asynchrony v předchozích verzích rozhraní .NET Framework najdete v tématu [TPL a tradiční rozhraní .NET Framework asynchronní programování](http://msdn.microsoft.com/library/e7b31170-a156-433f-9f26-b1fc7cd1776f).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Co se stane, že v asynchronní metody  
 Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. Následující diagram vás provede procesem.  
  
 ![Sledování aplikace asynchronní](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Čísla v diagramu odpovídají následujícím krokům.  
  
1.  Volá obslužnou rutinu události a čeká `AccessTheWebAsync` asynchronní metody.  
  
2.  `AccessTheWebAsync` vytvoří <xref:System.Net.Http.HttpClient> instance a volání <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronní metody pro stažení obsahu webu, jako řetězec.  
  
3.  Něco se stane, že v `GetStringAsync` který pozastaví jejím průběhu. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. K zabránění blokování prostředky, `GetStringAsync` vypočítá ovládacího prvku do jeho volajícího `AccessTheWebAsync`.  
  
     `GetStringAsync` Vrátí <xref:System.Threading.Tasks.Task%601> kde TResult je řetězec, a `AccessTheWebAsync` přiřadí úlohu, aby `getStringTask` proměnné. Úloha představuje proces probíhající pro volání `GetStringAsync`, s závazek k vytvoření hodnotu konkrétní řetězec po dokončení práce.  
  
4.  Protože `getStringTask` nebyl ještě očekávaná `AccessTheWebAsync` můžete pokračovat v dalších práci, kterou nezávisí na konečný výsledek z `GetStringAsync`. Pracovní je reprezentována volání synchronní metoda `DoIndependentWork`.  
  
5.  `DoIndependentWork` je synchronní metoda, která nemá svou práci a vrátí jeho volajícího.  
  
6.  `AccessTheWebAsync` nemá dostatek práci, kterou můžete provést bez výsledek z `getStringTask`. `AccessTheWebAsync` Další chce výpočtu a vrátí délku stažené řetězec, ale metoda nemůže tuto hodnotu vypočítat, dokud metoda obsahuje řetězec.  
  
     Proto `AccessTheWebAsync` používá operátor await pozastavit jeho průběh a yield – ovládací prvek na metodu, která volá `AccessTheWebAsync`. `AccessTheWebAsync` Vrátí `Task<int>` (`Task(Of Integer)` v jazyce Visual Basic) na volajícího. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.  
  
    > [!NOTE]
    >  Pokud `GetStringAsync` (a proto `getStringTask`) dokončení před `AccessTheWebAsync` čeká se pořád řízení `AccessTheWebAsync`. Nákladů na pozastavení a vrátilo se do `AccessTheWebAsync` by dojít ke znehodnocení části Pokud volané asynchronní proces (`getStringTask`) je již dokončena a AccessTheWebSync nemusí čekat na konečný výsledek.  
  
     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. Volající může provádět další činnosti, které nezávisí na výsledku z `AccessTheWebAsync` před čeká na tento výsledek nebo volající může await okamžitě.   Obslužné rutiny události se čeká na `AccessTheWebAsync`, a `AccessTheWebAsync` čeká `GetStringAsync`.  
  
7.  `GetStringAsync` dokončí a vytvoří výsledek řetězec. Není řetězec výsledek vrácený volání `GetStringAsync` takovým způsobem, který by se dalo očekávat. (Nezapomeňte, že metoda již vrátí úlohu v kroku 3.) Místo toho řetězec výsledek je uložen v úloha, která představuje dokončení metody, `getStringTask`. Operátor await načte výsledek z `getStringTask`. Příkaz přiřazení přiřadí načtené výsledek, který má `urlContents`.  
  
8.  Když `AccessTheWebAsync` řetězec výsledek, obsahuje metodu můžete vypočítat délka řetězce. Potom práci při `AccessTheWebAsync` je také dokončení, a můžete pokračovat v čekání na popisovač události. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.  
  
 Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.  
  
 Další informace o toku řízení najdete v tématu [řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Rozhraní API asynchronní metody  
 Možná se ptáte kde najít metody, jako `GetStringAsync` tuto podporu asynchronní programování. Rozhraní .NET Framework 4.5 nebo vyšší obsahuje mnoho členů, které pracují s `Async` a `Await`. Tito členové poznáte podle přípony "Asynchronní", který je připojen k název člena a návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Například `System.IO.Stream` třída obsahuje metody, jako například <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, a <xref:System.IO.Stream.WriteAsync%2A> spolu s synchronních metod <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, a <xref:System.IO.Stream.Write%2A>.  
  
 Prostředí Windows Runtime také obsahuje mnoho způsobů, které můžete použít s `Async` a `Await` v aplikacích pro Windows. Další informace a metody příklad najdete v tématu [volání asynchronní rozhraní API v C# nebo Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [asynchronní programování (aplikace Windows Runtime)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)), a [WhenAny: přemostění rozhraní .NET Framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).  
  
##  <a name="BKMK_Threads"></a> Vláken  
 Asynchronní metody mají být neblokující operace. `Await` Výrazu v asynchronní metody neblokuje aktuální vlákno spuštěného awaited úloh. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.  
  
 `Async` a `Await` klíčová slova nejsou způsobit další vláken, který se má vytvořit. Asynchronní metody nevyžadují multithreading, protože asynchronní metoda není spuštěna ve vlastním vlákně. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. Můžete použít <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> přesunout vázané na procesor pracovní vlákna na pozadí, ale na pozadí nemá přístup z více vláken usnadní proces, který se právě čeká na výsledky k dispozici.  
  
 Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. Konkrétně tento přístup je lepší, než <xref:System.ComponentModel.BackgroundWorker> pro I/výstupních operací protože kód je jednodušší a nemáte ochrana proti soupeřit podmínky. V kombinaci s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, je lepší, než asynchronní programování <xref:System.ComponentModel.BackgroundWorker> pro operace vázané na procesor protože asynchronní programování odděluje podrobnosti koordinaci spuštěním kódu z práce `Task.Run` přenosů, aby zachovalo.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async a operátoru Await  
 Pokud určíte, že je metoda asynchronní metody pomocí [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor, povolte následující dvě možnosti.  
  
-   Můžete použít označený asynchronní metody [Await](../../../../visual-basic/language-reference/operators/await-operator.md) k určení bodů pozastavení. Operátor await sděluje kompilátoru, že s asynchronními metodami nelze za daným bodem pokračovat, dokud nebude dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.  
  
     Pozastavení použití asynchronní metody na `Await` výrazu není tvoří výstupu z metody, a `Finally` nespouštět bloky.  
  
-   Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.  
  
 Asynchronní metody obvykle obsahuje jeden nebo více výskytů `Await` operátor, ale chybí `Await` výrazy není způsobit chyby kompilátoru. Pokud asynchronní metody nepoužívá `Await` operátor označit bod pozastavení metoda provádí synchronní metoda stejně bez ohledu `Async` modifikátor. Kompilátor u takových metod zahlásí upozornění.  
  
 `Async` a `Await` jsou kontextová klíčová slova. Další informace a příklady naleznete v následujících tématech:  
  
-   [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Parametry a návratové typy  
 V rozhraní .NET Framework programování asynchronní metody obvykle vrátí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Uvnitř použití asynchronní metody `Await` operátor se použije pro úlohu, která je vrácena z volání jiného asynchronní metody.  
  
 Zadáte <xref:System.Threading.Tasks.Task%601> jako návratový typ, pokud obsahuje metodu [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který určuje operand typu `TResult`.  
  
 Používáte `Task` jako návratový typ, pokud metoda má žádný příkaz return nebo který nevrací operand příkaz return.  
  
 Následující příklad ukazuje, jak deklarace a volání metody, která vrací <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.  
  
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
  
 Asynchronní metody může být také `Sub` metoda. Tento návratový typ se používá hlavně k definování obslužné rutiny událostí, kdy je potřeba návratový typ. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.  
  
 Asynchronní metody to je `Sub` nemůže být očekáváno postupu a volající nelze zachytit všechny výjimky, které vyvolá metoda.  
  
 Asynchronní metody nelze deklarovat [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametry, ale metodu můžete volat metody, které mají tyto parametry.  
  
 Další informace a příklady naleznete v tématu [asynchronní vrátit typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md). Další informace o tom, jak zachycení výjimek v asynchronní metody najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Asynchronní rozhraní API v prostředí Windows Runtime programování mít jednu z následujících návratové typy, které jsou podobné úlohy:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, která odpovídá <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, která odpovídá <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
  
 Další informace a příklady naleznete v tématu [volání asynchronní rozhraní API v C# nebo Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).  
  
##  <a name="BKMK_NamingConvention"></a> Zásady vytváření názvů  
 Podle konvence připojit "Asynchronní" na názvy metod, které mají `Async` modifikátor.  
  
 Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. Například by nemělo přejmenovat běžné obslužné rutiny událostí, například `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Související témata a ukázky (Visual Studio)  
  
|Název|Popis|Ukázka|  
|-----------|-----------------|------------|  
|[Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Ukázka asynchronního: Přístup k webové názorný postup](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Přidá <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do předchozího návodu. Použití `WhenAll` spustí všechny soubory ke stažení ve stejnou dobu.||  
|[Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Ukázka asynchronního: Paralelní provádění vícenásobných webových dotazů](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||  
|[Řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Ukázka asynchronního: Řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Vyladění s modifikátorem Async aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> -   [Zrušení asynchronní úlohy nebo seznamu úloh (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Zrušení asynchronních úloh po uplynutí časového intervalu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Zrušení zbývajících asynchronních úloh po jedné z nich dokončení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Ukázka asynchronního: Jemnou ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Ukazuje, jak zpracovat případy, ve kterých je aktivní asynchronní operace restartována po jejím spuštění.||  
|[WhenAny: Přemostění rozhraní .NET Framework a prostředí Windows Runtime](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|Ukazuje, jak přemostění mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby můžete použít <xref:System.Threading.Tasks.Task.WhenAny%2A> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Ukázka asynchronního: Přemostění rozhraní .NET a prostředí Windows Runtime (metody AsTask a WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|  
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Ukazuje, jak přemostění mezi typy úloh v rozhraní .NET Framework a IAsyncOperations v [!INCLUDE[wrt](~/includes/wrt-md.md)] tak, aby můžete použít <xref:System.Threading.CancellationTokenSource> s [!INCLUDE[wrt](~/includes/wrt-md.md)] metoda.|[Ukázka asynchronního: Přemostění rozhraní .NET a prostředí Windows Runtime (metody AsTask & zrušení)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Použití modifikátoru Async pro přístup k souborům (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||  
|[Asynchronní vzor založený na úlohách (TAP)](http://msdn.microsoft.com/library/8cef1fcf-6f9f-417c-b21f-3fd8bac75007)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. Je na základě vzoru <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> typy.||  
|[Asynchronní videa na kanálu 9](https://channel9.msdn.com/search?term=async+&type=All)|Poskytuje odkazy na různá videa o asynchronním programování.||  
  
##  <a name="BKMK_CompleteExample"></a> Úplný příklad  
 Následující kód je soubor MainWindow.xaml.vb z aplikace Windows Presentation Foundation (WPF), která toto téma popisuje. Si můžete stáhnout ukázkový z [asynchronní ukázka: příklad z "Asynchronní programování s Async a Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)
