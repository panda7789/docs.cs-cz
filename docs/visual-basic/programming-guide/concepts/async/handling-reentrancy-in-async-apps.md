---
title: Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: fa1bfcc5cfaf4a3ba1f5116be7b3f1851ce293af
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625383"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)
Pokud zahrnete asynchronní kód ve vaší aplikaci, by měl zvážit a případně zabránit vícenásobnému přístupu, který se vztahuje k nutnosti opětovného zadávání asynchronní operace ještě před dokončením. Pokud neidentifikujete a nemanipulujete vícenásobnému přístupu, může to způsobit neočekávané výsledky.  
  
 **V tomto tématu**  
  
-   [Rozpoznávání vícenásobného přístupu](#BKMK_RecognizingReentrancy)  
  
-   [Podpora vícenásobného přístupu](#BKMK_HandlingReentrancy)  
  
    -   [Zakázání tlačítka Start](#BKMK_DisableTheStartButton)  
  
    -   [Nerušte a nerestartujte operace](#BKMK_CancelAndRestart)  
  
    -   [Spustit více operací a zařazení výstupu do fronty](#BKMK_RunMultipleOperations)  
  
-   [Prostudování a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
##  <a name="BKMK_RecognizingReentrancy"></a> Rozpoznávání vícenásobného přístupu  
 V příkladu v tomto tématu, zvolte možnost uživatelé **Start** tlačítko pro zahájení asynchronní aplikace, která stáhne řady webů a vypočítá celkový počet bajtů, které byly staženy. Synchronní verze tohoto příkladu odpoví stejným způsobem bez ohledu na to, kolikrát uživatel vybere tlačítko, protože po prvním vlákně uživatelského rozhraní bude tyto události ignorovat až do ukončení aplikace. V asynchronní aplikaci však vlákno UI i nadále odpovídá a můžete znovu zadat asynchronní operace ještě před dokončením.  
  
 Následující příklad zobrazuje očekávaný výstup, když uživatel klikne **Start** tlačítko pouze jednou. Zobrazí se seznam stažených webových stránek s velikostí v bajtech každého webu. Na konci se zobrazuje celkový počet bajtů.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Pokud uživatel vybere tlačítko více než jednou, ale obslužná rutina události je vyvolána opakovaně, a proces stahování je znovu zadat pokaždé, když. V důsledku toho několik asynchronních operací spuštěno ve stejnou dobu, výstup předřadí výsledky a celkový počet bajtů je matoucí.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Můžete zkontrolovat kód, který vytváří tento výstup, přechodem na konci tohoto tématu. Můžete experimentovat s kódem stažením řešení do místního počítače a následným spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu k vytvoření vlastního projektu pro další informace a pokyny naleznete v tématu [ Prostudování a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample).  
  
##  <a name="BKMK_HandlingReentrancy"></a> Podpora vícenásobného přístupu  
 Můžete zpracovat vícenásobnost různými způsoby v závislosti na tom, co chcete, aby vaše aplikace provést. Toto téma představuje následující příklady:  
  
-   [Zakázání tlačítka Start](#BKMK_DisableTheStartButton)  
  
     Zakažte **Start** tlačítko během operace tak, aby uživatel nemohl přerušit ho.  
  
-   [Nerušte a nerestartujte operace](#BKMK_CancelAndRestart)  
  
     Zrušit jakoukoli operaci, která je stále spuštěna, když uživatel klikne **Start** tlačítko znovu, a potom pokračujte umožňují nedávno požadované operace.  
  
-   [Spustit více operací a zařazení výstupu do fronty](#BKMK_RunMultipleOperations)  
  
     Povolit, že všechny požadované operace běžely asynchronně, ale koordinovat zobrazení výstupu tak, aby se výsledky z každé operace zobrazovaly společně a v pořadí.  
  
###  <a name="BKMK_DisableTheStartButton"></a> Zakázání tlačítka Start  
 Můžete blokovat **Start** tlačítko, když je spuštěná operace, zakázáním tlačítka v horní části `StartButton_Click` obslužné rutiny události. Potom můžete znovu povolit tlačítko z `Finally` blokovat po ukončení operace tak, aby uživatelé můžou aplikaci spouštět znovu.  
  
 Následující kód znázorňuje tyto změny, které jsou označeny hvězdičkami. Změny můžete přidat do kódu na konci tohoto tématu nebo si můžete stáhnout hotovou aplikaci z [asynchronní vzorky: Vícenásobnost v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název projektu je DisableStartButton.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 V důsledku změny, tlačítko nereaguje zatímco `AccessTheWebAsync` stahuje webové stránky, takže proces nelze znovu zadat.  
  
###  <a name="BKMK_CancelAndRestart"></a> Nerušte a nerestartujte operace  
 Namísto zakázání **Start** tlačítko, můžete zachovat tlačítko aktivní, ale, pokud uživatel vybere toto tlačítko znovu, zrušit operaci, která je již spuštěna a nechá pokračovat v operaci naposledy spuštěnou.  
  
 Další informace o zrušení naleznete v tématu [asynchronní aplikace Fine-Tuning (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Nastavit tento scénář, proveďte následující změny základního kódu, která je součástí [Prostudování a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample). Také můžete stáhnout hotovou aplikaci z [asynchronní vzorky: Vícenásobnost v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název tohoto projektu je CancelAndRestart.  
  
1.  Deklarace <xref:System.Threading.CancellationTokenSource> proměnnou, `cts`, která je v oboru pro všechny metody.  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  V `StartButton_Click`, určete, zda již probíhá operace. Pokud hodnota `cts` je `Nothing`, žádná operace ještě není aktivní. Pokud hodnota není `Nothing`, je zrušena operace, která je již spuštěna.  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  Nastavte `cts` na jinou hodnotu, která představuje aktuální proces.  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  Na konci `StartButton_Click`, je aktuální proces dokončen, takže nastavte hodnotu `cts` zpět `Nothing`.  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 Následující kód ukazuje všechny změny v `StartButton_Click`. Přidání jsou označena hvězdičkami.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 V `AccessTheWebAsync`, proveďte následující změny.  
  
-   Přidat parametr pro přijetí tokenu zrušení z `StartButton_Click`.  
  
-   Použití <xref:System.Net.Http.HttpClient.GetAsync%2A> metoda stažení webových stránek, protože `GetAsync` přijímá <xref:System.Threading.CancellationToken> argument.  
  
-   Před voláním `DisplayResults` Chcete-li zobrazit výsledky pro každý stažený web, zkontrolujte `ct` k ověření, že aktuální operace nebyla zrušena.  
  
 Následující kód znázorňuje tyto změny, které jsou označeny hvězdičkami.  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 Pokud se rozhodnete **Start** tlačítko několikrát během spuštění této aplikace mohou být vráceny výsledky, které se podobají následujícímu výstupu.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Chcete-li odstranit dílčí seznamy, zrušte komentář u prvního řádku kódu v `StartButton_Click` vymazání textového pole pokaždé, když uživatel znovu spustí operaci.  
  
###  <a name="BKMK_RunMultipleOperations"></a> Spustit více operací a zařazení výstupu do fronty  
 Tento třetí příklad je v nejkomplikovanější v tom, že aplikace spustí jinou asynchronní operaci pokaždé, když uživatel klikne **Start** tlačítko a všechny operace běží až do dokončení. Všechny požadované operace stahují webové stránky ze seznamu asynchronně, ale výstup z operací je uveden postupně. To znamená, že skutečná aktivita stahování je prokládána, jak poukazuje výstup v [rozpoznávání vícenásobného přístupu](#BKMK_RecognizingReentrancy) zobrazí, ale seznam výsledků pro každou skupinu je předkládán samostatně.  
  
 Operace sdílí globální <xref:System.Threading.Tasks.Task>, `pendingWork`, který slouží jako správce pro zpracování zobrazení.  
  
 Tento příklad lze spustit zadáním nebo vložením změn do kódu v [aplikaci](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [si stáhnou aplikaci](#BKMK_DownloadingTheApp) ke stažení vzorku a spuštění projektu QueueResults.  
  
 Následující výstup zobrazuje výsledek, když uživatel klikne **Start** tlačítko pouze jednou. Označení písmenem A označuje, že výsledek pochází z prvního **Start** kliknutí na tlačítko. Čísla popisují pořadí adres URL v seznamu cílů ke stažení.  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 Pokud uživatel klikne **Start** tlačítko třikrát, aplikace vytvoří výstup, který se podobá následujícím řádkům. Podepsat informační řádky, které začínají znakem křížku (#), sledují průběh aplikace.  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 Skupiny B a C se spustí před dokončením skupiny A, ale výstup pro jednotlivé skupiny se zobrazí odděleně. Veškerý výstup pro skupinu A zobrazí se první, následovaný všemi výstupy pro skupinu B a pak veškerý výstup pro skupinu C. Aplikace vždy zobrazí skupiny v pořadí a pro každou skupinu vždy zobrazí informace o jednotlivých webech v pořadí, ve kterém se zobrazí v seznamu adres URL adresy URL.  
  
 Nelze však předvídat pořadí, ve kterém se soubory ke stažení skutečně došlo. Po spuštění více skupin, jsou všechny aktivní úlohy stahování, které generují. Nelze předpokládat, že A-1 se stáhne před b-1 a nelze předpokládat, že A-1 se stáhne před a-2.  
  
#### <a name="global-definitions"></a>Globální definice  
 Ukázka kódu obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 `Task` Proměnnou, `pendingWork`, dohlíží na proces zobrazení a zabrání jakékoli skupině v přerušení operace zobrazení jiné skupiny. Proměnné znaku `group`, značí výstup z různých skupin a ověřte tak, že výsledky zobrazí v očekávaném pořadí.  
  
#### <a name="the-click-event-handler"></a>Obslužná rutina události kliknutí  
 Obslužná rutina události `StartButton_Click`, zvyšuje písmeno skupiny pokaždé, když uživatel klikne **Start** tlačítko. Potom rutina volá `AccessTheWebAsync` ke spuštění operace stahování.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a>Metoda AccessTheWebAsync  
 V tomto příkladu rozdělí `AccessTheWebAsync` do dvou metod. První metoda `AccessTheWebAsync`, spustí všechny úlohy stahování pro skupinu a nastaví `pendingWork` k řízení procesu zobrazení. Metoda používá Language Integrated Query (LINQ dotaz) a <xref:System.Linq.Enumerable.ToArray%2A> zahájíte stahování všech úloh ve stejnou dobu.  
  
 `AccessTheWebAsync` pak zavolá `FinishOneGroupAsync` čekání na dokončení každého stažení a zobrazení jeho délky.  
  
 `FinishOneGroupAsync` Vrátí úlohu, která je přiřazena `pendingWork` v `AccessTheWebAsync`. Tato hodnota zabraňuje přerušení jinou operací před dokončením úkolu.  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a>Metoda FinishOneGroupAsync  
 Tato metoda projde stažené úlohy ve skupině, čeká na každé z nich, zobrazení délky staženého webu a přičtením délky k celku.  
  
 První příkaz v `FinishOneGroupAsync` používá `pendingWork` abyste měli jistotu, že zadávání metody není v konfliktu s operací, která je již v procesu zobrazení nebo která již čeká. Pokud tato operace probíhá, operace zadávání musí čekat, než přijde.  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 Tento příklad lze spustit zadáním nebo vložením změn do kódu v [aplikaci](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [si stáhnou aplikaci](#BKMK_DownloadingTheApp) ke stažení vzorku a spuštění projektu QueueResults.  
  
#### <a name="points-of-interest"></a>Body zájmu  
 Informační řádky, které začínají znakem křížku (#) ve výstupu vysvětlení, jak tento příklad funguje.  
  
 Výstup zobrazuje následující vzory.  
  
-   Skupiny může být spuštěna, když předchozí skupina zobrazuje výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   `pendingWork` Úkol je `Nothing` na začátku `FinishOneGroupAsync` pouze u skupiny A, která začíná jako první. Skupina A dosud nedokončila výraz await, až dosáhne `FinishOneGroupAsync`. Proto se ovládací prvek nevrátil do `AccessTheWebAsync`a první přiřazení k `pendingWork` nedošlo k.  
  
-   Následující dva řádky vždy zobrazí společně ve výstupu. Kód není nikdy přerušen mezi spuštěním operace skupiny `StartButton_Click` a přiřazením úkolu skupiny `pendingWork`.  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     Po vstupu skupiny do `StartButton_Click`, operace nedokončí výraz await, dokud operace nevstoupí do `FinishOneGroupAsync`. Proto se žádná jiná operace nemůže získat kontrolu během tohoto segmentu kódu.  
  
##  <a name="BKMD_SettingUpTheExample"></a> Prostudování a spuštění ukázkové aplikace  
 Pro lepší pochopení příkladu aplikace, můžete si ho stáhnout, sestavit ji sami nebo zkontrolovat kód na konci tohoto tématu bez implementace aplikace.  
  
> [!NOTE]
>  Chcete-li spustit příklad jako aplikaci klasické pracovní plochy Windows Presentation Foundation (WPF), musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
###  <a name="BKMK_DownloadingTheApp"></a> Stažení aplikace  
  
1.  Stáhněte si komprimovaný soubor z [asynchronní vzorky: Vícenásobnost v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).  
  
2.  Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.  
  
3.  V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.  
  
4.  Přejděte do složky obsahující dekomprimovaný ukázkový kód a potom otevřete soubor řešení (.sln).  
  
5.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt, který chcete spustit a klikněte na tlačítko **nastavit jako výchozí projekt**.  
  
6.  Stiskněte klávesy CTRL + F5 sestavte a spusťte projekt.  
  
###  <a name="BKMK_BuildingTheApp"></a> Vytvoření aplikace  
 Následující část obsahuje kód pro vytváření příklad jako aplikaci WPF.  
  
##### <a name="to-build-a-wpf-app"></a>Vytvoření aplikace WPF  
  
1.  Spusťte sadu Visual Studio.  
  
2.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3.  V **nainstalované šablony** podokně rozbalte **jazyka Visual Basic**a potom rozbalte **Windows**.  
  
4.  V seznamu typů projektů zvolte **aplikace WPF**.  
  
5.  Pojmenujte projekt `WebsiteDownloadWPF`a klikněte na tlačítko **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
6.  V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.  
  
     Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.  
  
7.  V **XAML** zobrazení souboru mainwindow.XAML, nahraďte kód následujícím kódem.  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** zobrazení souboru MainWindow.xaml.  
  
8.  Přidat odkaz pro <xref:System.Net.Http>.  
  
9. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.  
  
10. V souboru MainWindow.xaml.vb nahraďte kód následujícím kódem.  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/hh191443.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/jj155761.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/hh524395.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. Stiskněte klávesy CTRL + F5 ke spuštění programu a klikněte na tlačítko **Start** tlačítko několikrát.  
  
12. Proveďte požadované změny z [zakázat tlačítko Start](#BKMK_DisableTheStartButton), [nerušte a nerestartujte operaci](#BKMK_CancelAndRestart), nebo [spustit více operací a fronty výstupu](#BKMK_RunMultipleOperations) pro zpracování vícenásobného přístupu.  
  
## <a name="see-also"></a>Viz také:

- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
