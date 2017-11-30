---
title: "Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de1219de72be5ddc022d898c904663bf92ca5ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)
Asynchronní programy můžete napsat snadno a intuitivně najít pomocí modifikátoru async/await funkcí. Můžete napsat asynchronní kód, který vypadá jako synchronní kódu a nechat kompilátoru zpracování funkce zpětného volání obtížné a pokračování, které obvykle zahrnuje asynchronní kódu.  
  
 Další informace o funkci asynchronní najdete v tématu [asynchronní programování s Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sčítá počet bajtů v seznamu webů. Průvodce potom převede aplikace pro asynchronní řešení pomocí nové funkce.  
  
 Pokud nechcete, aby k vytváření aplikací, můžete stáhnout "asynchronní ukázka: přístup k webové návod (C# a Visual Basic)" z [ukázky kódu vývojáře](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
 V tomto návodu dokončit následující úlohy:  
  
-   [Chcete-li vytvořit aplikaci WPF](#CreateWPFApp)  
  
-   [Při návrhu jednoduché MainWindow WPF](#MainWindow)  
  
-   [Chcete-li přidat odkaz](#AddRef)  
  
-   [Chcete-li přidat potřebné příkazy importy](#ImportsState)  
  
-   [Chcete-li vytvořit synchronní aplikace](#synchronous)  
  
-   [K testování synchronní řešení](#testSynch)  
  
-   [Chcete-li převést GetURLContents asynchronní metody](#GetURLContents)  
  
-   [Chcete-li převést SumPageSizes asynchronní metody](#SumPageSizes)  
  
-   [Chcete-li převést startButton_Click asynchronní metody](#startButton)  
  
-   [K testování asynchronní řešení](#testAsynch)  
  
-   [Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework](#GetURLContentsAsync)  
  
-   [Příklad](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>Požadavky  
 Visual Studio 2012 nebo novější musí být nainstalován v počítači. Další informace najdete v tématu [webu společnosti Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).  
  
###  <a name="CreateWPFApp"></a>Chcete-li vytvořit aplikaci WPF  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **nainstalovaných šablonách** podokně vyberte jazyka Visual Basic a potom vyberte **aplikaci WPF** ze seznamu typy projektů.  
  
4.  V **název** textové pole, zadejte `AsyncExampleWPF`a potom zvolte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a>Při návrhu jednoduché MainWindow WPF  
  
1.  V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.  
  
2.  Pokud **sada nástrojů** okno není viditelný, otevřete **zobrazení** nabídce a potom zvolte **sada nástrojů**.  
  
3.  Přidat **tlačítko** řízení a **TextBox** řídit k **MainWindow** okno.  
  
4.  Zvýrazněte **TextBox** řízení a v **vlastnosti** okno, nastavte následující hodnoty:  
  
    -   Nastavte **název** vlastnost `resultsTextBox`.  
  
    -   Nastavte **výška** vlastnost, která má 250.  
  
    -   Nastavte **šířka** vlastnost na 500.  
  
    -   Na **Text** zadejte neproporcionálního písma, jako je například Lucida Console nebo globální neproporcionální.  
  
5.  Zvýrazněte **tlačítko** řízení a v **vlastnosti** okno, nastavte následující hodnoty:  
  
    -   Nastavte **název** vlastnost `startButton`.  
  
    -   Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **spustit**.  
  
6.  Pozice textového pole a tlačítko tak, aby obsahovat **MainWindow** okno.  
  
     Další informace o WPF návrháře XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a>Chcete-li přidat odkaz  
  
1.  V **Průzkumníku**, zvýrazněte názvem vašeho projektu.  
  
2.  Na řádku nabídek zvolte **projektu**, **přidat odkaz na**.  
  
     **Správce odkazů** zobrazí se dialogové okno.  
  
3.  V horní části dialogových oken ověřte, že je váš projekt cílení na rozhraní .NET Framework 4.5 nebo vyšší.  
  
4.  V **sestavení** oblasti, zvolte **Framework** Pokud již není vybraná.  
  
5.  V seznamu názvů, vyberte **System.Net.Http** zaškrtávací políčko.  
  
6.  Vyberte **OK** tlačítko dialogové okno zavřete.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a>Chcete-li přidat potřebné příkazy importy  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.vb a potom zvolte **kód zobrazení**.  
  
2.  Přidejte následující `Imports` příkazy v horní části souboru kódu, pokud nejsou již existuje.  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a>Chcete-li vytvořit synchronní aplikace  
  
1.  V okně návrhu MainWindow.xaml, dvakrát klikněte **spustit** tlačítko vytvořte `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.vb.  
  
2.  V MainWindow.xaml.vb, zkopírujte následující kód do textu `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     Kód volá metody, která řídí aplikace, `SumPageSizes`a zobrazí zprávu, když se vrátí ovládací prvek `startButton_Click`.  
  
3.  Kód pro synchronní řešení obsahuje následující čtyři metody:  
  
    -   `SumPageSizes`, který získá seznam adres URL webové stránky z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.  
  
    -   `SetUpURLList`, který provede a vrátí seznam hodnot webové adresy.  
  
    -   `GetURLContents`, který stáhne obsah každý web a vrátí obsah jako bajtové pole.  
  
    -   `DisplayResults`, který zobrazí počet bajtů v bajtové pole pro každou adresu URL.  
  
     Zkopírujte následující čtyři metody a vložte je v části `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.vb:  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a>K testování synchronní řešení  
  
1.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
     By se zobrazit výstup, který vypadá takto: v následujícím seznamu.  
  
    ```  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
    ```  
  
     Všimněte si, že bude trvat několik sekund zobrazí počty. Během této doby je blokována vlákna uživatelského rozhraní, kdy čeká požadované prostředky ke stažení. V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo i zavřete okno zobrazení po kliknutí **spustit** tlačítko. Tyto úsilí nezdaří, dokud začít zobrazí počet bajtů. Pokud web nereaguje, nemáte žádná informace o lokality, která se nezdařila. Je i obtížné čekání na zastavení a ukončení programu.  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a>Chcete-li převést GetURLContents asynchronní metody  
  
1.  Převést synchronní řešení asynchronní řešení, je nejlepší místo k spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje k webové . Rozhraní .NET Framework usnadňuje převod zadáním asynchronní verze obě metody.  
  
     Další informace o metodách, které se používají v `GetURLContents`, najdete v části <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Jak budete postupovat podle kroků v tomto návodu, zobrazí se několik chyb kompilátoru. Můžete je ignorovat a pokračovat návodu.  
  
     Změnit metodu, která je volána v třetím řádku `GetURLContents` z `GetResponse` pro asynchronní, založený na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda.  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync`Vrátí <xref:System.Threading.Tasks.Task%601>. V takovém případě *návratový proměnnou úloh*, `TResult`, má typ <xref:System.Net.WebResponse>. Tato úloha je promise k vytvoření skutečné třídě `WebResponse` objektu po požadovaná data byla stažena a je úloha spuštěná na dokončení.  
  
     Načíst `WebResponse` z úlohy hodnoty, použijí [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operátor k volání `GetResponseAsync`, jak ukazuje následující kód.  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     `Await` Operátor pozastaví provádění aktuální metody `GetURLContents`, dokud se nedokončí awaited úloh. Do té doby vrátí ovládací prvek volajícímu aktuální metoda. V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`. Po dokončení úlohy, přislíbeném `WebResponse` objektu je jako hodnotu awaited úloh a jejich přiřazení k proměnné `response`.  
  
     Do následujících dvou příkazů o vysvětlení, co se stane, je možné oddělit předchozí příkaz.  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`. Potom `Await` operátor se použije k načtení úkolu `WebResponse` hodnotu.  
  
     Pokud asynchronní metody práce uděláte, které nezávisí na dokončení úlohy, metodu můžete pokračovat v které pracují mezi těchto dvou příkazů po volání asynchronní metody a před použitím operátoru await. Příklady najdete v tématu [postup: Zkontrolujte vícenásobných webových dotazů paralelně pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [postupy: rozšíření návodu asynchronních podle pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Protože jste přidali `Await` dojde k chybě kompilátoru operátor v předchozím kroku. Operátor mohou být používány pouze metody, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor. Ignorovat chybu při opakováním kroků převod nahradit volání `CopyTo` pomocí volání `CopyToAsync`.  
  
    -   Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   `CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů na její argument `content`a nevrací smysluplný hodnotu. V synchronní verzi volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu. Asynchronní verzi `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>. Úloha funguje jako "Task(void)" a umožňuje metody být očekáváno. Použít `Await` nebo `await` k volání `CopyToAsync`, jak ukazuje následující kód.  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         Předchozí příkaz zkrátí následující dva řádky kódu.  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  Všechno, co zůstane v `GetURLContents` je upravte podpis metody. Můžete použít `Await` operátor pouze v metody, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor. Přidat modifikátor označit jako metodu *asynchronní metody*, jak ukazuje následující kód.  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  Návratový typ asynchronní metody lze pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. V jazyce Visual Basic, musí být metoda `Function` , který vrací `Task` nebo `Task(Of T)`, nebo musí být metoda `Sub`. Obvykle `Sub` metoda se používá jenom v asynchronní obslužnou rutinu, kde `Sub` je vyžadován. V ostatních případech použijete `Task(T)` Pokud má metodu dokončené [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který vrací hodnotu zadejte T a používáte `Task` pokud dokončené metoda nevrací hodnotu smysluplný.  
  
     Další informace najdete v tématu [asynchronní vrátit typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
     Metoda `GetURLContents` má příkaz return, a příkaz vrátí pole bajtů. Návratový typ asynchronní verze je proto Task(T), kde T představuje bajtové pole. Proveďte následující změny v podpis metody:  
  
    -   Změnit návratový typ na `Task(Of Byte())`.  
  
    -   Podle konvence asynchronní metody mají názvy, které končí "Asynchronní,", přejmenujte metodu `GetURLContentsAsync`.  
  
     Následující kód ukazuje tyto změny.  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     Pomocí těchto několik změn, převod `GetURLContents` pro asynchronní metodu dokončení.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a>Chcete-li převést SumPageSizes asynchronní metody  
  
1.  Opakováním kroků v předchozím postupu pro `SumPageSizes`. Nejprve změnit volání `GetURLContents` pro asynchronní volání.  
  
    -   Změňte název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.  
  
    -   Použít `Await` úlohy, `GetURLContentsAsync` vrátí získat bajtů pole hodnota.  
  
     Následující kód ukazuje tyto změny.  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     Předchozí přiřazení zkrátí následující dva řádky kódu.  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  Proveďte následující změny v signatury metody:  
  
    -   Označit metodu s `Async` modifikátor.  
  
    -   Přidejte "Asynchronní" název metody.  
  
    -   Neexistuje žádné proměnné návratový úkolů, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metodu neobsahuje žádné `Return` příkaz.) Však musí vracet metodu `Task` být může používat await. Proto změnit typ metody z `Sub` k `Function`. Návratový typ funkce je `Task`.  
  
     Následující kód ukazuje tyto změny.  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     Převod `SumPageSizes` k `SumPageSizesAsync` dokončení.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a>Chcete-li převést startButton_Click asynchronní metody  
  
1.  V obslužné rutině, změňte název metody volané z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.  
  
2.  Protože `SumPageSizesAsync` je asynchronní metody, změňte kód v obslužné rutiny události pro await výsledek.  
  
     Volání `SumPageSizesAsync` odpovídá volání `CopyToAsync` v `GetURLContentsAsync`. Vrátí volání `Task`, nikoli `Task(T)`.  
  
     Jako v předchozích postupech můžete převést volání pomocí jeden příkaz nebo dvou příkazů. Následující kód ukazuje tyto změny.  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  Pokud chcete zabránit omylem nutnosti opětovného zadávání operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **spustit** tlačítko.  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     Tlačítko na konci obslužné rutiny události můžete znovu povolit.  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     Další informace o opětovné zadání najdete v tématu [zpracování vícenásobný přístup v aplikacích s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Nakonec přidejte `Async` modifikátor deklaraci tak, aby obslužná rutina události můžete await `SumPagSizesAsync`.  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     Obvykle se nezmění názvy obslužných rutin událostí. Návratový typ se nezmění na `Task` protože obslužné rutiny události musí být `Sub` procedury v jazyce Visual Basic.  
  
     Převod projektu synchronní pro asynchronní zpracování je dokončena.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a>K testování asynchronní řešení  
  
1.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
2.  By se zobrazit výstup, který vypadá takto: výstup synchronní řešení. Všimněte si však následující rozdíly.  
  
    -   Výsledky všechny nedojde ve stejnou dobu, po dokončení zpracování. Například obě aplikace obsahovat řádek v `startButton_Click` který vymaže textového pole. Je cílem vymazat textové pole mezi spustí, pokud se rozhodnete **spustit** tlačítko druhý dobu, po ukazuje se, jednu sadu výsledků. V synchronní verzi textového pole není zaškrtnuto, těsně před zobrazí počty druhý dobu, po dokončení stahování a vlákna uživatelského rozhraní může provádět další činnosti. V asynchronní verzi textového pole vymaže hned po zvolení **spustit** tlačítko.  
  
    -   Co je nejdůležitější – vlákna uživatelského rozhraní není blokován během stahování. Můžete přesunout nebo změňte velikost okna během stahování webové prostředky, počítají a zobrazit. Pokud jeden z webů je pomalé nebo přestane reagovat, můžete zrušit operaci tak, že zvolíte **Zavřít** tlačítko (x v poli red v pravém horním rohu).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a>Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework  
  
1.  Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít. Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, nemá právě co potřebujete pro účely tohoto postupu. Můžete ho místo `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.  
  
     Prvním krokem je vytvoření `HttpClient` objektu v metodě `SumPageSizesAsync`. Přidejte následující deklarace při spuštění metody.  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  V `SumPageSizesAsync,` nahradit volání vaše `GetURLContentsAsync` metoda pomocí volání `HttpClient` metoda.  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  Odeberte nebo komentář `GetURLContentsAsync` metoda, která jste napsali.  
  
4.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
     Chování tuto verzi projekt by měl odpovídat chování, které je popsaný v části "postup testovací asynchronní řešení", ale s i méně úsilí od vás.  
  
##  <a name="BKMK_CompleteCodeExamples"></a>Příklad  
 Následující kód obsahuje úplný příklad převod synchronního asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metoda, která jste napsali. Všimněte si, že důrazně podobá řešení původní, synchronní.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 Následující kód obsahuje kompletní příklad řešení, která používá `HttpClient` metody `GetByteArrayAsync`.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázka asynchronního: Přístup k webové návod (C# a Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [Await – operátor](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [Asynchronní](../../../../visual-basic/language-reference/modifiers/async.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [Asynchronní programování založené na úlohách (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
