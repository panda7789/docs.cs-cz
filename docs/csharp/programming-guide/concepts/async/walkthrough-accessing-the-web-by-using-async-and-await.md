---
title: 'Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 33145f6a7ececd85e6eeaebb80a81f3075878761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338127"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)
Asynchronní programy můžete napsat snadno a intuitivně najít pomocí modifikátoru async/await funkcí. Můžete napsat asynchronní kód, který vypadá jako synchronní kódu a nechat kompilátoru zpracování funkce zpětného volání obtížné a pokračování, které obvykle zahrnuje asynchronní kódu.  
  
 Další informace o funkci asynchronní najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
 Tento názorný postup začíná synchronní aplikace Windows Presentation Foundation (WPF), který sčítá počet bajtů v seznamu webů. Průvodce potom převede aplikace pro asynchronní řešení pomocí nové funkce.  
  
 Pokud nechcete, aby k vytváření aplikací, můžete stáhnout [asynchronní ukázka: přístup k webové návod (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
 V tomto návodu dokončit následující úlohy:  
  
-   [Chcete-li vytvořit aplikaci WPF](#CreateWPFApp)  
  
-   [Při návrhu jednoduché MainWindow WPF](#MainWindow)  
  
-   [Chcete-li přidat odkaz](#AddRef)  
  
-   [Chcete-li přidat potřebné pomocí direktiv](#usingDir)  
  
-   [Chcete-li vytvořit synchronní aplikace](#synchronous)  
  
-   [K testování synchronní řešení](#testSynch)  
  
-   [Chcete-li převést GetURLContents asynchronní metody](#GetURLContents)  
  
-   [Chcete-li převést SumPageSizes asynchronní metody](#SumPageSizes)  
  
-   [Chcete-li převést startButton_Click asynchronní metody](#startButton)  
  
-   [K testování asynchronní řešení](#testAsynch)  
  
-   [Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework](#GetURLContentsAsync)  
  
-   [Příklad](#BKMK_CompleteCodeExamples)  
  
> [!NOTE]
>  Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.  
  
###  <a name="CreateWPFApp"></a> Chcete-li vytvořit aplikaci WPF  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **nainstalovaných šablonách** podokně vyberte Visual C# a potom vyberte **aplikaci WPF** ze seznamu typy projektů.  
  
4.  V **název** textové pole, zadejte `AsyncExampleWPF`a potom zvolte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> Při návrhu jednoduché MainWindow WPF  
  
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
###  <a name="AddRef"></a> Chcete-li přidat odkaz  
  
1.  V **Průzkumníku**, zvýrazněte názvem vašeho projektu.  
  
2.  Na řádku nabídek zvolte **projektu**, **přidat odkaz na**.  
  
     **Správce odkazů** zobrazí se dialogové okno.  
  
3.  V horní části dialogových oken ověřte, že je váš projekt cílení na rozhraní .NET Framework 4.5 nebo vyšší.  
  
4.  V **sestavení** oblasti, zvolte **Framework** Pokud již není vybraná.  
  
5.  V seznamu názvů, vyberte **System.Net.Http** zaškrtávací políčko.  
  
6.  Vyberte **OK** tlačítko dialogové okno zavřete.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a> Chcete-li přidat potřebné pomocí direktiv  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a potom zvolte **kód zobrazení**.  
  
2.  Přidejte následující `using` direktivy v horní části souboru kódu, pokud nejsou již existuje.  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> Chcete-li vytvořit synchronní aplikace  
  
1.  V okně návrhu MainWindow.xaml, dvakrát klikněte **spustit** tlačítko vytvořte `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs.  
  
2.  V MainWindow.xaml.cs, zkopírujte následující kód do textu `startButton_Click`:  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     Kód volá metody, která řídí aplikace, `SumPageSizes`a zobrazí zprávu, když se vrátí ovládací prvek `startButton_Click`.  
  
3.  Kód pro synchronní řešení obsahuje následující čtyři metody:  
  
    -   `SumPageSizes`, který získá seznam adres URL webové stránky z `SetUpURLList` a potom zavolá `GetURLContents` a `DisplayResults` zpracovat každou adresu URL.  
  
    -   `SetUpURLList`, který provede a vrátí seznam hodnot webové adresy.  
  
    -   `GetURLContents`, který stáhne obsah každý web a vrátí obsah jako bajtové pole.  
  
    -   `DisplayResults`, který zobrazí počet bajtů v bajtové pole pro každou adresu URL.  
  
     Zkopírujte následující čtyři metody a vložte je v části `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs:  
  
    ```csharp  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
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
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> K testování synchronní řešení  
  
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
###  <a name="GetURLContents"></a> Chcete-li převést GetURLContents asynchronní metody  
  
1.  Převést synchronní řešení asynchronní řešení, je nejlepší místo k spuštění v `GetURLContents` protože volání <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> a <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> jsou, kde aplikace přistupuje k webové . Rozhraní .NET Framework usnadňuje převod zadáním asynchronní verze obě metody.  
  
     Další informace o metodách, které se používají v `GetURLContents`, najdete v části <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Jak budete postupovat podle kroků v tomto návodu, zobrazí se několik chyb kompilátoru. Můžete je ignorovat a pokračovat návodu.  
  
     Změnit metodu, která je volána v třetím řádku `GetURLContents` z `GetResponse` pro asynchronní, založený na úlohách <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda.  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  `GetResponseAsync` Vrátí <xref:System.Threading.Tasks.Task%601>. V takovém případě *návratový proměnnou úloh*, `TResult`, má typ <xref:System.Net.WebResponse>. Tato úloha je promise k vytvoření skutečné třídě `WebResponse` objektu po požadovaná data byla stažena a je úloha spuštěná na dokončení.  
  
     Načíst `WebResponse` z úlohy hodnoty, použijí [await](../../../../csharp/language-reference/keywords/await.md) operátor k volání `GetResponseAsync`, jak ukazuje následující kód.  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     `await` Operátor pozastaví provádění aktuální metody `GetURLContents`, dokud se nedokončí awaited úloh. Do té doby vrátí ovládací prvek volajícímu aktuální metoda. V tomto příkladu je aktuální metoda `GetURLContents`, a má volající `SumPageSizes`. Po dokončení úlohy, přislíbeném `WebResponse` objektu je jako hodnotu awaited úloh a jejich přiřazení k proměnné `response`.  
  
     Do následujících dvou příkazů o vysvětlení, co se stane, je možné oddělit předchozí příkaz.  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     Volání `webReq.GetResponseAsync` vrátí `Task(Of WebResponse)` nebo `Task<WebResponse>`. Pak operátor await se použije pro úlohu načíst `WebResponse` hodnotu.  
  
     Pokud asynchronní metody má práce uděláte, které nezávisí na dokončení úlohy, které pracují mezi těchto dvou příkazů po volání metody asynchronní a před pokračovat metodu `await` operátor platí. Příklady najdete v tématu [postupy: paralelní provádění více webových dotazů pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) a [postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Protože jste přidali `await` dojde k chybě kompilátoru operátor v předchozím kroku. Operátor mohou být používány pouze metody, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor. Ignorovat chybu při opakováním kroků převod nahradit volání `CopyTo` pomocí volání `CopyToAsync`.  
  
    -   Změňte název metody, která je volána pro <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   `CopyTo` Nebo `CopyToAsync` metoda zkopíruje bajtů na její argument `content`a nevrací smysluplný hodnotu. V synchronní verzi volání `CopyTo` je jednoduchý příkaz, který nevrací hodnotu. Asynchronní verzi `CopyToAsync`, vrátí <xref:System.Threading.Tasks.Task>. Úloha funguje jako "Task(void)" a umožňuje metody být očekáváno. Použít `Await` nebo `await` k volání `CopyToAsync`, jak ukazuje následující kód.  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         Předchozí příkaz zkrátí následující dva řádky kódu.  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  Všechno, co zůstane v `GetURLContents` je upravte podpis metody. Můžete použít `await` operátor pouze v metody, které jsou označené [asynchronní](../../../../csharp/language-reference/keywords/async.md) modifikátor. Přidat modifikátor označit jako metodu *asynchronní metody*, jak ukazuje následující kód.  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  Návratový typ asynchronní metody lze pouze <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, nebo `void` v jazyce C#. Obvykle návratovým typem `void` se používá jenom v asynchronní obslužnou rutinu, kde `void` je vyžadován. V ostatních případech použijete `Task(T)` Pokud má metodu dokončené [vrátit](../../../../csharp/language-reference/keywords/return.md) příkaz, který vrací hodnotu zadejte T a používáte `Task` pokud dokončené metoda nevrací hodnotu smysluplný. Si můžete představit `Task` návratový typ jako znamená "Task(void)."  
  
     Další informace najdete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
     Metoda `GetURLContents` má příkaz return, a příkaz vrátí pole bajtů. Návratový typ asynchronní verze je proto Task(T), kde T představuje bajtové pole. Proveďte následující změny v podpis metody:  
  
    -   Změnit návratový typ na `Task<byte[]>`.  
  
    -   Podle konvence asynchronní metody mají názvy, které končí "Asynchronní,", přejmenujte metodu `GetURLContentsAsync`.  
  
     Následující kód ukazuje tyto změny.  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     Pomocí těchto několik změn, převod `GetURLContents` pro asynchronní metodu dokončení.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> Chcete-li převést SumPageSizes asynchronní metody  
  
1.  Opakováním kroků v předchozím postupu pro `SumPageSizes`. Nejprve změnit volání `GetURLContents` pro asynchronní volání.  
  
    -   Změňte název metody, která je volána z `GetURLContents` k `GetURLContentsAsync`, pokud jste tak již neučinili.  
  
    -   Použít `await` úlohy, `GetURLContentsAsync` vrátí získat bajtů pole hodnota.  
  
     Následující kód ukazuje tyto změny.  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     Předchozí přiřazení zkrátí následující dva řádky kódu.  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  Proveďte následující změny v signatury metody:  
  
    -   Označit metodu s `async` modifikátor.  
  
    -   Přidejte "Asynchronní" název metody.  
  
    -   Neexistuje žádné proměnné návratový úkolů, T, tentokrát protože `SumPageSizesAsync` nevrací hodnotu pro T. (Metodu neobsahuje žádné `return` příkaz.) Však musí vracet metodu `Task` být může používat await. Proto změnit návratový typ metody z `void` k `Task`.  
  
     Následující kód ukazuje tyto změny.  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     Převod `SumPageSizes` k `SumPageSizesAsync` dokončení.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> Chcete-li převést startButton_Click asynchronní metody  
  
1.  V obslužné rutině, změňte název metody volané z `SumPageSizes` k `SumPageSizesAsync`, pokud jste tak již neučinili.  
  
2.  Protože `SumPageSizesAsync` je asynchronní metody, změňte kód v obslužné rutiny události pro await výsledek.  
  
     Volání `SumPageSizesAsync` odpovídá volání `CopyToAsync` v `GetURLContentsAsync`. Vrátí volání `Task`, nikoli `Task(T)`.  
  
     Jako v předchozích postupech můžete převést volání pomocí jeden příkaz nebo dvou příkazů. Následující kód ukazuje tyto změny.  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  Pokud chcete zabránit omylem nutnosti opětovného zadávání operaci, přidejte následující příkaz v horní části `startButton_Click` zakázat **spustit** tlačítko.  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     Tlačítko na konci obslužné rutiny události můžete znovu povolit.  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     Další informace o opětovné zadání najdete v tématu [zpracování vícenásobný přístup v aplikacích s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Nakonec přidejte `async` modifikátor deklaraci tak, aby obslužná rutina události můžete await `SumPagSizesAsync`.  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     Obvykle se nezmění názvy obslužných rutin událostí. Návratový typ se nezmění na `Task` protože obslužné rutiny události musí vracet `void`.  
  
     Převod projektu synchronní pro asynchronní zpracování je dokončena.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> K testování asynchronní řešení  
  
1.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
2.  By se zobrazit výstup, který vypadá takto: výstup synchronní řešení. Všimněte si však následující rozdíly.  
  
    -   Výsledky všechny nedojde ve stejnou dobu, po dokončení zpracování. Například obě aplikace obsahovat řádek v `startButton_Click` který vymaže textového pole. Je cílem vymazat textové pole mezi spustí, pokud se rozhodnete **spustit** tlačítko druhý dobu, po ukazuje se, jednu sadu výsledků. V synchronní verzi textového pole není zaškrtnuto, těsně před zobrazí počty druhý dobu, po dokončení stahování a vlákna uživatelského rozhraní může provádět další činnosti. V asynchronní verzi textového pole vymaže hned po zvolení **spustit** tlačítko.  
  
    -   Co je nejdůležitější – vlákna uživatelského rozhraní není blokován během stahování. Můžete přesunout nebo změňte velikost okna během stahování webové prostředky, počítají a zobrazit. Pokud jeden z webů je pomalé nebo přestane reagovat, můžete zrušit operaci tak, že zvolíte **Zavřít** tlačítko (x v poli red v pravém horním rohu).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> Chcete-li nahradit metoda GetURLContentsAsync pomocí metody rozhraní .NET Framework  
  
1.  Rozhraní .NET Framework 4.5 poskytuje mnoho asynchronní metody, které můžete použít. Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, nemá právě co potřebujete pro účely tohoto postupu. Můžete ho místo `GetURLContentsAsync` metoda, kterou jste vytvořili v předchozím kroku.  
  
     Prvním krokem je vytvoření `HttpClient` objektu v metodě `SumPageSizesAsync`. Přidejte následující deklarace při spuštění metody.  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  V `SumPageSizesAsync,` nahradit volání vaše `GetURLContentsAsync` metoda pomocí volání `HttpClient` metoda.  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  Odeberte nebo komentář `GetURLContentsAsync` metoda, která jste napsali.  
  
4.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
     Chování tuto verzi projekt by měl odpovídat chování, které je popsaný v části "postup testovací asynchronní řešení", ale s i méně úsilí od vás.  
  
##  <a name="BKMK_CompleteCodeExamples"></a> Příklad  
 Následující kód obsahuje úplný příklad převod synchronního asynchronní řešení pomocí asynchronní `GetURLContentsAsync` metoda, která jste napsali. Všimněte si, že důrazně podobá řešení původní, synchronní.  
  
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
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 Následující kód obsahuje kompletní příklad řešení, která používá `HttpClient` metody `GetByteArrayAsync`.  
  
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
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázka asynchronního: Přístup k webové návod (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [async](../../../../csharp/language-reference/keywords/async.md)  
 [await](../../../../csharp/language-reference/keywords/await.md)  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Asynchronní programování založené na úlohách (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957)  
 [Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
