---
title: Podpora vícenásobného přístupu v aplikacích s modifikátorem Async
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 2d1af14016f82b5de875d3638b132e14c7d2280d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396633"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Zpracování Vícenásobný přístup v asynchronních aplikacích (Visual Basic)

Při zahrnutí asynchronního kódu do aplikace byste měli zvážit a případně zabránit Vícenásobný přístup, která označuje, že se má znovu zadat asynchronní operace předtím, než se dokončí. Pokud neidentifikujete a nezpracováváte možnosti pro Vícenásobný přístup, může dojít k neočekávaným výsledkům.

> [!NOTE]
> Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

> [!NOTE]
> Protokol TLS (Transport Layer Security) verze 1,2 je teď minimální verzí, která se má použít při vývoji aplikací. Pokud se vaše aplikace zaměřuje na verzi .NET Framework starší než 4,7, přečtěte si následující článek o [osvědčených postupech TLS (Transport Layer Security) s .NET Framework](../../../../framework/network-programming/tls.md).

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a>Rozpoznávání Vícenásobný přístup

V příkladu v tomto tématu uživatelé zvolí tlačítko **Spustit** pro zahájení asynchronní aplikace, která stáhne řadu webů a vypočítá celkový počet stažených bajtů. Synchronní verze příkladu by reagovala stejným způsobem bez ohledu na to, kolikrát uživatel vybere tlačítko, protože po prvním spuštění vlákno UI tyto události ignoruje, dokud se aplikace nedokončí. V asynchronní aplikaci ale vlákno uživatelského rozhraní nadále reaguje a před dokončením můžete znovu zadat asynchronní operaci.

Následující příklad ukazuje očekávaný výstup, pokud uživatel klikne na tlačítko **Start** pouze jednou. Seznam stažených webů se zobrazí v bajtech v bajtech každé lokality. Celkový počet bajtů se zobrazí na konci.

```console
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

Pokud však uživatel zvolí tlačítko více než jednou, obslužná rutina události je vyvolána opakovaně a proces stahování je znovu zadán pokaždé. Výsledkem je, že několik asynchronních operací je současně spuštěno, výstup vynechává výsledky a celkový počet bajtů je matoucí.

```console
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

Můžete zkontrolovat kód, který vytváří tento výstup posouváním na konec tohoto tématu. Můžete experimentovat s kódem stažením řešení do místního počítače a následným spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu Vytvoření vlastního projektu pro další informace a pokyny najdete v tématu [Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample).

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a>Zpracování Vícenásobný přístup

V závislosti na tom, co má vaše aplikace dělat, můžete Vícenásobný přístup zpracovávat různými způsoby. Toto téma nabízí následující příklady:

