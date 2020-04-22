---
title: Podpora vícenásobného přístupu v aplikacích s modifikátorem Async
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 110298a2ca937dbf39c94cfe9df29afb2e76a91c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021490"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Zpracování reentrancy v asynchronních aplikacích (Visual Basic)

Když do aplikace zahrnete asynchronní kód, měli byste zvážit a případně zabránit reentrancy, což se týká opětovného zadání asynchronní operace před dokončením. Pokud neidentifikujete a nezpracováváte možnosti reentrancy, může to způsobit neočekávané výsledky.

> [!NOTE]
> Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

> [!NOTE]
> Zabezpečení transportní vrstvy (TLS) verze 1.2 je nyní minimální verze, která se má použít ve vývoji aplikace. Pokud vaše aplikace cílí na verzi rozhraní .NET Framework starší než 4.7, přečtěte si následující článek o [doporučených postupech zabezpečení transportní vrstvy (TLS) pomocí rozhraní .NET Framework](../../../../framework/network-programming/tls.md).

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a>Rozpoznání reentrancy

V příkladu v tomto tématu uživatelé zvolí tlačítko **Start** pro spuštění asynchronní aplikace, která stáhne řadu webů a vypočítá celkový počet stažených bajtů. Synchronní verze příkladu by reagovat stejným způsobem bez ohledu na to, kolikrát uživatel zvolí tlačítko, protože po prvním, vlákno uživatelského rozhraní ignoruje tyto události, dokud aplikace dokončí spuštění. V asynchronní aplikaci však vlákno uživatelského rozhraní nadále reaguje a můžete znovu zadat asynchronní operaci před dokončením.

Následující příklad ukazuje očekávaný výstup, pokud uživatel zvolí tlačítko **Start** pouze jednou. Zobrazí se seznam stažených webů s velikostí jednotlivých webů v bajtech. Celkový počet bajtů se zobrazí na konci.

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

Pokud však uživatel zvolí tlačítko více než jednou, obslužná rutina události je vyvolána opakovaně a proces stahování je pokaždé znovu zadán. Výsledkem je několik asynchronních operací současně, výstup propojí výsledky a celkový počet bajtů je matoucí.

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

