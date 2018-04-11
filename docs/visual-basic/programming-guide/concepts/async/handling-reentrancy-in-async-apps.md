---
title: Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c2f80eb8a0fbc655143ca02ead5f6f46f102918
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)
Když zahrnete asynchronní kód ve vaší aplikaci, musí vzít v úvahu a pravděpodobně zabránit vícenásobný přístup, který odkazuje na nutnosti opětovného zadávání asynchronní operace předtím, než byla dokončena. Pokud nemáte identifikovat a zpracování možnosti pro vícenásobný přístup, může to způsobit neočekávané výsledky.  
  
 **V tomto tématu**  
  
-   [Rozpozná vícenásobný přístup](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [Podpora vícenásobného přístupu](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Zakázat tlačítko Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Zrušit a operaci restartujte.](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Spustit více operací a fronty výstupu](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [Kontrola a spuštění aplikace příklad](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.  
  
##  <a name="BKMK_RecognizingReentrancy"></a> Rozpozná vícenásobný přístup  
 V příkladu v tomto tématu, vyberte uživatele **spustit** tlačítko zahájíte asynchronní aplikaci, která stáhne řadu weby a vypočítá celkový počet bajtů, které jsou staženy. Synchronní verzi příkladu by odpovídat stejný způsobem, bez ohledu na to o tom, kolikrát uživatel vybere tlačítko proto, že po prvním vlákna uživatelského rozhraní ignoruje tyto události, dokud nebude dokončeno aplikace spuštěná. V aplikaci asynchronní však vlákna uživatelského rozhraní nadále reagovat a předtím, než byla dokončena, může je znovu zadat asynchronní operaci.  
  
 Následující příklad ukazuje očekávaný výstup, pokud uživatel vybere **spustit** tlačítko pouze jednou. Zobrazí seznam stažené webů s velikost v bajtech každé lokality. Celkový počet bajtů, zobrazí se na konci.  
  
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
  
 Ale pokud se uživatel rozhodne tlačítko více než jednou, obslužné rutiny události je volána opakovaně a proces stahování je znovu zadat pokaždé, když. V důsledku toho několik asynchronních operací běží ve stejnou dobu, výstup interleaves výsledky a celkový počet bajtů je matoucí.  
  
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
  
 Můžete zkontrolovat kód, který vytváří tento výstup podle posouvání na konci tohoto tématu. Můžete experimentovat s kódem stahování řešení do místního počítače a potom spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu vytvořit svůj vlastní projekt pro další informace a pokyny najdete v části [ Kontrola a spuštění aplikace příklad](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).  
  
##  <a name="BKMK_HandlingReentrancy"></a> Podpora vícenásobného přístupu  
 Vícenásobný přístup v mnoha různými způsoby v závislosti na tom, co chcete udělat v aplikaci může zpracovávat. Toto téma představuje následující příklady:  
  
-   [Zakázat tlačítko Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Zakažte **spustit** tlačítko při operaci tak, aby uživatel ji ukončit.  
  
-   [Zrušit a operaci restartujte.](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Zrušte všechny operace, která je stále spuštěn, když uživatel vybere **spustit** tlačítko znovu a poté pokračujte umožňují nedávno požadovanou operaci.  
  
-   [Spustit více operací a fronty výstupu](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Povolit všechny požadované operace běží asynchronně, ale koordinaci zobrazení výstupu tak, aby výsledky z každé operace se zobrazí společně a v pořadí.  
  
###  <a name="BKMK_DisableTheStartButton"></a> Zakázat tlačítko Start  
 Můžete blokovat **spustit** tlačítko spuštěného operace zakázáním tlačítka v horní části `StartButton_Click` obslužné rutiny události. Pak opětovného povolení tlačítko uvnitř `Finally` blokovat po dokončení operace tak, aby uživatelé znovu spusťte aplikaci.  
  
 Následující kód ukazuje tyto změny, které jsou označeny pomocí hvězdiček. Změny můžete přidat do kód na konci tohoto tématu nebo dokončení aplikaci si můžete stáhnout [ukázky asynchronní: vícenásobný přístup v aplikacích .NET plochy](http://go.microsoft.com/fwlink/?LinkId=266571). Název projektu je DisableStartButton.  
  
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
  
 V důsledku změny, tlačítko nereaguje při `AccessTheWebAsync` stahuje webů, takže proces nelze znovu zadat.  
  
###  <a name="BKMK_CancelAndRestart"></a> Zrušit a operaci restartujte.  
 Místo zakázání **spustit** tlačítko můžete zachovat tlačítko aktivní, ale, pokud uživatel vybere akci, že tlačítko Zrušit operaci, která je již spuštěna a pokračovat v operaci nedávno spustila.  
  
 Další informace o zrušení najdete v tématu [Fine-Tuning vaše asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Nastavit tento scénář, proveďte následující změny k základní kód, který je součástí [kontrolu a spuštění aplikace příklad](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645). Také můžete stáhnout dokončení aplikace z [ukázky asynchronní: vícenásobný přístup v aplikacích .NET plochy](http://go.microsoft.com/fwlink/?LinkId=266571). Název tohoto projektu je CancelAndRestart.  
  
1.  Deklarace <xref:System.Threading.CancellationTokenSource> proměnnou, `cts`, který je v oboru pro všechny metody.  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  V `StartButton_Click`, určete, zda již probíhá operace. Pokud hodnota `cts` je `Nothing`, je již aktivní žádná operace. Pokud není hodnota `Nothing`, je zrušená operaci, která je již spuštěna.  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  Nastavit `cts` na jinou hodnotu, který představuje aktuální proces.  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  Na konci `StartButton_Click`aktuální proces nebude hotový, takže nastavit hodnotu `cts` zpět na `Nothing`.  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 Následující kód ukazuje všechny změny v `StartButton_Click`. Budou přidány jsou označené hvězdičky.  
  
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
  
-   Přidání parametru tak, aby přijímal token zrušení z `StartButton_Click`.  
  
-   Použití <xref:System.Net.Http.HttpClient.GetAsync%2A> metoda stažení weby, protože `GetAsync` přijme <xref:System.Threading.CancellationToken> argument.  
  
-   Před voláním `DisplayResults` zobrazíte výsledky pro každý web stažené zkontrolujte `ct` k ověření, že nedošlo ke zrušení aktuální operace.  
  
 Následující kód ukazuje tyto změny, které jsou označeny pomocí hvězdiček.  
  
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
  
 Pokud se rozhodnete **spustit** tlačítko několikrát při spuštěné aplikaci ho by měl vytvořit výsledky, které se podobají následující výstup.  
  
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
  
 K vyloučení částečné seznamy, zrušte komentář u první řádek kódu `StartButton_Click` zrušte textového pole pokaždé, když uživatel znovu spustí operaci.  
  
###  <a name="BKMK_RunMultipleOperations"></a> Spustit více operací a fronty výstupu  
 Tento příklad třetí je nejvíce složitý, v tom, že jiná asynchronní operace pokaždé, když uživatel vybere spuštění aplikace **spustit** tlačítko a všechny operace spustit na dokončení. Všechny požadované operace stáhnout weby ze seznamu asynchronně, ale postupně zobrazí výstup z operace. To znamená, je prokládaný skutečné stahování aktivity, jako výstup v [rozpozná vícenásobný přístup](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ukazuje, ale seznam výsledků pro každou skupinu se zobrazí samostatně.  
  
 Operace sdílet globální konfiguraci <xref:System.Threading.Tasks.Task>, `pendingWork`, který slouží jako těchto pravidel pro proces zobrazení.  
  
 Spuštěním tohoto příkladu vložením změny do kódu v [vytváření aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), nebo můžete podle pokynů v [stahování aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ukázku stáhnout a spusťte projekt QueueResults.  
  
 Následující výstup zobrazuje výsledek, pokud uživatel vybere **spustit** tlačítko pouze jednou. Popisek písmeno, A, označuje, že výsledkem je od prvního **spustit** je zvolen tlačítko. Čísla zobrazit pořadí adresy URL v seznamu cílů stahování.  
  
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
  
 Pokud se uživatel rozhodne **spustit** tlačítko třikrát, aplikace vytváří výstup, která se podobá následující řádky. Přihlásit informace řádky, které začínají křížek (#) trasování průběh aplikace.  
  
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
  
 Skupiny B a C spustit před skupiny A byl dokončen, ale zobrazí výstup pro každou skupinu samostatně. Veškerý výstup pro skupiny A jako první se objeví, za nímž následuje veškerý výstup pro skupinu B a pak všechny výstup pro skupinu C. Aplikace vždy zobrazí skupiny, v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webů v pořadí, ve kterém příslušné adresy URL se zobrazí v seznamu adres URL.  
  
 Nelze však předvídání pořadí, ve které se stahování ve skutečnosti dojít. Po spuštění více skupin stažení úlohy, které generují jsou všechny adaptéry aktivní. Nelze předpokládat, že A-1 bude stažen před b-1 objekty a nelze předpokládat, že A-1 bude stažen před A-2.  
  
#### <a name="global-definitions"></a>Globální definice  
 Ukázkový kód obsahuje následující dvě globální deklarace, které jsou viditelné z všechny metody.  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 `Task` Proměnnou, `pendingWork`, dohlíží proces zobrazení a zabrání libovolnou skupinu přerušení operace zobrazení jinou skupinu. Proměnnou znak `group`, popisků výstup z různých skupin k ověření, že výsledky se zobrazí v očekávaném pořadí.  
  
#### <a name="the-click-event-handler"></a>Obslužná rutina události kliknutí  
 Obslužné rutiny události `StartButton_Click`, zvýší písmeno skupiny pokaždé, když uživatel vybere **spustit** tlačítko. Potom volání obslužné rutiny `AccessTheWebAsync` spustit stahování operaci.  
  
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
 Tento příklad rozdělí `AccessTheWebAsync` do dvou metod. První metoda `AccessTheWebAsync`, spustí všechny úlohy stahování pro skupinu a nastavuje `pendingWork` řídit proces zobrazení. Metoda používá integrované dotaz jazyka (dotaz LINQ) a <xref:System.Linq.Enumerable.ToArray%2A> spustit všechny úlohy stahování ve stejnou dobu.  
  
 `AccessTheWebAsync` pak zavolá `FinishOneGroupAsync` await dokončení každého stažení a zobrazit jeho délka.  
  
 `FinishOneGroupAsync` Vrátí úlohu, která je přiřazena k `pendingWork` v `AccessTheWebAsync`. Že hodnota zabraňuje přerušení jinou operací před dokončením úlohy.  
  
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
 Tato metoda procházení stažení úlohy ve skupině, čeká na každé z nich, zobrazí délka stažené webu a přidá do celkové délka.  
  
 První příkaz v `FinishOneGroupAsync` používá `pendingWork` a ujistěte se, že zadáte metoda není v konfliktu se operace, která je již v zobrazení procesu nebo který je už čeká. Pokud probíhá takové operace, vstup operace musí počkat jeho vypněte.  
  
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
  
 Spuštěním tohoto příkladu vložením změny do kódu v [vytváření aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), nebo můžete podle pokynů v [stahování aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) stáhnout vzorek, a pak spusťte projekt QueueResults.  
  
#### <a name="points-of-interest"></a>Body zájmu  
 Informace řádky, které začínají křížek (#), ve výstupu vysvětlení, jak tento příklad funguje.  
  
 Výstup zobrazuje následující vzory.  
  
-   Skupinu lze spustit skupinu předchozí zobrazit její výstup, ale proces se nepřerušil zobrazení předchozí skupině výstup.  
  
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
  
-   `pendingWork` Úloha je `Nothing` na začátku `FinishOneGroupAsync` pouze pro skupiny A, což zahájení první. Skupiny A zatím není dokončený výraz await, když se dosáhne `FinishOneGroupAsync`. Proto se řízení nevrátí k `AccessTheWebAsync`a první přiřazení `pendingWork` nedošlo k.  
  
-   Následující dva řádky vždy objeví spolu ve výstupu. Kód je nemohlo dojít k přerušení mezi skupině operaci počínaje `StartButton_Click` a přiřazení úloh pro skupinu do `pendingWork`.  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     Po zadání skupiny `StartButton_Click`, operace nedokončí výraz await, dokud zadá operaci `FinishOneGroupAsync`. Žádné jiné operace. proto může získat kontrolu během tohoto segmentu kódu.  
  
##  <a name="BKMD_SettingUpTheExample"></a> Kontrola a spuštění aplikace příklad  
 Abyste lépe pochopili, například aplikace, můžete ji stáhnout, vytvořit sami nebo zkontrolujte kód na konci tohoto tématu bez implementace aplikace.  
  
> [!NOTE]
>  Pokud chcete spustit v příkladu jako aplikace na ploše Windows Presentation Foundation (WPF), musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.  
  
###  <a name="BKMK_DownloadingTheApp"></a> Stažení aplikace  
  
1.  Stáhněte si komprimovaný soubor z [ukázky asynchronní: vícenásobný přístup v aplikacích .NET plochy](http://go.microsoft.com/fwlink/?LinkId=266571).  
  
2.  Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.  
  
3.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
4.  Přejděte do složky, která obsahuje dekomprimovaných ukázkový kód a pak otevřete soubor řešení (.sln).  
  
5.  V **Průzkumníku řešení**, otevřete místní nabídku pro projekt, který chcete spustit a potom vyberte **nastavit jako StartUpProject**.  
  
6.  Zvolte klávesy CTRL + F5 sestavení a spuštění projektu.  
  
###  <a name="BKMK_BuildingTheApp"></a> Vytváření aplikace  
 Následující část obsahuje kód, který sestavení v příkladu jako aplikaci WPF.  
  
##### <a name="to-build-a-wpf-app"></a>Vytvoření aplikace WPF  
  
1.  Start Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **nainstalovaných šablonách** podokně rozbalte **jazyka Visual Basic**a potom rozbalte **Windows**.  
  
4.  V seznamu typy projektů, vyberte **aplikaci WPF**.  
  
5.  Název projektu `WebsiteDownloadWPF`a potom zvolte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
6.  V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.  
  
     Pokud na kartě není zobrazena, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.  
  
7.  V **XAML** zobrazení MainWindow.xaml, nahraďte kód následujícím kódem.  
  
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
  
     Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhu** zobrazení MainWindow.xaml.  
  
8.  Přidat odkaz pro <xref:System.Net.Http>.  
  
9. V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.vb a potom zvolte **kód zobrazení**.  
  
10. V MainWindow.xaml.vb nahraďte kód následujícím kódem.  
  
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
  
11. Zvolte CTRL + F5 klíče pro spuštění programu a potom vyberte **spustit** tlačítko několikrát.  
  
12. Proveďte změny z [zakázat tlačítko Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [zrušit a restartujte operaci](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), nebo [spustit více operací a fronty výstup](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pro zpracování vícenásobný přístup.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