- [Zakázání tlačítka Start](#BKMK_DisableTheStartButton)

  Zakáže tlačítko **Start** , když je operace spuštěná, aby ji uživatel nemohl přerušit.

- [Zrušení a restartování operace](#BKMK_CancelAndRestart)

  Zrušte všechny operace, které pořád běží, když uživatel znovu zvolí tlačítko **Start** , a pak nechte poslední vyžadovanou operaci pokračovat.

- [Spuštění více operací a zařazení výstupu do fronty](#BKMK_RunMultipleOperations)

  Povolí asynchronní spouštění všech požadovaných operací, ale koordinuje zobrazení výstupu, aby se výsledky jednotlivých operací zobrazovaly společně a v daném pořadí.

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a>Zakázání tlačítka Start

Tlačítko **Start** lze zablokovat, když je operace spuštěna, zakázáním tlačítka v horní části `StartButton_Click` obslužné rutiny události. Pak můžete znovu povolit tlačítko v rámci `Finally` bloku po dokončení operace, aby uživatelé mohli aplikaci znovu spustit.

Následující kód zobrazuje tyto změny, které jsou označeny hvězdičkami. Změny můžete přidat do kódu na konci tohoto tématu nebo si můžete stáhnout dokončenou aplikaci z [asynchronních ukázek: Vícenásobný přístup v aplikacích .NET Desktop](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název projektu je DisableStartButton.

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

V důsledku změn tlačítko při stahování webů nereaguje na `AccessTheWebAsync` to, aby se tento proces nemohl znovu zadat.

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a>Zrušení a restartování operace

Místo zakázání tlačítka **Start** můžete ponechat tlačítko aktivní, ale pokud uživatel toto tlačítko zvolí znovu, zrušte operaci, která už je spuštěná, a nechejte operaci naposledy spuštěnou.

Další informace o zrušení najdete v tématu [jemné vyladění aplikace Async (Visual Basic)](fine-tuning-your-async-application.md).

Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [části Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample). Dokončenou aplikaci si můžete také stáhnout z části [Async Samples: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název tohoto projektu je CancelAndRestart.

1. Deklarujte <xref:System.Threading.CancellationTokenSource> proměnnou, `cts` , která je v oboru pro všechny metody.

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. V nástroji `StartButton_Click` Určete, zda již operace probíhá. Pokud hodnota `cts` je `Nothing` , žádná operace již není aktivní. Pokud hodnota není `Nothing` , operace, která je již spuštěna, je zrušena.

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. Nastavte `cts` na jinou hodnotu, která představuje aktuální proces.

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. Na konci `StartButton_Click` je aktuální proces dokončen, takže nastavte hodnotu `cts` zpět na `Nothing` .

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

Následující kód ukazuje všechny změny v `StartButton_Click` . Přidané položky jsou označeny hvězdičkami.

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

V nástroji `AccessTheWebAsync` proveďte následující změny.

- Přidejte parametr pro přijetí tokenu zrušení z `StartButton_Click` .

- Použijte <xref:System.Net.Http.HttpClient.GetAsync%2A> metodu ke stažení webů, protože `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argument.

- Před voláním pro `DisplayResults` zobrazení výsledků každého staženého webu zkontrolujte, zda nebyla `ct` aktuální operace zrušena.

 Následující kód zobrazuje tyto změny, které jsou označeny hvězdičkami.

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

Pokud při spuštění této aplikace několikrát kliknete na tlačítko **Start** , mělo by se jednat o výsledky, které se podobají následujícímu výstupu:

```console
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

Chcete-li odstranit částečné seznamy, odkomentujte první řádek kódu v nástroji, `StartButton_Click` aby při každém restartování operace vymazalo textové pole.

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a>Spuštění více operací a zařazení výstupu do fronty

Tento třetí příklad je nejsložitější v tom, že aplikace spouští další asynchronní operace pokaždé, když uživatel zvolí tlačítko **Start** , a všechny operace, které se spouštějí k dokončení. Všechny požadované operace stahují weby ze seznamu asynchronně, ale výstup z operací je prezentován sekvenčně. To znamená, že se aktuální aktivita stahování prochází, protože se zobrazuje výstup v [rozpoznávání Vícenásobný přístup](#BKMK_RecognizingReentrancy) , ale seznam výsledků pro každou skupinu se zobrazí samostatně.

Operace sdílí globální <xref:System.Threading.Tasks.Task> , `pendingWork` , který slouží jako server gatekeeper pro proces zobrazení.

Tento příklad můžete spustit vložením změn do kódu v [sestavování aplikace](#BKMK_BuildingTheApp)nebo můžete postupovat podle pokynů v tématu Stažení [aplikace](#BKMK_DownloadingTheApp) ke stažení ukázky a spuštění projektu QueueResults.

Následující výstup ukazuje výsledek, pokud uživatel zvolí tlačítko **Start** pouze jednou. Označení písmenem (a) označuje, že výsledek je od první zvolené tlačítko **Start** . Čísla zobrazují pořadí adres URL v seznamu cílů stahování.

```console
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

Pokud uživatel třikrát zvolí tlačítko **Start** , aplikace vytvoří výstup podobný následujícímu řádku. Informační řádky, které začínají znakem křížku (#) sledují průběh aplikace.

```console
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

Skupiny B a C se spustí před dokončením skupiny A, ale výstup pro každou skupinu se zobrazí samostatně. Nejprve se zobrazí celý výstup pro skupinu A následovaný celým výstupem pro skupinu B a pak všechny výstupy pro skupinu C. Aplikace vždy zobrazuje skupiny v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webech v pořadí, v jakém se adresy URL zobrazují v seznamu adres URL.

Nemůžete ale předpovědět pořadí, ve kterém ke stažení skutečně dojde. Po spuštění více skupin jsou všechny úlohy stahování, které generují, všechny aktivní. Nemůžete předpokládat, že A-1 se stáhne před B-1 a nemůžete předpokládat, že A-1 se stáhne před A-2.

#### <a name="global-definitions"></a>Globální definice

Vzorový kód obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

`Task`Proměnná, `pendingWork` , dohlíží na proces zobrazení a zabraňuje všem skupinám v přerušení operace zobrazení jiné skupiny. Proměnná znaku, `group` , označí výstup z různých skupin a ověří tak, že se výsledky zobrazí v očekávaném pořadí.

#### <a name="the-click-event-handler"></a>Obslužná rutina události kliknutí

Obslužná rutina události `StartButton_Click` zvýší počet písmen skupiny pokaždé, když uživatel klikne na tlačítko **Start** . Pak obslužná rutina volá `AccessTheWebAsync` ke spuštění operace stahování.

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

Tento příklad rozdělí `AccessTheWebAsync` do dvou metod. První metoda `AccessTheWebAsync` spustí všechny úlohy stahování pro skupinu a nastaví `pendingWork` pro řízení procesu zobrazení. Metoda používá dotaz integrovaný do jazyka (dotaz LINQ) a <xref:System.Linq.Enumerable.ToArray%2A> ke spuštění všech úloh stažení současně.

`AccessTheWebAsync`pak volá, `FinishOneGroupAsync` aby čekal na dokončení jednotlivých stažení a zobrazila jeho délku.

`FinishOneGroupAsync`Vrátí úkol, který je přiřazen `pendingWork` v `AccessTheWebAsync` . Tato hodnota brání přerušení jinou operací před dokončením úkolu.

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

Tato metoda cyklicky projde úlohy stahování ve skupině, které čekají na každé z nich, zobrazuje délku staženého webu a přidává délku k celkovému součtu.

První příkaz v `FinishOneGroupAsync` používá `pendingWork` k zajištění, že vstup do metody nekoliduje s operací, která je již v procesu zobrazení nebo která již čeká. Pokud taková operace probíhá, musí operace zadání počkat na její zapnutí.

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

Tento příklad můžete spustit vložením změn do kódu v [sestavování aplikace](#BKMK_BuildingTheApp)nebo můžete postupovat podle pokynů v tématu Stažení [aplikace](#BKMK_DownloadingTheApp) pro stažení ukázky a následného spuštění projektu QueueResults.

#### <a name="points-of-interest"></a>Body zájmu

Informační řádky, které začínají znakem křížku (#) ve výstupu objasňují, jak tento příklad funguje.

Výstup ukazuje následující vzory.

- Skupinu lze spustit, když se v předchozí skupině zobrazuje výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.

  ```console
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

- `pendingWork`Úkol je `Nothing` na začátku `FinishOneGroupAsync` pouze pro skupinu a, která začala jako první. Skupina A ještě nedokončila výraz await, když dosáhne `FinishOneGroupAsync` . Proto ovládací prvek nebyl vrácen do `AccessTheWebAsync` a první přiřazení, k němuž došlo, se nezvrátilo `pendingWork` .

- Ve výstupu se vždy zobrazí následující dva řádky společně. Kód se nikdy nepřerušil mezi zahájením operace skupiny v `StartButton_Click` a přiřazením úlohy pro skupinu `pendingWork` .

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  Po zadání skupiny se `StartButton_Click` operace nedokončila ve výrazu await, dokud operace nevstoupí do `FinishOneGroupAsync` . Proto žádná jiná operace nemůže získat řízení během tohoto segmentu kódu.

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a>Kontrola a spuštění ukázkové aplikace

Abyste lépe pochopili ukázkovou aplikaci, můžete si ji stáhnout, sestavit sami nebo si projít kód na konci tohoto tématu bez implementace aplikace.

> [!NOTE]
> Chcete-li spustit příklad jako desktopovou aplikaci Windows Presentation Foundation (WPF), musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a>Stahování aplikace

1. Stáhněte si komprimovaný soubor z [Async Samples: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.

3. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.

4. Přejděte do složky, která obsahuje dekomprimovaný ukázkový kód, a poté otevřete soubor řešení (. sln).

5. V **Průzkumník řešení**otevřete místní nabídku pro projekt, který chcete spustit, a pak zvolte **nastavit jako StartUpProject**.

6. Kliknutím na klávesy CTRL + F5 Sestavte a spusťte projekt.

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a>Sestavování aplikace

Následující část poskytuje kód pro sestavení příkladu jako aplikace WPF.

##### <a name="to-build-a-wpf-app"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V podokně **Nainstalované šablony** rozbalte **Visual Basic**a potom rozbalte **okna**.

4. V seznamu typů projektů vyberte možnost **aplikace WPF**.

5. Pojmenujte projekt `WebsiteDownloadWPF` , zvolte .NET Framework verze 4,6 nebo vyšší a pak klikněte na tlačítko **OK** .

     Nový projekt se zobrazí v **Průzkumník řešení**.

6. V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .

     Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.

7. V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.

    ```xaml
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

     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.

8. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy** a vyberte **Přidat odkaz**.

     Přidejte odkaz pro <xref:System.Net.Http> , pokud již není vybrán.

9. V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.

10. V souboru MainWindow. XAML. vb nahraďte kód následujícím kódem.

    ```vb
    ' Add the following Imports statements, and add a reference for System.Net.Http.
    Imports System.Net.Http
    Imports System.Threading

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
            System.Net.ServicePointManager.SecurityProtocol = System.Net.ServicePointManager.SecurityProtocol Or System.Net.SecurityProtocolType.Tls12

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
                "https://msdn.microsoft.com/library/hh191443.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/jj155761.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/hh524395.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
            Return urls
        End Function

        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)
            ' Display the length of each website. The string format is designed
            ' to be used with a monospaced font, such as Lucida Console or
            ' Global Monospace.

            ' Strip off the "http:'".
            Dim displayURL = url.Replace("https://", "")
            ' Display position in the URL list, the URL, and the number of bytes.
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)
        End Sub
    End Class
    ```

11. Stiskněte klávesy CTRL + F5 ke spuštění programu a pak několikrát zvolte tlačítko **Start** .

12. Proveďte změny z [zakázání tlačítka Start](#BKMK_DisableTheStartButton), [zrušte a restartujte operaci](#BKMK_CancelAndRestart)nebo [Spusťte více operací a](#BKMK_RunMultipleOperations) zaznamenejte výstup pro zpracování Vícenásobný přístup.

## <a name="see-also"></a>Viz také

- [Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](index.md)