Můžete zkontrolovat kód, který vytváří tento výstup posouváním na konec tohoto tématu. S kódem můžete experimentovat stažením řešení do místního počítače a spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu k vytvoření vlastního projektu Další informace a pokyny naleznete v [tématu Revize a spuštění aplikace Example .](#BKMD_SettingUpTheExample)

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a>Manipulace s reentrancy

Reentrancy můžete zpracovat různými způsoby v závislosti na tom, co chcete, aby vaše aplikace dělat. Toto téma uvádí následující příklady:

- [Zakázání tlačítka Start](#BKMK_DisableTheStartButton)

  Zakažte tlačítko **Start,** když je operace spuštěna, aby ji uživatel nemohl přerušit.

- [Zrušit a restartovat operaci](#BKMK_CancelAndRestart)

  Zrušte všechny operace, které jsou stále spuštěny, když uživatel znovu vybere tlačítko **Start,** a potom nechte naposledy požadovanou operaci pokračovat.

- [Spuštění více operací a fronty výstupu](#BKMK_RunMultipleOperations)

  Povolit všechny požadované operace spustit asynchronně, ale koordinovat zobrazení výstupu tak, aby výsledky z každé operace se zobrazí společně a v pořadí.

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a>Zakázání tlačítka Start

Tlačítko **Start** můžete blokovat v době, kdy je spuštěna operace, zakázáním tlačítka v horní části obslužné rutiny `StartButton_Click` události. Po dokončení operace pak můžete `Finally` znovu povolit tlačítko z bloku, aby uživatelé mohli aplikaci znovu spustit.

Následující kód ukazuje tyto změny, které jsou označeny hvězdičkami. Můžete přidat změny kódu na konci tohoto tématu, nebo si můžete stáhnout dokončenou aplikaci z [Async Samples: Reentrancy v .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název projektu je DisableStartButton.

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

V důsledku změn tlačítko nereaguje při `AccessTheWebAsync` stahování webových stránek, takže proces nelze znovu zadat.

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a>Zrušit a restartovat operaci

Místo zakázání tlačítka **Start** můžete ponechat tlačítko aktivní, ale pokud uživatel toto tlačítko znovu zvolí, zrušte operaci, která je již spuštěna, a nechte pokračovat v naposledy zahájené operaci.

Další informace o zrušení naleznete v [tématu Jemné doladění asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).

Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [revizi a spuštění aplikace Příklad](#BKMD_SettingUpTheExample). Hotovou aplikaci si můžete také stáhnout z [aplikace Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název tohoto projektu je CancelAndRestart.

1. Deklarovat proměnnou <xref:System.Threading.CancellationTokenSource> , `cts`která je v oboru pro všechny metody.

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. V `StartButton_Click`aplikaci určete, zda operace již probíhá. Pokud `cts` je `Nothing`hodnota , žádná operace je již aktivní. Pokud hodnota není `Nothing`, operace, která je již spuštěna, je zrušena.

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

4. Na konci `StartButton_Click`, aktuální proces je dokončen, takže `cts` nastavte `Nothing`hodnotu zpět na .

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

Následující kód zobrazuje všechny `StartButton_Click`změny v . Přídavky jsou označeny hvězdičkami.

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

- Přidejte parametr pro přijetí `StartButton_Click`tokenu zrušení z .

- Pomocí <xref:System.Net.Http.HttpClient.GetAsync%2A> této metody stáhněte `GetAsync` weby, protože přijímá <xref:System.Threading.CancellationToken> argument.

- Před `DisplayResults` voláním za účelem zobrazení výsledků `ct` pro každý stažený web zkontrolujte, zda nebyla aktuální operace zrušena.

 Následující kód ukazuje tyto změny, které jsou označeny hvězdičkami.

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

Pokud zvolíte tlačítko **Start** několikrát, když je tato aplikace spuštěna, mělo by to přinést výsledky, které se podobají následujícímu výstupu:

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

Chcete-li odstranit částečné seznamy, odkomentujte první řádek `StartButton_Click` kódu, abyste zrušili textové pole při každém restartování operace uživatelem.

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a>Spuštění více operací a fronty výstupu

Tento třetí příklad je nejsložitější v tom, že aplikace spustí další asynchronní operaci pokaždé, když uživatel zvolí tlačítko **Start** a všechny operace spustit až do konce. Všechny požadované operace stáhnout weby ze seznamu asynchronně, ale výstup z operací je prezentován akvenční. To znamená, že skutečná aktivita stahování je prokládána, jak ukazuje výstup v [rozpoznávání reentrancy,](#BKMK_RecognizingReentrancy) ale seznam výsledků pro každou skupinu je uveden samostatně.

Operace sdílejí globální <xref:System.Threading.Tasks.Task> `pendingWork`, , který slouží jako gatekeeper pro proces zobrazení.

Tento příklad můžete spustit vložením změny do kódu v [sestavení aplikace](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [stažení aplikace](#BKMK_DownloadingTheApp) stáhnout ukázku a potom spustit projekt QueueResults.

Následující výstup ukazuje výsledek, pokud uživatel zvolí tlačítko **Start** pouze jednou. Popisek písmene A označuje, že výsledek je od prvního výběru tlačítka **Start.** Čísla zobrazují pořadí adres URL v seznamu cílů stahování.

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

Pokud uživatel třikrát zvolí tlačítko **Start,** aplikace vytvoří výstup, který se podobá následujícím řádkům. Informační řádky, které začínají znakem libry (#), sledují průběh aplikace.

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

Skupiny B a C začínají před dokončením skupiny A, ale výstup pro každou skupinu se zobrazí samostatně. Nejprve se zobrazí veškerý výstup pro skupinu A následovaný veškerým výstupem pro skupinu B a potom veškerým výstupem pro skupinu C. Aplikace vždy zobrazuje skupiny v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webech v pořadí, v jakém se adresy URL zobrazují v seznamu adres URL.

Nelze však předpovědět pořadí, ve kterém ke stažení skutečně dochází. Po spuštění více skupin jsou všechny úlohy stahování, které generují, aktivní. Nemůžete předpokládat, že A-1 bude stažen před B-1, a nemůžete předpokládat, že A-1 bude staženpřed A-2.

#### <a name="global-definitions"></a>Globální definice

Ukázkový kód obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

Proměnná `Task` `pendingWork`, dohlíží na proces zobrazení a zabraňuje jakékoli skupině přerušit operaci zobrazení jiné skupiny. Znaková proměnná , `group`označuje výstup z různých skupin, aby ověřila, že se výsledky zobrazí v očekávaném pořadí.

#### <a name="the-click-event-handler"></a>Obslužná rutina události kliknutí

Obslužná rutina události , `StartButton_Click`zintáží skupinové písmeno pokaždé, když uživatel zvolí tlačítko **Start.** Potom obslužná rutina volá `AccessTheWebAsync` ke spuštění operace stahování.

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

Tento příklad `AccessTheWebAsync` se rozdělí na dvě metody. První metoda `AccessTheWebAsync`, spustí všechny úlohy stahování pro `pendingWork` skupinu a nastaví řízení procesu zobrazení. Metoda používá jazyk integrovaný dotaz (dotaz <xref:System.Linq.Enumerable.ToArray%2A> LINQ) a spustit všechny úlohy stahování ve stejnou dobu.

`AccessTheWebAsync`pak `FinishOneGroupAsync` volá čekat na dokončení každého stažení a zobrazit jeho délku.

`FinishOneGroupAsync`vrátí úkol, který je `pendingWork` `AccessTheWebAsync`přiřazen v aplikaci . Tato hodnota zabraňuje přerušení jinou operací před dokončením úlohy.

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

Tato metoda cyklicky prochází úlohy stahování ve skupině, čeká na každou z nich, zobrazuje délku staženého webu a přidává délku k celkovému součtu.

První příkaz `FinishOneGroupAsync` v `pendingWork` používá k ujistěte se, že zadání metody není v rozporu s operací, která je již v procesu zobrazení nebo který je již čeká. Pokud taková operace probíhá, musí zadávacího řízení počkat, až přijde na řadu.

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

Tento příklad můžete spustit vložením změny do kódu v [sestavení aplikace](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [stažení aplikace](#BKMK_DownloadingTheApp) ke stažení ukázky a potom spusťte projekt QueueResults.

#### <a name="points-of-interest"></a>Body zájmu

Informační řádky, které začínají znakem libry (#) ve výstupu, objasňují, jak tento příklad funguje.

Výstup ukazuje následující vzory.

- Skupinu lze spustit, zatímco předchozí skupina zobrazuje svůj výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.

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

- Úkol `pendingWork` je `Nothing` na začátku pouze pro skupinu `FinishOneGroupAsync` A, která byla zahájena jako první. Skupina A ještě nedokončila výraz čekání, `FinishOneGroupAsync`jakmile dosáhne . Proto ovládací prvek nebyl `AccessTheWebAsync`vrácen do , `pendingWork` a první přiřazení do nedošlo.

- Následující dva řádky se vždy zobrazí společně ve výstupu. Kód není nikdy přerušen mezi spuštěním `StartButton_Click` operace skupiny v aplikaci `pendingWork`a přiřazením úkolu pro skupinu .

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  Po zadání skupiny `StartButton_Click`operace nedokončí výraz čekání, dokud operace `FinishOneGroupAsync`nevstoupí . Proto žádná jiná operace může získat kontrolu během tohoto segmentu kódu.

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a>Kontrola a spuštění ukázkové aplikace

Chcete-li lépe porozumět ukázkové aplikaci, můžete si ji stáhnout, vytvořit sami nebo zkontrolovat kód na konci tohoto tématu bez implementace aplikace.

> [!NOTE]
> Chcete-li spustit příklad jako desktopovou aplikaci WPF (Windows Presentation Foundation), musíte mít v počítači nainstalovanou visual studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější.

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a>Stažení aplikace

1. Stáhněte si komprimovaný soubor z [ukázky asynchronní: Reentrancy v .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.

3. Na řádku nabídek zvolte **Soubor**, **Otevřít**, **Projekt/Řešení**.

4. Přejděte do složky, která obsahuje dekomprimovaný ukázkový kód, a otevřete soubor řešení (.sln).

5. V **Průzkumníku řešení**otevřete místní nabídku projektu, který chcete spustit, a pak zvolte **Nastavit jako StartUpProject**.

6. Zvolte klávesy CTRL+F5 pro sestavení a spuštění projektu.

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a>Vytváření aplikace

Následující část obsahuje kód pro sestavení příkladu jako aplikace WPF.

##### <a name="to-build-a-wpf-app"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. Na řádku nabídek zvolte **Soubor**, **Nový**, **Projekt**.

     Otevře se dialogové okno **Nový projekt.**

3. V podokně **Nainstalované šablony** rozbalte **položku Visual Basic**a potom rozbalte **položku Windows**.

4. V seznamu typů projektů zvolte **WPF Aplikace**.

5. Pojmenujte `WebsiteDownloadWPF`projekt , zvolte verzi rozhraní .NET Framework verze 4.6 nebo vyšší a klepněte na tlačítko **OK.**

     Nový projekt se zobrazí v **Průzkumníku řešení**.

6. V Editoru kódu Visual Studia zvolte kartu **MainWindow.xaml.**

     Pokud karta není viditelná, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a pak zvolte **Zobrazit kód**.

7. V zobrazení **XAML** MainWindow.xaml nahraďte kód následujícím kódem.

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

     Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhovém** zobrazení MainWindow.xaml.

8. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **odkaz odkazy** a vyberte přidat **odkaz**.

     Přidejte odkaz <xref:System.Net.Http>pro , pokud ještě není vybrán.

9. V **Průzkumníku řešení**otevřete místní nabídku pro soubor MainWindow.xaml.vb a pak zvolte **Zobrazit kód**.

10. V souboru MainWindow.xaml.vb nahraďte kód následujícím kódem.

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

11. Chcete-li spustit program, zvolte klávesy CTRL+F5 a pak několikrát zvolte tlačítko **Start.**

12. Proveďte změny z [funkce Zakázat tlačítko Start](#BKMK_DisableTheStartButton), Zrušit a [restartovat operaci](#BKMK_CancelAndRestart)nebo [Spusťte více operací a zařazujte výstup](#BKMK_RunMultipleOperations) do fronty, abyste zpracovat reentrancy.

## <a name="see-also"></a>Viz také

- [Návod: Přístup k webu pomocí asynchronní a čeká (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování s asynchronní a čeká (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
