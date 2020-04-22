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
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="7b71e-102">Zpracování reentrancy v asynchronních aplikacích (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b71e-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>

<span data-ttu-id="7b71e-103">Když do aplikace zahrnete asynchronní kód, měli byste zvážit a případně zabránit reentrancy, což se týká opětovného zadání asynchronní operace před dokončením.</span><span class="sxs-lookup"><span data-stu-id="7b71e-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="7b71e-104">Pokud neidentifikujete a nezpracováváte možnosti reentrancy, může to způsobit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="7b71e-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

> [!NOTE]
> <span data-ttu-id="7b71e-105">Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="7b71e-105">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="7b71e-106">Zabezpečení transportní vrstvy (TLS) verze 1.2 je nyní minimální verze, která se má použít ve vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b71e-106">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="7b71e-107">Pokud vaše aplikace cílí na verzi rozhraní .NET Framework starší než 4.7, přečtěte si následující článek o [doporučených postupech zabezpečení transportní vrstvy (TLS) pomocí rozhraní .NET Framework](../../../../framework/network-programming/tls.md).</span><span class="sxs-lookup"><span data-stu-id="7b71e-107">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="7b71e-108">Rozpoznání reentrancy</span><span class="sxs-lookup"><span data-stu-id="7b71e-108">Recognizing Reentrancy</span></span>

<span data-ttu-id="7b71e-109">V příkladu v tomto tématu uživatelé zvolí tlačítko **Start** pro spuštění asynchronní aplikace, která stáhne řadu webů a vypočítá celkový počet stažených bajtů.</span><span class="sxs-lookup"><span data-stu-id="7b71e-109">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="7b71e-110">Synchronní verze příkladu by reagovat stejným způsobem bez ohledu na to, kolikrát uživatel zvolí tlačítko, protože po prvním, vlákno uživatelského rozhraní ignoruje tyto události, dokud aplikace dokončí spuštění.</span><span class="sxs-lookup"><span data-stu-id="7b71e-110">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="7b71e-111">V asynchronní aplikaci však vlákno uživatelského rozhraní nadále reaguje a můžete znovu zadat asynchronní operaci před dokončením.</span><span class="sxs-lookup"><span data-stu-id="7b71e-111">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="7b71e-112">Následující příklad ukazuje očekávaný výstup, pokud uživatel zvolí tlačítko **Start** pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="7b71e-112">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="7b71e-113">Zobrazí se seznam stažených webů s velikostí jednotlivých webů v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7b71e-113">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="7b71e-114">Celkový počet bajtů se zobrazí na konci.</span><span class="sxs-lookup"><span data-stu-id="7b71e-114">The total number of bytes appears at the end.</span></span>

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

<span data-ttu-id="7b71e-115">Pokud však uživatel zvolí tlačítko více než jednou, obslužná rutina události je vyvolána opakovaně a proces stahování je pokaždé znovu zadán.</span><span class="sxs-lookup"><span data-stu-id="7b71e-115">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="7b71e-116">Výsledkem je několik asynchronních operací současně, výstup propojí výsledky a celkový počet bajtů je matoucí.</span><span class="sxs-lookup"><span data-stu-id="7b71e-116">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

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

<span data-ttu-id="7b71e-117">Můžete zkontrolovat kód, který vytváří tento výstup posouváním na konec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7b71e-117">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="7b71e-118">S kódem můžete experimentovat stažením řešení do místního počítače a spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu k vytvoření vlastního projektu Další informace a pokyny naleznete v [tématu Revize a spuštění aplikace Example .](#BKMD_SettingUpTheExample)</span><span class="sxs-lookup"><span data-stu-id="7b71e-118">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="7b71e-119">Manipulace s reentrancy</span><span class="sxs-lookup"><span data-stu-id="7b71e-119">Handling Reentrancy</span></span>

<span data-ttu-id="7b71e-120">Reentrancy můžete zpracovat různými způsoby v závislosti na tom, co chcete, aby vaše aplikace dělat.</span><span class="sxs-lookup"><span data-stu-id="7b71e-120">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="7b71e-121">Toto téma uvádí následující příklady:</span><span class="sxs-lookup"><span data-stu-id="7b71e-121">This topic presents the following examples:</span></span>

- [<span data-ttu-id="7b71e-122">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="7b71e-122">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="7b71e-123">Zakažte tlačítko **Start,** když je operace spuštěna, aby ji uživatel nemohl přerušit.</span><span class="sxs-lookup"><span data-stu-id="7b71e-123">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="7b71e-124">Zrušit a restartovat operaci</span><span class="sxs-lookup"><span data-stu-id="7b71e-124">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="7b71e-125">Zrušte všechny operace, které jsou stále spuštěny, když uživatel znovu vybere tlačítko **Start,** a potom nechte naposledy požadovanou operaci pokračovat.</span><span class="sxs-lookup"><span data-stu-id="7b71e-125">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="7b71e-126">Spuštění více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="7b71e-126">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="7b71e-127">Povolit všechny požadované operace spustit asynchronně, ale koordinovat zobrazení výstupu tak, aby výsledky z každé operace se zobrazí společně a v pořadí.</span><span class="sxs-lookup"><span data-stu-id="7b71e-127">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="7b71e-128">Zakázání tlačítka Start</span><span class="sxs-lookup"><span data-stu-id="7b71e-128">Disable the Start Button</span></span>

<span data-ttu-id="7b71e-129">Tlačítko **Start** můžete blokovat v době, kdy je spuštěna operace, zakázáním tlačítka v horní části obslužné rutiny `StartButton_Click` události.</span><span class="sxs-lookup"><span data-stu-id="7b71e-129">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="7b71e-130">Po dokončení operace pak můžete `Finally` znovu povolit tlačítko z bloku, aby uživatelé mohli aplikaci znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="7b71e-130">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="7b71e-131">Následující kód ukazuje tyto změny, které jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="7b71e-131">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="7b71e-132">Můžete přidat změny kódu na konci tohoto tématu, nebo si můžete stáhnout dokončenou aplikaci z [Async Samples: Reentrancy v .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="7b71e-132">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="7b71e-133">Název projektu je DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="7b71e-133">The project name is DisableStartButton.</span></span>

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

<span data-ttu-id="7b71e-134">V důsledku změn tlačítko nereaguje při `AccessTheWebAsync` stahování webových stránek, takže proces nelze znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="7b71e-134">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a><span data-ttu-id="7b71e-135">Zrušit a restartovat operaci</span><span class="sxs-lookup"><span data-stu-id="7b71e-135">Cancel and Restart the Operation</span></span>

<span data-ttu-id="7b71e-136">Místo zakázání tlačítka **Start** můžete ponechat tlačítko aktivní, ale pokud uživatel toto tlačítko znovu zvolí, zrušte operaci, která je již spuštěna, a nechte pokračovat v naposledy zahájené operaci.</span><span class="sxs-lookup"><span data-stu-id="7b71e-136">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="7b71e-137">Další informace o zrušení naleznete v [tématu Jemné doladění asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="7b71e-137">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="7b71e-138">Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [revizi a spuštění aplikace Příklad](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="7b71e-138">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="7b71e-139">Hotovou aplikaci si můžete také stáhnout z [aplikace Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="7b71e-139">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="7b71e-140">Název tohoto projektu je CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="7b71e-140">The name of this project is CancelAndRestart.</span></span>

1. <span data-ttu-id="7b71e-141">Deklarovat proměnnou <xref:System.Threading.CancellationTokenSource> , `cts`která je v oboru pro všechny metody.</span><span class="sxs-lookup"><span data-stu-id="7b71e-141">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="7b71e-142">V `StartButton_Click`aplikaci určete, zda operace již probíhá.</span><span class="sxs-lookup"><span data-stu-id="7b71e-142">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="7b71e-143">Pokud `cts` je `Nothing`hodnota , žádná operace je již aktivní.</span><span class="sxs-lookup"><span data-stu-id="7b71e-143">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="7b71e-144">Pokud hodnota není `Nothing`, operace, která je již spuštěna, je zrušena.</span><span class="sxs-lookup"><span data-stu-id="7b71e-144">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. <span data-ttu-id="7b71e-145">Nastavte `cts` na jinou hodnotu, která představuje aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="7b71e-145">Set `cts` to a different value that represents the current process.</span></span>

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. <span data-ttu-id="7b71e-146">Na konci `StartButton_Click`, aktuální proces je dokončen, takže `cts` nastavte `Nothing`hodnotu zpět na .</span><span class="sxs-lookup"><span data-stu-id="7b71e-146">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

<span data-ttu-id="7b71e-147">Následující kód zobrazuje všechny `StartButton_Click`změny v .</span><span class="sxs-lookup"><span data-stu-id="7b71e-147">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="7b71e-148">Přídavky jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="7b71e-148">The additions are marked with asterisks.</span></span>

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

<span data-ttu-id="7b71e-149">V `AccessTheWebAsync`, proveďte následující změny.</span><span class="sxs-lookup"><span data-stu-id="7b71e-149">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="7b71e-150">Přidejte parametr pro přijetí `StartButton_Click`tokenu zrušení z .</span><span class="sxs-lookup"><span data-stu-id="7b71e-150">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="7b71e-151">Pomocí <xref:System.Net.Http.HttpClient.GetAsync%2A> této metody stáhněte `GetAsync` weby, protože přijímá <xref:System.Threading.CancellationToken> argument.</span><span class="sxs-lookup"><span data-stu-id="7b71e-151">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="7b71e-152">Před `DisplayResults` voláním za účelem zobrazení výsledků `ct` pro každý stažený web zkontrolujte, zda nebyla aktuální operace zrušena.</span><span class="sxs-lookup"><span data-stu-id="7b71e-152">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

 <span data-ttu-id="7b71e-153">Následující kód ukazuje tyto změny, které jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="7b71e-153">The following code shows these changes, which are marked with asterisks.</span></span>

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

<span data-ttu-id="7b71e-154">Pokud zvolíte tlačítko **Start** několikrát, když je tato aplikace spuštěna, mělo by to přinést výsledky, které se podobají následujícímu výstupu:</span><span class="sxs-lookup"><span data-stu-id="7b71e-154">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output:</span></span>

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

<span data-ttu-id="7b71e-155">Chcete-li odstranit částečné seznamy, odkomentujte první řádek `StartButton_Click` kódu, abyste zrušili textové pole při každém restartování operace uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7b71e-155">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="7b71e-156">Spuštění více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="7b71e-156">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="7b71e-157">Tento třetí příklad je nejsložitější v tom, že aplikace spustí další asynchronní operaci pokaždé, když uživatel zvolí tlačítko **Start** a všechny operace spustit až do konce.</span><span class="sxs-lookup"><span data-stu-id="7b71e-157">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="7b71e-158">Všechny požadované operace stáhnout weby ze seznamu asynchronně, ale výstup z operací je prezentován akvenční.</span><span class="sxs-lookup"><span data-stu-id="7b71e-158">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="7b71e-159">To znamená, že skutečná aktivita stahování je prokládána, jak ukazuje výstup v [rozpoznávání reentrancy,](#BKMK_RecognizingReentrancy) ale seznam výsledků pro každou skupinu je uveden samostatně.</span><span class="sxs-lookup"><span data-stu-id="7b71e-159">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="7b71e-160">Operace sdílejí globální <xref:System.Threading.Tasks.Task> `pendingWork`, , který slouží jako gatekeeper pro proces zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7b71e-160">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="7b71e-161">Tento příklad můžete spustit vložením změny do kódu v [sestavení aplikace](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [stažení aplikace](#BKMK_DownloadingTheApp) stáhnout ukázku a potom spustit projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="7b71e-161">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>

<span data-ttu-id="7b71e-162">Následující výstup ukazuje výsledek, pokud uživatel zvolí tlačítko **Start** pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="7b71e-162">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="7b71e-163">Popisek písmene A označuje, že výsledek je od prvního výběru tlačítka **Start.**</span><span class="sxs-lookup"><span data-stu-id="7b71e-163">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="7b71e-164">Čísla zobrazují pořadí adres URL v seznamu cílů stahování.</span><span class="sxs-lookup"><span data-stu-id="7b71e-164">The numbers show the order of the URLs in the list of download targets.</span></span>

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

<span data-ttu-id="7b71e-165">Pokud uživatel třikrát zvolí tlačítko **Start,** aplikace vytvoří výstup, který se podobá následujícím řádkům.</span><span class="sxs-lookup"><span data-stu-id="7b71e-165">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="7b71e-166">Informační řádky, které začínají znakem libry (#), sledují průběh aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b71e-166">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

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

<span data-ttu-id="7b71e-167">Skupiny B a C začínají před dokončením skupiny A, ale výstup pro každou skupinu se zobrazí samostatně.</span><span class="sxs-lookup"><span data-stu-id="7b71e-167">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="7b71e-168">Nejprve se zobrazí veškerý výstup pro skupinu A následovaný veškerým výstupem pro skupinu B a potom veškerým výstupem pro skupinu C. Aplikace vždy zobrazuje skupiny v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webech v pořadí, v jakém se adresy URL zobrazují v seznamu adres URL.</span><span class="sxs-lookup"><span data-stu-id="7b71e-168">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="7b71e-169">Nelze však předpovědět pořadí, ve kterém ke stažení skutečně dochází.</span><span class="sxs-lookup"><span data-stu-id="7b71e-169">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="7b71e-170">Po spuštění více skupin jsou všechny úlohy stahování, které generují, aktivní.</span><span class="sxs-lookup"><span data-stu-id="7b71e-170">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="7b71e-171">Nemůžete předpokládat, že A-1 bude stažen před B-1, a nemůžete předpokládat, že A-1 bude staženpřed A-2.</span><span class="sxs-lookup"><span data-stu-id="7b71e-171">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="7b71e-172">Globální definice</span><span class="sxs-lookup"><span data-stu-id="7b71e-172">Global Definitions</span></span>

<span data-ttu-id="7b71e-173">Ukázkový kód obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.</span><span class="sxs-lookup"><span data-stu-id="7b71e-173">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

<span data-ttu-id="7b71e-174">Proměnná `Task` `pendingWork`, dohlíží na proces zobrazení a zabraňuje jakékoli skupině přerušit operaci zobrazení jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="7b71e-174">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="7b71e-175">Znaková proměnná , `group`označuje výstup z různých skupin, aby ověřila, že se výsledky zobrazí v očekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7b71e-175">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="7b71e-176">Obslužná rutina události kliknutí</span><span class="sxs-lookup"><span data-stu-id="7b71e-176">The Click Event Handler</span></span>

<span data-ttu-id="7b71e-177">Obslužná rutina události , `StartButton_Click`zintáží skupinové písmeno pokaždé, když uživatel zvolí tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="7b71e-177">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="7b71e-178">Potom obslužná rutina volá `AccessTheWebAsync` ke spuštění operace stahování.</span><span class="sxs-lookup"><span data-stu-id="7b71e-178">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

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

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="7b71e-179">Metoda AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="7b71e-179">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="7b71e-180">Tento příklad `AccessTheWebAsync` se rozdělí na dvě metody.</span><span class="sxs-lookup"><span data-stu-id="7b71e-180">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="7b71e-181">První metoda `AccessTheWebAsync`, spustí všechny úlohy stahování pro `pendingWork` skupinu a nastaví řízení procesu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7b71e-181">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="7b71e-182">Metoda používá jazyk integrovaný dotaz (dotaz <xref:System.Linq.Enumerable.ToArray%2A> LINQ) a spustit všechny úlohy stahování ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="7b71e-182">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="7b71e-183">`AccessTheWebAsync`pak `FinishOneGroupAsync` volá čekat na dokončení každého stažení a zobrazit jeho délku.</span><span class="sxs-lookup"><span data-stu-id="7b71e-183">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="7b71e-184">`FinishOneGroupAsync`vrátí úkol, který je `pendingWork` `AccessTheWebAsync`přiřazen v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="7b71e-184">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="7b71e-185">Tato hodnota zabraňuje přerušení jinou operací před dokončením úlohy.</span><span class="sxs-lookup"><span data-stu-id="7b71e-185">That value prevents interruption by another operation before the task is complete.</span></span>

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

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="7b71e-186">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="7b71e-186">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="7b71e-187">Tato metoda cyklicky prochází úlohy stahování ve skupině, čeká na každou z nich, zobrazuje délku staženého webu a přidává délku k celkovému součtu.</span><span class="sxs-lookup"><span data-stu-id="7b71e-187">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="7b71e-188">První příkaz `FinishOneGroupAsync` v `pendingWork` používá k ujistěte se, že zadání metody není v rozporu s operací, která je již v procesu zobrazení nebo který je již čeká.</span><span class="sxs-lookup"><span data-stu-id="7b71e-188">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="7b71e-189">Pokud taková operace probíhá, musí zadávacího řízení počkat, až přijde na řadu.</span><span class="sxs-lookup"><span data-stu-id="7b71e-189">If such an operation is in progress, the entering operation must wait its turn.</span></span>

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

<span data-ttu-id="7b71e-190">Tento příklad můžete spustit vložením změny do kódu v [sestavení aplikace](#BKMK_BuildingTheApp), nebo můžete postupovat podle pokynů v [stažení aplikace](#BKMK_DownloadingTheApp) ke stažení ukázky a potom spusťte projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="7b71e-190">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>

#### <a name="points-of-interest"></a><span data-ttu-id="7b71e-191">Body zájmu</span><span class="sxs-lookup"><span data-stu-id="7b71e-191">Points of Interest</span></span>

<span data-ttu-id="7b71e-192">Informační řádky, které začínají znakem libry (#) ve výstupu, objasňují, jak tento příklad funguje.</span><span class="sxs-lookup"><span data-stu-id="7b71e-192">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="7b71e-193">Výstup ukazuje následující vzory.</span><span class="sxs-lookup"><span data-stu-id="7b71e-193">The output shows the following patterns.</span></span>

- <span data-ttu-id="7b71e-194">Skupinu lze spustit, zatímco předchozí skupina zobrazuje svůj výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.</span><span class="sxs-lookup"><span data-stu-id="7b71e-194">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

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

- <span data-ttu-id="7b71e-195">Úkol `pendingWork` je `Nothing` na začátku pouze pro skupinu `FinishOneGroupAsync` A, která byla zahájena jako první.</span><span class="sxs-lookup"><span data-stu-id="7b71e-195">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="7b71e-196">Skupina A ještě nedokončila výraz čekání, `FinishOneGroupAsync`jakmile dosáhne .</span><span class="sxs-lookup"><span data-stu-id="7b71e-196">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="7b71e-197">Proto ovládací prvek nebyl `AccessTheWebAsync`vrácen do , `pendingWork` a první přiřazení do nedošlo.</span><span class="sxs-lookup"><span data-stu-id="7b71e-197">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="7b71e-198">Následující dva řádky se vždy zobrazí společně ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="7b71e-198">The following two lines always appear together in the output.</span></span> <span data-ttu-id="7b71e-199">Kód není nikdy přerušen mezi spuštěním `StartButton_Click` operace skupiny v aplikaci `pendingWork`a přiřazením úkolu pro skupinu .</span><span class="sxs-lookup"><span data-stu-id="7b71e-199">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  <span data-ttu-id="7b71e-200">Po zadání skupiny `StartButton_Click`operace nedokončí výraz čekání, dokud operace `FinishOneGroupAsync`nevstoupí .</span><span class="sxs-lookup"><span data-stu-id="7b71e-200">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="7b71e-201">Proto žádná jiná operace může získat kontrolu během tohoto segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="7b71e-201">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="7b71e-202">Kontrola a spuštění ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="7b71e-202">Reviewing and Running the Example App</span></span>

<span data-ttu-id="7b71e-203">Chcete-li lépe porozumět ukázkové aplikaci, můžete si ji stáhnout, vytvořit sami nebo zkontrolovat kód na konci tohoto tématu bez implementace aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b71e-203">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="7b71e-204">Chcete-li spustit příklad jako desktopovou aplikaci WPF (Windows Presentation Foundation), musíte mít v počítači nainstalovanou visual studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="7b71e-204">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="7b71e-205">Stažení aplikace</span><span class="sxs-lookup"><span data-stu-id="7b71e-205">Downloading the App</span></span>

1. <span data-ttu-id="7b71e-206">Stáhněte si komprimovaný soubor z [ukázky asynchronní: Reentrancy v .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="7b71e-206">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="7b71e-207">Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b71e-207">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="7b71e-208">Na řádku nabídek zvolte **Soubor**, **Otevřít**, **Projekt/Řešení**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-208">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="7b71e-209">Přejděte do složky, která obsahuje dekomprimovaný ukázkový kód, a otevřete soubor řešení (.sln).</span><span class="sxs-lookup"><span data-stu-id="7b71e-209">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="7b71e-210">V **Průzkumníku řešení**otevřete místní nabídku projektu, který chcete spustit, a pak zvolte **Nastavit jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-210">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="7b71e-211">Zvolte klávesy CTRL+F5 pro sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="7b71e-211">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a><span data-ttu-id="7b71e-212">Vytváření aplikace</span><span class="sxs-lookup"><span data-stu-id="7b71e-212">Building the App</span></span>

<span data-ttu-id="7b71e-213">Následující část obsahuje kód pro sestavení příkladu jako aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="7b71e-213">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="7b71e-214">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="7b71e-214">To build a WPF app</span></span>

1. <span data-ttu-id="7b71e-215">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b71e-215">Start Visual Studio.</span></span>

2. <span data-ttu-id="7b71e-216">Na řádku nabídek zvolte **Soubor**, **Nový**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-216">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="7b71e-217">Otevře se dialogové okno **Nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="7b71e-217">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="7b71e-218">V podokně **Nainstalované šablony** rozbalte **položku Visual Basic**a potom rozbalte **položku Windows**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-218">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="7b71e-219">V seznamu typů projektů zvolte **WPF Aplikace**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-219">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="7b71e-220">Pojmenujte `WebsiteDownloadWPF`projekt , zvolte verzi rozhraní .NET Framework verze 4.6 nebo vyšší a klepněte na tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="7b71e-220">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="7b71e-221">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-221">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="7b71e-222">V Editoru kódu Visual Studia zvolte kartu **MainWindow.xaml.**</span><span class="sxs-lookup"><span data-stu-id="7b71e-222">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="7b71e-223">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-223">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="7b71e-224">V zobrazení **XAML** MainWindow.xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="7b71e-224">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="7b71e-225">Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhovém** zobrazení MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="7b71e-225">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="7b71e-226">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **odkaz odkazy** a vyberte přidat **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-226">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="7b71e-227">Přidejte odkaz <xref:System.Net.Http>pro , pokud ještě není vybrán.</span><span class="sxs-lookup"><span data-stu-id="7b71e-227">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="7b71e-228">V **Průzkumníku řešení**otevřete místní nabídku pro soubor MainWindow.xaml.vb a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7b71e-228">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

10. <span data-ttu-id="7b71e-229">V souboru MainWindow.xaml.vb nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="7b71e-229">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

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

11. <span data-ttu-id="7b71e-230">Chcete-li spustit program, zvolte klávesy CTRL+F5 a pak několikrát zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="7b71e-230">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="7b71e-231">Proveďte změny z [funkce Zakázat tlačítko Start](#BKMK_DisableTheStartButton), Zrušit a [restartovat operaci](#BKMK_CancelAndRestart)nebo [Spusťte více operací a zařazujte výstup](#BKMK_RunMultipleOperations) do fronty, abyste zpracovat reentrancy.</span><span class="sxs-lookup"><span data-stu-id="7b71e-231">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b71e-232">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b71e-232">See also</span></span>

- [<span data-ttu-id="7b71e-233">Návod: Přístup k webu pomocí asynchronní a čeká (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b71e-233">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="7b71e-234">Asynchronní programování s asynchronní a čeká (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b71e-234">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
