---
title: Zpracování Vícenásobný přístup v asynchronních aplikacích (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 199b7ce2cb8b3f3b8e220f9e2bab7e9c39a8d033
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351985"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="a0901-102">Zpracování Vícenásobný přístup v asynchronních aplikacích (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0901-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>

<span data-ttu-id="a0901-103">Při zahrnutí asynchronního kódu do aplikace byste měli zvážit a případně zabránit Vícenásobný přístup, která označuje, že se má znovu zadat asynchronní operace předtím, než se dokončí.</span><span class="sxs-lookup"><span data-stu-id="a0901-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="a0901-104">Pokud neidentifikujete a nezpracováváte možnosti pro Vícenásobný přístup, může dojít k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="a0901-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

> [!NOTE]
> <span data-ttu-id="a0901-105">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a0901-105">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="a0901-106">Rozpoznávání Vícenásobný přístup</span><span class="sxs-lookup"><span data-stu-id="a0901-106">Recognizing Reentrancy</span></span>

<span data-ttu-id="a0901-107">V příkladu v tomto tématu uživatelé zvolí tlačítko **Spustit** pro zahájení asynchronní aplikace, která stáhne řadu webů a vypočítá celkový počet stažených bajtů.</span><span class="sxs-lookup"><span data-stu-id="a0901-107">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="a0901-108">Synchronní verze příkladu by reagovala stejným způsobem bez ohledu na to, kolikrát uživatel vybere tlačítko, protože po prvním spuštění vlákno UI tyto události ignoruje, dokud se aplikace nedokončí.</span><span class="sxs-lookup"><span data-stu-id="a0901-108">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="a0901-109">V asynchronní aplikaci ale vlákno uživatelského rozhraní nadále reaguje a před dokončením můžete znovu zadat asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="a0901-109">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="a0901-110">Následující příklad ukazuje očekávaný výstup, pokud uživatel klikne na tlačítko **Start** pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a0901-110">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="a0901-111">Seznam stažených webů se zobrazí v bajtech v bajtech každé lokality.</span><span class="sxs-lookup"><span data-stu-id="a0901-111">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="a0901-112">Celkový počet bajtů se zobrazí na konci.</span><span class="sxs-lookup"><span data-stu-id="a0901-112">The total number of bytes appears at the end.</span></span>

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

<span data-ttu-id="a0901-113">Pokud však uživatel zvolí tlačítko více než jednou, obslužná rutina události je vyvolána opakovaně a proces stahování je znovu zadán pokaždé.</span><span class="sxs-lookup"><span data-stu-id="a0901-113">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="a0901-114">Výsledkem je, že několik asynchronních operací je současně spuštěno, výstup vynechává výsledky a celkový počet bajtů je matoucí.</span><span class="sxs-lookup"><span data-stu-id="a0901-114">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

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

<span data-ttu-id="a0901-115">Můžete zkontrolovat kód, který vytváří tento výstup posouváním na konec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a0901-115">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="a0901-116">Můžete experimentovat s kódem stažením řešení do místního počítače a pak spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu vytvořit vlastní projekt pro další informace a pokyny naleznete v tématu [Kontrola a Spouští se ukázková aplikace](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="a0901-116">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="a0901-117">Zpracování Vícenásobný přístup</span><span class="sxs-lookup"><span data-stu-id="a0901-117">Handling Reentrancy</span></span>

<span data-ttu-id="a0901-118">V závislosti na tom, co má vaše aplikace dělat, můžete Vícenásobný přístup zpracovávat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="a0901-118">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="a0901-119">Toto téma nabízí následující příklady:</span><span class="sxs-lookup"><span data-stu-id="a0901-119">This topic presents the following examples:</span></span>

- [<span data-ttu-id="a0901-120">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="a0901-120">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="a0901-121">Zakáže tlačítko **Start** , když je operace spuštěná, aby ji uživatel nemohl přerušit.</span><span class="sxs-lookup"><span data-stu-id="a0901-121">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="a0901-122">Zrušení a restartování operace</span><span class="sxs-lookup"><span data-stu-id="a0901-122">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="a0901-123">Zrušte všechny operace, které pořád běží, když uživatel znovu zvolí tlačítko **Start** , a pak nechte poslední vyžadovanou operaci pokračovat.</span><span class="sxs-lookup"><span data-stu-id="a0901-123">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="a0901-124">Spuštění více operací a zařazení výstupu do fronty</span><span class="sxs-lookup"><span data-stu-id="a0901-124">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="a0901-125">Povolí asynchronní spouštění všech požadovaných operací, ale koordinuje zobrazení výstupu, aby se výsledky jednotlivých operací zobrazovaly společně a v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a0901-125">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="a0901-126">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="a0901-126">Disable the Start Button</span></span>

<span data-ttu-id="a0901-127">Tlačítko **Start** lze zablokovat, když je operace spuštěna, zakázáním tlačítka v horní části obslužné rutiny události `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="a0901-127">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="a0901-128">Pak můžete znovu povolit tlačítko z bloku `Finally` po dokončení operace, aby uživatelé mohli aplikaci znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="a0901-128">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="a0901-129">Následující kód zobrazuje tyto změny, které jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="a0901-129">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="a0901-130">Změny můžete přidat do kódu na konci tohoto tématu nebo si můžete stáhnout hotovou aplikaci z ukázek [Async: Vícenásobný přístup v desktopových aplikacích .NET @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="a0901-130">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="a0901-131">Název projektu je DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="a0901-131">The project name is DisableStartButton.</span></span>

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

<span data-ttu-id="a0901-132">V důsledku změn tlačítko nereaguje, když `AccessTheWebAsync` stahuje weby, takže se tento proces nedá znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="a0901-132">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="BKMK_CancelAndRestart"></a><span data-ttu-id="a0901-133">Zrušení a restartování operace</span><span class="sxs-lookup"><span data-stu-id="a0901-133">Cancel and Restart the Operation</span></span>

<span data-ttu-id="a0901-134">Místo zakázání tlačítka **Start** můžete ponechat tlačítko aktivní, ale pokud uživatel toto tlačítko zvolí znovu, zrušte operaci, která už je spuštěná, a nechejte operaci naposledy spuštěnou.</span><span class="sxs-lookup"><span data-stu-id="a0901-134">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="a0901-135">Další informace o zrušení najdete v tématu [jemné vyladění aplikace Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="a0901-135">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="a0901-136">Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [části Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="a0901-136">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="a0901-137">Hotovou aplikaci si můžete stáhnout také z ukázek [Async: Vícenásobný přístup v desktopových aplikacích .NET @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="a0901-137">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="a0901-138">Název tohoto projektu je CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="a0901-138">The name of this project is CancelAndRestart.</span></span>

1. <span data-ttu-id="a0901-139">Deklarujte proměnnou <xref:System.Threading.CancellationTokenSource> `cts`, která je v oboru pro všechny metody.</span><span class="sxs-lookup"><span data-stu-id="a0901-139">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="a0901-140">V `StartButton_Click` určete, zda operace již probíhá.</span><span class="sxs-lookup"><span data-stu-id="a0901-140">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="a0901-141">Pokud je hodnota `cts` `Nothing`, již žádná operace není aktivní.</span><span class="sxs-lookup"><span data-stu-id="a0901-141">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="a0901-142">Pokud hodnota není `Nothing`, operace, která je již spuštěna, je zrušena.</span><span class="sxs-lookup"><span data-stu-id="a0901-142">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. <span data-ttu-id="a0901-143">Nastavte `cts` na jinou hodnotu, která představuje aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="a0901-143">Set `cts` to a different value that represents the current process.</span></span>

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. <span data-ttu-id="a0901-144">Na konci `StartButton_Click` se aktuální proces dokončí, takže nastavte hodnotu `cts` zpět na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a0901-144">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

<span data-ttu-id="a0901-145">Následující kód ukazuje všechny změny v `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="a0901-145">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="a0901-146">Přidané položky jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="a0901-146">The additions are marked with asterisks.</span></span>

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

<span data-ttu-id="a0901-147">V `AccessTheWebAsync` proveďte následující změny.</span><span class="sxs-lookup"><span data-stu-id="a0901-147">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="a0901-148">Přidejte parametr pro přijetí tokenu zrušení z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="a0901-148">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="a0901-149">Použijte metodu <xref:System.Net.Http.HttpClient.GetAsync%2A> ke stažení webů, protože `GetAsync` přijímá argument <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="a0901-149">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="a0901-150">Před voláním `DisplayResults` pro zobrazení výsledků pro každý stažený web zkontrolujte `ct` a ověřte, zda aktuální operace nebyla zrušena.</span><span class="sxs-lookup"><span data-stu-id="a0901-150">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

 <span data-ttu-id="a0901-151">Následující kód zobrazuje tyto změny, které jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="a0901-151">The following code shows these changes, which are marked with asterisks.</span></span>

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

<span data-ttu-id="a0901-152">Pokud při spuštění této aplikace několikrát kliknete na tlačítko **Start** , mělo by se jednat o výsledky, které se podobají následujícímu výstupu:</span><span class="sxs-lookup"><span data-stu-id="a0901-152">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output:</span></span>

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

<span data-ttu-id="a0901-153">Chcete-li odstranit částečné seznamy, odkomentujte první řádek kódu v `StartButton_Click`, chcete-li vymazat textové pole pokaždé, když uživatel operaci restartuje.</span><span class="sxs-lookup"><span data-stu-id="a0901-153">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="a0901-154">Spuštění více operací a zařazení výstupu do fronty</span><span class="sxs-lookup"><span data-stu-id="a0901-154">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="a0901-155">Tento třetí příklad je nejsložitější v tom, že aplikace spouští další asynchronní operace pokaždé, když uživatel zvolí tlačítko **Start** , a všechny operace, které se spouštějí k dokončení.</span><span class="sxs-lookup"><span data-stu-id="a0901-155">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="a0901-156">Všechny požadované operace stahují weby ze seznamu asynchronně, ale výstup z operací je prezentován sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="a0901-156">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="a0901-157">To znamená, že se aktuální aktivita stahování prochází, protože se zobrazuje výstup v [rozpoznávání Vícenásobný přístup](#BKMK_RecognizingReentrancy) , ale seznam výsledků pro každou skupinu se zobrazí samostatně.</span><span class="sxs-lookup"><span data-stu-id="a0901-157">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="a0901-158">Operace sdílí globální <xref:System.Threading.Tasks.Task> `pendingWork`, který slouží jako server gatekeeper pro proces zobrazení.</span><span class="sxs-lookup"><span data-stu-id="a0901-158">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="a0901-159">Tento příklad můžete spustit vložením změn do kódu v [sestavování aplikace](#BKMK_BuildingTheApp)nebo můžete postupovat podle pokynů v tématu Stažení [aplikace](#BKMK_DownloadingTheApp) ke stažení ukázky a spuštění projektu QueueResults.</span><span class="sxs-lookup"><span data-stu-id="a0901-159">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>

<span data-ttu-id="a0901-160">Následující výstup ukazuje výsledek, pokud uživatel zvolí tlačítko **Start** pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a0901-160">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="a0901-161">Označení písmenem (a) označuje, že výsledek je od první zvolené tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="a0901-161">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="a0901-162">Čísla zobrazují pořadí adres URL v seznamu cílů stahování.</span><span class="sxs-lookup"><span data-stu-id="a0901-162">The numbers show the order of the URLs in the list of download targets.</span></span>

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

<span data-ttu-id="a0901-163">Pokud uživatel třikrát zvolí tlačítko **Start** , aplikace vytvoří výstup podobný následujícímu řádku.</span><span class="sxs-lookup"><span data-stu-id="a0901-163">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="a0901-164">Informační řádky, které začínají znakem křížku (#) sledují průběh aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0901-164">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

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

<span data-ttu-id="a0901-165">Skupiny B a C se spustí před dokončením skupiny A, ale výstup pro každou skupinu se zobrazí samostatně.</span><span class="sxs-lookup"><span data-stu-id="a0901-165">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="a0901-166">Nejprve se zobrazí celý výstup pro skupinu A následovaný celým výstupem pro skupinu B a pak všechny výstupy pro skupinu C. Aplikace vždy zobrazuje skupiny v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webech v pořadí, v jakém se adresy URL zobrazují v seznamu adres URL.</span><span class="sxs-lookup"><span data-stu-id="a0901-166">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="a0901-167">Nemůžete ale předpovědět pořadí, ve kterém ke stažení skutečně dojde.</span><span class="sxs-lookup"><span data-stu-id="a0901-167">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="a0901-168">Po spuštění více skupin jsou všechny úlohy stahování, které generují, všechny aktivní.</span><span class="sxs-lookup"><span data-stu-id="a0901-168">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="a0901-169">Nemůžete předpokládat, že A-1 se stáhne před B-1 a nemůžete předpokládat, že A-1 se stáhne před A-2.</span><span class="sxs-lookup"><span data-stu-id="a0901-169">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="a0901-170">Globální definice</span><span class="sxs-lookup"><span data-stu-id="a0901-170">Global Definitions</span></span>

<span data-ttu-id="a0901-171">Vzorový kód obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.</span><span class="sxs-lookup"><span data-stu-id="a0901-171">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

<span data-ttu-id="a0901-172">Proměnná `Task`, `pendingWork`, dohlíží na proces zobrazení a zabraňuje všem skupinám v přerušení operace zobrazení jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="a0901-172">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="a0901-173">Znaková proměnná `group` označí výstup z různých skupin a ověří tak, že se výsledky zobrazí v očekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a0901-173">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="a0901-174">Obslužná rutina události kliknutí</span><span class="sxs-lookup"><span data-stu-id="a0901-174">The Click Event Handler</span></span>

<span data-ttu-id="a0901-175">Obslužná rutina události `StartButton_Click` zvýší písmeno skupiny pokaždé, když uživatel klikne na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="a0901-175">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="a0901-176">Obslužná rutina pak zavolá `AccessTheWebAsync` ke spuštění operace stahování.</span><span class="sxs-lookup"><span data-stu-id="a0901-176">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

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

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="a0901-177">Metoda AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="a0901-177">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="a0901-178">Tento příklad rozdělí `AccessTheWebAsync` do dvou metod.</span><span class="sxs-lookup"><span data-stu-id="a0901-178">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="a0901-179">První metoda, `AccessTheWebAsync`, spustí všechny úlohy stažení pro skupinu a nastaví `pendingWork` pro řízení procesu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="a0901-179">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="a0901-180">Metoda používá dotaz založený na jazyce (LINQ Query) a <xref:System.Linq.Enumerable.ToArray%2A> ke spuštění všech úloh stažení současně.</span><span class="sxs-lookup"><span data-stu-id="a0901-180">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="a0901-181">`AccessTheWebAsync` potom zavolá `FinishOneGroupAsync`, aby čekal na dokončení jednotlivých stažení a zobrazila jeho délku.</span><span class="sxs-lookup"><span data-stu-id="a0901-181">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="a0901-182">`FinishOneGroupAsync` vrátí úkol, který je přiřazen `pendingWork` v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="a0901-182">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="a0901-183">Tato hodnota brání přerušení jinou operací před dokončením úkolu.</span><span class="sxs-lookup"><span data-stu-id="a0901-183">That value prevents interruption by another operation before the task is complete.</span></span>

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

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="a0901-184">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="a0901-184">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="a0901-185">Tato metoda cyklicky projde úlohy stahování ve skupině, které čekají na každé z nich, zobrazuje délku staženého webu a přidává délku k celkovému součtu.</span><span class="sxs-lookup"><span data-stu-id="a0901-185">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="a0901-186">První příkaz v `FinishOneGroupAsync` používá `pendingWork` k ujištění, že vstup do metody nekoliduje s operací, která je již v procesu zobrazení, nebo už čeká.</span><span class="sxs-lookup"><span data-stu-id="a0901-186">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="a0901-187">Pokud taková operace probíhá, musí operace zadání počkat na její zapnutí.</span><span class="sxs-lookup"><span data-stu-id="a0901-187">If such an operation is in progress, the entering operation must wait its turn.</span></span>

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

<span data-ttu-id="a0901-188">Tento příklad můžete spustit vložením změn do kódu v [sestavování aplikace](#BKMK_BuildingTheApp)nebo můžete postupovat podle pokynů v tématu Stažení [aplikace](#BKMK_DownloadingTheApp) pro stažení ukázky a následného spuštění projektu QueueResults.</span><span class="sxs-lookup"><span data-stu-id="a0901-188">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>

#### <a name="points-of-interest"></a><span data-ttu-id="a0901-189">Body zájmu</span><span class="sxs-lookup"><span data-stu-id="a0901-189">Points of Interest</span></span>

<span data-ttu-id="a0901-190">Informační řádky, které začínají znakem křížku (#) ve výstupu objasňují, jak tento příklad funguje.</span><span class="sxs-lookup"><span data-stu-id="a0901-190">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="a0901-191">Výstup ukazuje následující vzory.</span><span class="sxs-lookup"><span data-stu-id="a0901-191">The output shows the following patterns.</span></span>

- <span data-ttu-id="a0901-192">Skupinu lze spustit, když se v předchozí skupině zobrazuje výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.</span><span class="sxs-lookup"><span data-stu-id="a0901-192">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

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

- <span data-ttu-id="a0901-193">Úloha `pendingWork` je `Nothing` na začátku `FinishOneGroupAsync` pouze pro skupinu A, která začala jako první.</span><span class="sxs-lookup"><span data-stu-id="a0901-193">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="a0901-194">Skupina A ještě nedokončila výraz await, když dosáhne `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="a0901-194">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="a0901-195">Proto ovládací prvek nebyl vrácen do `AccessTheWebAsync` a první přiřazení `pendingWork` neproběhlo.</span><span class="sxs-lookup"><span data-stu-id="a0901-195">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="a0901-196">Ve výstupu se vždy zobrazí následující dva řádky společně.</span><span class="sxs-lookup"><span data-stu-id="a0901-196">The following two lines always appear together in the output.</span></span> <span data-ttu-id="a0901-197">Kód se nikdy nepřerušil mezi zahájením operace skupiny v `StartButton_Click` a přiřazením úlohy pro skupinu `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="a0901-197">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  <span data-ttu-id="a0901-198">Po zadání skupiny `StartButton_Click` operace nekončí výraz await, dokud operace nevstoupí `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="a0901-198">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="a0901-199">Proto žádná jiná operace nemůže získat řízení během tohoto segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="a0901-199">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="a0901-200">Kontrola a spuštění ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="a0901-200">Reviewing and Running the Example App</span></span>

<span data-ttu-id="a0901-201">Abyste lépe pochopili ukázkovou aplikaci, můžete si ji stáhnout, sestavit sami nebo si projít kód na konci tohoto tématu bez implementace aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0901-201">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="a0901-202">Chcete-li spustit příklad jako desktopovou aplikaci Windows Presentation Foundation (WPF), musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a0901-202">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="a0901-203">Stahování aplikace</span><span class="sxs-lookup"><span data-stu-id="a0901-203">Downloading the App</span></span>

1. <span data-ttu-id="a0901-204">Stáhněte si komprimovaný soubor z ukázek [Async: Vícenásobný přístup v desktopových aplikacích .NET @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="a0901-204">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="a0901-205">Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0901-205">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="a0901-206">Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="a0901-206">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="a0901-207">Přejděte do složky, která obsahuje dekomprimovaný ukázkový kód, a poté otevřete soubor řešení (. sln).</span><span class="sxs-lookup"><span data-stu-id="a0901-207">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="a0901-208">V **Průzkumník řešení**otevřete místní nabídku pro projekt, který chcete spustit, a pak zvolte **nastavit jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="a0901-208">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="a0901-209">Kliknutím na klávesy CTRL + F5 Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="a0901-209">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="BKMK_BuildingTheApp"></a><span data-ttu-id="a0901-210">Sestavování aplikace</span><span class="sxs-lookup"><span data-stu-id="a0901-210">Building the App</span></span>

<span data-ttu-id="a0901-211">Následující část poskytuje kód pro sestavení příkladu jako aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="a0901-211">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="a0901-212">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="a0901-212">To build a WPF app</span></span>

1. <span data-ttu-id="a0901-213">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0901-213">Start Visual Studio.</span></span>

2. <span data-ttu-id="a0901-214">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a0901-214">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="a0901-215">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a0901-215">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="a0901-216">V podokně **Nainstalované šablony** rozbalte **Visual Basic**a potom rozbalte **okna**.</span><span class="sxs-lookup"><span data-stu-id="a0901-216">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="a0901-217">V seznamu typů projektů vyberte možnost **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="a0901-217">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="a0901-218">Pojmenujte projekt `WebsiteDownloadWPF` a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="a0901-218">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="a0901-219">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="a0901-219">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="a0901-220">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="a0901-220">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="a0901-221">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a0901-221">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="a0901-222">V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="a0901-222">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="a0901-223">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="a0901-223">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="a0901-224">Přidejte odkaz na <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="a0901-224">Add a reference for <xref:System.Net.Http>.</span></span>

9. <span data-ttu-id="a0901-225">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a0901-225">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

10. <span data-ttu-id="a0901-226">V souboru MainWindow. XAML. vb nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="a0901-226">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

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

11. <span data-ttu-id="a0901-227">Stiskněte klávesy CTRL + F5 ke spuštění programu a pak několikrát zvolte tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="a0901-227">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="a0901-228">Proveďte změny z [zakázání tlačítka Start](#BKMK_DisableTheStartButton), [zrušte a restartujte operaci](#BKMK_CancelAndRestart)nebo [Spusťte více operací a](#BKMK_RunMultipleOperations) zaznamenejte výstup pro zpracování Vícenásobný přístup.</span><span class="sxs-lookup"><span data-stu-id="a0901-228">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0901-229">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0901-229">See also</span></span>

- [<span data-ttu-id="a0901-230">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="a0901-230">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="a0901-231">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0901-231">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
