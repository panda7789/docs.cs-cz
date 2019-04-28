---
title: 'Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 7f9b71bc76e8d17cf2fb6714070b4439265d1fda
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765918"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)
Asynchronní programy můžete napsat snadno a intuitivně s použitím funkce async/await. Můžete psát asynchronní kód, který vypadá jako synchronní kód a nechte kompilátor obtížné zpětného volání funkce a pokračování, které obvykle zahrnuje asynchronního kódu.  
  
 Další informace o funkci Async naleznete v tématu [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sumarizuje počet bajtů v seznamu webů. Návodu poté převádí aplikaci, aby asynchronní řešení pomocí nové funkce.  
  
 Pokud nechcete, aby k vytváření aplikací, si můžete stáhnout "asynchronní vzorek: Přístup k webovému návodu (C# a Visual Basic) "z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
 V tomto návodu dokončíte následující úkoly:  
  
- [Vytvoření aplikace WPF](#CreateWPFApp)  
  
- [Návrh jednoduchého hlavního okna MainWindow WPF](#MainWindow)  
  
- [Přidání odkazu](#AddRef)  
  
- [Přidání potřebných příkazů Imports](#ImportsState)  
  
- [Vytvoření synchronní aplikace](#synchronous)  
  
- [Otestování synchronního řešení](#testSynch)  
  
- [Převedení metody GetURLContents na asynchronní metodu](#GetURLContents)  
  
- [Převedení metody SumPageSizes na asynchronní metodu](#SumPageSizes)  
  
- [Převedení metody startButton_Click na asynchronní metodu](#startButton)  
  
- [Otestování asynchronního řešení](#testAsynch)  
  
- [Nahrazení metody GetURLContentsAsync metodou rozhraní .NET Framework](#GetURLContentsAsync)  
  
- [Příklad](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>Požadavky  
 Visual Studio 2012 nebo novější musí nainstalovat ve vašem počítači. Další informace najdete v tématu [webu společnosti Microsoft](https://go.microsoft.com/fwlink/?LinkId=235233).  
  
### <a name="CreateWPFApp"></a> Vytvoření aplikace WPF  
  
1. Spusťte Visual Studio.  
  
2. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3. V **nainstalované šablony** podokně zvolte jazyka Visual Basic a pak zvolte **aplikace WPF** ze seznamu typů projektů.  
  
4. V **název** textové pole, zadejte `AsyncExampleWPF`a klikněte na tlačítko **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
## <a name="BKMK_DesignWPFMainWin"></a>   
### <a name="MainWindow"></a> Návrh jednoduchého hlavního okna MainWindow WPF  
  
1. V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.  
  
2. Pokud **nástrojů** okně není zobrazena, otevřete **zobrazení** nabídky a klikněte na tlačítko **nástrojů**.  
  
3. Přidat **tlačítko** ovládacího prvku a **textového pole** ovládací prvek **hlavního okna MainWindow** okna.  
  
4. Zvýrazněte **TextBox** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:  
  
    - Nastavte **název** vlastnost `resultsTextBox`.  
  
    - Nastavte **výška** vlastnost na 250.  
  
    - Nastavte **šířka** vlastnost na hodnotu 500.  
  
    - Na **Text** kartu, zadejte neproporcionální písmo jako Arial konzoly nebo globální neproporcionálním písmem v.  
  
5. Zvýrazněte **tlačítko** ovládací prvek a v **vlastnosti** okno, nastavte následující hodnoty:  
  
    - Nastavte **název** vlastnost `startButton`.  
  
    - Změňte hodnotu **obsahu** vlastnost z **tlačítko** k **Start**.  
  
6. Umístěte do textového pole a tlačítko tak, aby oba se objeví v **hlavního okna MainWindow** okna.  
  
     Další informace o Návrhář WPF XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
## <a name="BKMK_AddReference"></a>   
### <a name="AddRef"></a> Přidání odkazu  
  
1. V **Průzkumníka řešení**, vyberte název vašeho projektu.  
  
2. V panelu nabídky zvolte **projektu**, **přidat odkaz**.  
  
     **Správce odkazů** zobrazí se dialogové okno.  
  
3. V horní části dialogového okna ověřte, že váš projekt je cílen na verzi rozhraní .NET Framework 4.5 nebo vyšší.  
  
4. V **sestavení** oblasti, zvolte **Framework** Pokud není již vybrána.  
  
5. Vyberte v seznamu názvů **System.Net.Http** zaškrtávací políčko.  
  
6. Zvolte **OK** tlačítka zavřete dialogové okno.  
  
## <a name="BKMK_AddStatesandDirs"></a>   
### <a name="ImportsState"></a> Přidání potřebných příkazů Imports  
  
1. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.  
  
2. Přidejte následující `Imports` příkazů v horní části souboru kódu, pokud již nejsou k dispozici.  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
## <a name="BKMK_CreatSynchApp"></a>   
### <a name="synchronous"></a> Vytvoření synchronní aplikace  
  
1. V okně návrhu, MainWindow.xaml, dvakrát klikněte **Start** pro vytvoření `startButton_Click` obslužné rutiny události v souboru MainWindow.xaml.vb.  
  
2. V souboru MainWindow.xaml.vb, zkopírujte následující kód do hlavní části `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     Kód volá metodu, která řídí aplikaci, `SumPageSizes`a zobrazí zprávu, když se ovládací prvek vrátí `startButton_Click`.  
  
3. Kód pro synchronní řešení obsahuje následující čtyři metody:  
  
    - `SumPageSizes`, která načte seznam adres URL webové stránky z `SetUpURLList` a pak zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.  
  
    - `SetUpURLList`, který provede a vrátí seznam webové adresy.  
  
    - `GetURLContents`, který stáhne obsah každého webu a vrátí obsah jako bajtové pole.  
  
    - `DisplayResults`, který zobrazuje počet bajtů v bajtové pole pro každou adresu URL.  
  
     Následující čtyři metody zkopírujte a vložte je za `startButton_Click` obslužné rutiny události v souborech MainWindow.xaml.vb:  
  
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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
## <a name="BKMK_TestSynchSol"></a>   
### <a name="testSynch"></a> Otestování synchronního řešení  
  
1. Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
     By se zobrazit výstup, který vypadá podobně jako v následujícím seznamu.  
  
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
  
     Všimněte si, že trvá několik sekund zobrazí počty. Během této doby vlákno uživatelského rozhraní je blokována během čekání požadované prostředky ke stažení. V důsledku toho nelze přesunout, maximalizovat, minimalizovat nebo dokonce zavřete okno zobrazení po zvolení **Start** tlačítko. Tyto aktivity dál rozšiřuji neúspěšné, dokud se začnou objevovat počtu bajtů. Pokud web nereaguje, je nutné žádná zpráva o které lokalitě se nezdařilo. Je obtížné i zastavte čekání a ukončení programu.  
  
## <a name="BKMK_ConvertGtBtArr"></a>   
### <a name="GetURLContents"></a> Převedení metody GetURLContents na asynchronní metodu  
  
1. Převést synchronní řešení na asynchronní řešení, je nejlepším místem pro spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> – metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje na web . Rozhraní .NET Framework zjednodušuje převod zadáním asynchronní verze obě metody.  
  
     Další informace o metodách, které se používají v `GetURLContents`, naleznete v tématu <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Jak budete postupovat podle kroků v tomto názorném postupu se zobrazí několik chyby kompilátoru. Můžete je ignorovat a pokračovat v tomto návodu.  
  
     Změnit metodu, která je volána v třetí řádek `GetURLContents` z `GetResponse` na asynchronní, založené na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2. `GetResponseAsync` Vrátí <xref:System.Threading.Tasks.Task%601>. V takovém případě *úloh návratové*, `TResult`, má typ <xref:System.Net.WebResponse>. Úkol je příslib z k vytvoření skutečný `WebResponse` objektu po stažení požadovaných dat a je úloha spuštěná na dokončení.  
  
     Načíst `WebResponse` hodnoty z úlohy, použijte [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operátor volání `GetResponseAsync`, jak ukazuje následující kód.  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     `Await` Operátor pozastaví vykonávání aktuální metody, `GetURLContents`, dokud není dokončen očekávaný úkol. Mezitím se ovládací prvek vrátí volajícímu metody, aktuální. V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`. Úloha dokončení přislíbeném `WebResponse` objekt je vytvořen jako hodnota očekávané úlohy a přiřazená k proměnné `response`.  
  
     Předchozí příkaz je možné rozdělit na následující dva příkazy o vysvětlení, co se stane.  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`. Potom `Await` úkol k získání je použit operátor `WebResponse` hodnotu.  
  
     Pokud asynchronní metoda má práce, která nezávisí na dokončení úlohy, metoda může pokračovat v práci mezi tyto dva příkazy po volání metody async a předtím, než je použit operátor await. Příklady najdete v tématu [jak: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [jak: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3. Vzhledem k tomu, že jste přidali `Await` dojde k chybě kompilátoru operátor v předchozím kroku. Operátor, který lze použít pouze v metodách, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor. Ignorovat chybu, zatímco nahraďte volání kroky převod `CopyTo` voláním `CopyToAsync`.  
  
    - Změnit název metody, která je volána k <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    - `CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů do svého argumentu, `content`a nevrací smysluplnou hodnotu. Synchronní verze volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu. Asynchronní verze `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>. Úloha funkce jako "Task(void)" a umožňuje metodu k ní použít operátor await. Použít `Await` nebo `await` volání `CopyToAsync`, jak ukazuje následující kód.  
  
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
  
4. Všechno, zůstane do `GetURLContents` je upravte podpis metody. Můžete použít `Await` operátor pouze v metodách, které jsou označené [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor. Přidat modifikátor k označení metody jako *asynchronní metoda*, jak ukazuje následující kód.  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5. Návratový typ asynchronní metody může být pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. V jazyce Visual Basic, musí být metoda `Function` , která vrací `Task` nebo `Task(Of T)`, nebo metoda musí být `Sub`. Obvykle `Sub` metoda se používá jenom v asynchronní obslužnou rutinu události, kde `Sub` je povinný. V ostatních případech použijete `Task(T)` pokud dokončené metody [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, který vrátí hodnotu typu T a používáte `Task` Pokud dokončená metoda nevrací hodnotu smysluplné.  
  
     Další informace najdete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
     Metoda `GetURLContents` disponuje návratovým příkazem, a příkaz vrátí pole bajtů. Návratový typ asynchronní verze je proto Task(T), kde T je bajtové pole. Proveďte následující změny v podpisu metody:  
  
    - Změňte návratový typ na `Task(Of Byte())`.  
  
    - Podle konvence asynchronní metody mají názvy, které končí slovem "Async", takže přejmenovat metodu `GetURLContentsAsync`.  
  
     Následující kód znázorňuje tyto změny.  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     Tyto drobné změny převodu `GetURLContents` na asynchronní metodu dokončení.  
  
## <a name="BKMK_ConvertSumPagSzs"></a>   
### <a name="SumPageSizes"></a> Převedení metody SumPageSizes na asynchronní metodu  
  
1. Zopakujte kroky z předchozího postupu pro `SumPageSizes`. Nejprve změňte volání `GetURLContents` pro asynchronní volání.  
  
    - Změnit název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.  
  
    - Použít `Await` úkolu, který `GetURLContentsAsync` hodnota pole vrátí získat bajt.  
  
     Následující kód znázorňuje tyto změny.  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     Dřívější přiřazení zkrátí následující dva řádky kódu.  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2. Proveďte následující změny v podpisu metody:  
  
    - Označení metody `Async` modifikátor.  
  
    - Přidáte k názvu metody "Async".  
  
    - Neexistuje žádná proměnná vrácené úlohy, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metoda nemá žádný `Return` příkazu.) Metoda však musí vrátit `Task` bude očekávatelný. Proto změnit typ metody z `Sub` k `Function`. Návratový typ funkce je `Task`.  
  
     Následující kód znázorňuje tyto změny.  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     Převod `SumPageSizes` k `SumPageSizesAsync` je dokončena.  
  
## <a name="BKMK_Cnvrtbttn1"></a>   
### <a name="startButton"></a> Převedení metody startButton_Click na asynchronní metodu  
  
1. V obslužné rutině události změnit název volané metody z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.  
  
2. Protože `SumPageSizesAsync` je metodou asynchronní kód v obslužné rutině události await pro čekání výsledek.  
  
     Volání `SumPageSizesAsync` zrcadlí volání `CopyToAsync` v `GetURLContentsAsync`. Volání se vrátí `Task`, nikoli `Task(T)`.  
  
     Stejně jako v předchozích postupů můžete převést volání pomocí jednoho příkazu nebo dvou příkazů. Následující kód znázorňuje tyto změny.  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3. Chcete-li zabránit náhodnému pokuste operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **Start** tlačítko.  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     Můžete znovu povolit tlačítko na konci obslužné rutiny události.  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     Další informace o vícenásobného přístupu najdete v tématu [zpracování vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4. Nakonec přidejte `Async` modifikátoru deklarace tak, aby obslužná rutina události může čekat `SumPagSizesAsync`.  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     Obvykle se nezmění názvy obslužných rutin událostí. Návratový typ není změněn na `Task` protože obslužné rutiny události musí být `Sub` procedury v jazyce Visual Basic.  
  
     Dokončení převodu projektu z synchronní pro asynchronní zpracování.  
  
## <a name="BKMK_testAsynchSolution"></a>   
### <a name="testAsynch"></a> Otestování asynchronního řešení  
  
1. Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
2. By se zobrazit výstup, který se podobá výstup synchronní řešení. Všimněte si však následující rozdíly.  
  
    - Výsledky všech nedojde ve stejnou dobu, po dokončení zpracování. Například obě aplikace obsahovat řádek v `startButton_Click` , který vymaže do textového pole. Naším záměrem je zrušte textové pole mezi spuštění, pokud se rozhodnete **Start** tlačítko podruhé, po jednu sadu výsledků nezobrazila. Synchronní verze do textového pole není zaškrtnuto, těsně před plánovaným začátkem zobrazují počty pro při druhém volání při dokončení stahování a vlákna uživatelského rozhraní je zdarma provádět další činnosti. V asynchronní verze, do textového pole vymaže ihned poté, co vyberete **Start** tlačítko.  
  
    - Co je nejdůležitější vlákno uživatelského rozhraní není blokované, soubory ke stažení. Můžete přecházet nebo změně velikosti okna, zatímco v průběhu stahování webové prostředky počítá a zobrazuje. Pokud některý z webů je pomalý nebo nereaguje, můžete zrušit operaci výběrem **Zavřít** tlačítko (x červená pole v pravém horním rohu).  
  
## <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
### <a name="GetURLContentsAsync"></a> Nahrazení metody GetURLContentsAsync metodou rozhraní .NET Framework  
  
1. Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít. Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, stačí provedla potřebné pro tento návod. Můžete použít místo něj `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.  
  
     Prvním krokem je vytvoření `HttpClient` objektů v metodě `SumPageSizesAsync`. Na začátek metody přidejte následující deklarace.  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2. V `SumPageSizesAsync,` nahraďte volání vaše `GetURLContentsAsync` pomocí volání metody `HttpClient` metody.  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3. Odstranit nebo okomentovat `GetURLContentsAsync` metodu, která jste napsali.  
  
4. Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
     Chování této verze projektu by měl odpovídat chování, které popisuje postup "k otestování asynchronního řešení", ale s i menším úsilím od vás.  
  
## <a name="BKMK_CompleteCodeExamples"></a> Příklad  
 Následující kód obsahuje úplný příklad převod ze synchronního na asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metodu, která jste napsali. Všimněte si, že důrazně vypadá podobně jako původní, která je synchronní řešení.  
  
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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 Následující kód obsahuje úplný příklad řešení, které používá `HttpClient` metody `GetByteArrayAsync`.  
  
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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Viz také:

- [Ukázka asynchronní metody: Přístup k webovému návodu (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Asynchronní programování založené na úlohách (TAP)](https://go.microsoft.com/fwlink/?LinkId=204847)
- [Postupy: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
