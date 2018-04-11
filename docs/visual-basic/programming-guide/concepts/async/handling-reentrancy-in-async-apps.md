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
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="946e3-102">Podpora vícenásobného přístupu v aplikacích s modifikátorem Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946e3-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="946e3-103">Když zahrnete asynchronní kód ve vaší aplikaci, musí vzít v úvahu a pravděpodobně zabránit vícenásobný přístup, který odkazuje na nutnosti opětovného zadávání asynchronní operace předtím, než byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="946e3-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="946e3-104">Pokud nemáte identifikovat a zpracování možnosti pro vícenásobný přístup, může to způsobit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="946e3-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="946e3-105">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="946e3-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="946e3-106">Rozpozná vícenásobný přístup</span><span class="sxs-lookup"><span data-stu-id="946e3-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="946e3-107">Podpora vícenásobného přístupu</span><span class="sxs-lookup"><span data-stu-id="946e3-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="946e3-108">Zakázat tlačítko Start</span><span class="sxs-lookup"><span data-stu-id="946e3-108">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="946e3-109">Zrušit a operaci restartujte.</span><span class="sxs-lookup"><span data-stu-id="946e3-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="946e3-110">Spustit více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="946e3-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="946e3-111">Kontrola a spuštění aplikace příklad</span><span class="sxs-lookup"><span data-stu-id="946e3-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="946e3-112">Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="946e3-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="946e3-113">Rozpozná vícenásobný přístup</span><span class="sxs-lookup"><span data-stu-id="946e3-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="946e3-114">V příkladu v tomto tématu, vyberte uživatele **spustit** tlačítko zahájíte asynchronní aplikaci, která stáhne řadu weby a vypočítá celkový počet bajtů, které jsou staženy.</span><span class="sxs-lookup"><span data-stu-id="946e3-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="946e3-115">Synchronní verzi příkladu by odpovídat stejný způsobem, bez ohledu na to o tom, kolikrát uživatel vybere tlačítko proto, že po prvním vlákna uživatelského rozhraní ignoruje tyto události, dokud nebude dokončeno aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="946e3-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="946e3-116">V aplikaci asynchronní však vlákna uživatelského rozhraní nadále reagovat a předtím, než byla dokončena, může je znovu zadat asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="946e3-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="946e3-117">Následující příklad ukazuje očekávaný výstup, pokud uživatel vybere **spustit** tlačítko pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="946e3-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="946e3-118">Zobrazí seznam stažené webů s velikost v bajtech každé lokality.</span><span class="sxs-lookup"><span data-stu-id="946e3-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="946e3-119">Celkový počet bajtů, zobrazí se na konci.</span><span class="sxs-lookup"><span data-stu-id="946e3-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="946e3-120">Ale pokud se uživatel rozhodne tlačítko více než jednou, obslužné rutiny události je volána opakovaně a proces stahování je znovu zadat pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="946e3-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="946e3-121">V důsledku toho několik asynchronních operací běží ve stejnou dobu, výstup interleaves výsledky a celkový počet bajtů je matoucí.</span><span class="sxs-lookup"><span data-stu-id="946e3-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
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
  
 <span data-ttu-id="946e3-122">Můžete zkontrolovat kód, který vytváří tento výstup podle posouvání na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="946e3-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="946e3-123">Můžete experimentovat s kódem stahování řešení do místního počítače a potom spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu vytvořit svůj vlastní projekt pro další informace a pokyny najdete v části [ Kontrola a spuštění aplikace příklad](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="946e3-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="946e3-124">Podpora vícenásobného přístupu</span><span class="sxs-lookup"><span data-stu-id="946e3-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="946e3-125">Vícenásobný přístup v mnoha různými způsoby v závislosti na tom, co chcete udělat v aplikaci může zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="946e3-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="946e3-126">Toto téma představuje následující příklady:</span><span class="sxs-lookup"><span data-stu-id="946e3-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="946e3-127">Zakázat tlačítko Start</span><span class="sxs-lookup"><span data-stu-id="946e3-127">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="946e3-128">Zakažte **spustit** tlačítko při operaci tak, aby uživatel ji ukončit.</span><span class="sxs-lookup"><span data-stu-id="946e3-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="946e3-129">Zrušit a operaci restartujte.</span><span class="sxs-lookup"><span data-stu-id="946e3-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="946e3-130">Zrušte všechny operace, která je stále spuštěn, když uživatel vybere **spustit** tlačítko znovu a poté pokračujte umožňují nedávno požadovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="946e3-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="946e3-131">Spustit více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="946e3-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="946e3-132">Povolit všechny požadované operace běží asynchronně, ale koordinaci zobrazení výstupu tak, aby výsledky z každé operace se zobrazí společně a v pořadí.</span><span class="sxs-lookup"><span data-stu-id="946e3-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="946e3-133">Zakázat tlačítko Start</span><span class="sxs-lookup"><span data-stu-id="946e3-133">Disable the Start Button</span></span>  
 <span data-ttu-id="946e3-134">Můžete blokovat **spustit** tlačítko spuštěného operace zakázáním tlačítka v horní části `StartButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="946e3-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="946e3-135">Pak opětovného povolení tlačítko uvnitř `Finally` blokovat po dokončení operace tak, aby uživatelé znovu spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="946e3-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="946e3-136">Následující kód ukazuje tyto změny, které jsou označeny pomocí hvězdiček.</span><span class="sxs-lookup"><span data-stu-id="946e3-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="946e3-137">Změny můžete přidat do kód na konci tohoto tématu nebo dokončení aplikaci si můžete stáhnout [ukázky asynchronní: vícenásobný přístup v aplikacích .NET plochy](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="946e3-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="946e3-138">Název projektu je DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="946e3-138">The project name is DisableStartButton.</span></span>  
  
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
  
 <span data-ttu-id="946e3-139">V důsledku změny, tlačítko nereaguje při `AccessTheWebAsync` stahuje webů, takže proces nelze znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="946e3-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="946e3-140">Zrušit a operaci restartujte.</span><span class="sxs-lookup"><span data-stu-id="946e3-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="946e3-141">Místo zakázání **spustit** tlačítko můžete zachovat tlačítko aktivní, ale, pokud uživatel vybere akci, že tlačítko Zrušit operaci, která je již spuštěna a pokračovat v operaci nedávno spustila.</span><span class="sxs-lookup"><span data-stu-id="946e3-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="946e3-142">Další informace o zrušení najdete v tématu [Fine-Tuning vaše asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="946e3-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="946e3-143">Nastavit tento scénář, proveďte následující změny k základní kód, který je součástí [kontrolu a spuštění aplikace příklad](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="946e3-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="946e3-144">Také můžete stáhnout dokončení aplikace z [ukázky asynchronní: vícenásobný přístup v aplikacích .NET plochy](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="946e3-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="946e3-145">Název tohoto projektu je CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="946e3-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="946e3-146">Deklarace <xref:System.Threading.CancellationTokenSource> proměnnou, `cts`, který je v oboru pro všechny metody.</span><span class="sxs-lookup"><span data-stu-id="946e3-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="946e3-147">V `StartButton_Click`, určete, zda již probíhá operace.</span><span class="sxs-lookup"><span data-stu-id="946e3-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="946e3-148">Pokud hodnota `cts` je `Nothing`, je již aktivní žádná operace.</span><span class="sxs-lookup"><span data-stu-id="946e3-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="946e3-149">Pokud není hodnota `Nothing`, je zrušená operaci, která je již spuštěna.</span><span class="sxs-lookup"><span data-stu-id="946e3-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="946e3-150">Nastavit `cts` na jinou hodnotu, který představuje aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="946e3-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="946e3-151">Na konci `StartButton_Click`aktuální proces nebude hotový, takže nastavit hodnotu `cts` zpět na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="946e3-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="946e3-152">Následující kód ukazuje všechny změny v `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="946e3-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="946e3-153">Budou přidány jsou označené hvězdičky.</span><span class="sxs-lookup"><span data-stu-id="946e3-153">The additions are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="946e3-154">V `AccessTheWebAsync`, proveďte následující změny.</span><span class="sxs-lookup"><span data-stu-id="946e3-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="946e3-155">Přidání parametru tak, aby přijímal token zrušení z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="946e3-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="946e3-156">Použití <xref:System.Net.Http.HttpClient.GetAsync%2A> metoda stažení weby, protože `GetAsync` přijme <xref:System.Threading.CancellationToken> argument.</span><span class="sxs-lookup"><span data-stu-id="946e3-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="946e3-157">Před voláním `DisplayResults` zobrazíte výsledky pro každý web stažené zkontrolujte `ct` k ověření, že nedošlo ke zrušení aktuální operace.</span><span class="sxs-lookup"><span data-stu-id="946e3-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="946e3-158">Následující kód ukazuje tyto změny, které jsou označeny pomocí hvězdiček.</span><span class="sxs-lookup"><span data-stu-id="946e3-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="946e3-159">Pokud se rozhodnete **spustit** tlačítko několikrát při spuštěné aplikaci ho by měl vytvořit výsledky, které se podobají následující výstup.</span><span class="sxs-lookup"><span data-stu-id="946e3-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="946e3-160">K vyloučení částečné seznamy, zrušte komentář u první řádek kódu `StartButton_Click` zrušte textového pole pokaždé, když uživatel znovu spustí operaci.</span><span class="sxs-lookup"><span data-stu-id="946e3-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="946e3-161">Spustit více operací a fronty výstupu</span><span class="sxs-lookup"><span data-stu-id="946e3-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="946e3-162">Tento příklad třetí je nejvíce složitý, v tom, že jiná asynchronní operace pokaždé, když uživatel vybere spuštění aplikace **spustit** tlačítko a všechny operace spustit na dokončení.</span><span class="sxs-lookup"><span data-stu-id="946e3-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="946e3-163">Všechny požadované operace stáhnout weby ze seznamu asynchronně, ale postupně zobrazí výstup z operace.</span><span class="sxs-lookup"><span data-stu-id="946e3-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="946e3-164">To znamená, je prokládaný skutečné stahování aktivity, jako výstup v [rozpozná vícenásobný přístup](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ukazuje, ale seznam výsledků pro každou skupinu se zobrazí samostatně.</span><span class="sxs-lookup"><span data-stu-id="946e3-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="946e3-165">Operace sdílet globální konfiguraci <xref:System.Threading.Tasks.Task>, `pendingWork`, který slouží jako těchto pravidel pro proces zobrazení.</span><span class="sxs-lookup"><span data-stu-id="946e3-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="946e3-166">Spuštěním tohoto příkladu vložením změny do kódu v [vytváření aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), nebo můžete podle pokynů v [stahování aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ukázku stáhnout a spusťte projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="946e3-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="946e3-167">Následující výstup zobrazuje výsledek, pokud uživatel vybere **spustit** tlačítko pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="946e3-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="946e3-168">Popisek písmeno, A, označuje, že výsledkem je od prvního **spustit** je zvolen tlačítko.</span><span class="sxs-lookup"><span data-stu-id="946e3-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="946e3-169">Čísla zobrazit pořadí adresy URL v seznamu cílů stahování.</span><span class="sxs-lookup"><span data-stu-id="946e3-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="946e3-170">Pokud se uživatel rozhodne **spustit** tlačítko třikrát, aplikace vytváří výstup, která se podobá následující řádky.</span><span class="sxs-lookup"><span data-stu-id="946e3-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="946e3-171">Přihlásit informace řádky, které začínají křížek (#) trasování průběh aplikace.</span><span class="sxs-lookup"><span data-stu-id="946e3-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="946e3-172">Skupiny B a C spustit před skupiny A byl dokončen, ale zobrazí výstup pro každou skupinu samostatně.</span><span class="sxs-lookup"><span data-stu-id="946e3-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="946e3-173">Veškerý výstup pro skupiny A jako první se objeví, za nímž následuje veškerý výstup pro skupinu B a pak všechny výstup pro skupinu C. Aplikace vždy zobrazí skupiny, v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webů v pořadí, ve kterém příslušné adresy URL se zobrazí v seznamu adres URL.</span><span class="sxs-lookup"><span data-stu-id="946e3-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="946e3-174">Nelze však předvídání pořadí, ve které se stahování ve skutečnosti dojít.</span><span class="sxs-lookup"><span data-stu-id="946e3-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="946e3-175">Po spuštění více skupin stažení úlohy, které generují jsou všechny adaptéry aktivní.</span><span class="sxs-lookup"><span data-stu-id="946e3-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="946e3-176">Nelze předpokládat, že A-1 bude stažen před b-1 objekty a nelze předpokládat, že A-1 bude stažen před A-2.</span><span class="sxs-lookup"><span data-stu-id="946e3-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="946e3-177">Globální definice</span><span class="sxs-lookup"><span data-stu-id="946e3-177">Global Definitions</span></span>  
 <span data-ttu-id="946e3-178">Ukázkový kód obsahuje následující dvě globální deklarace, které jsou viditelné z všechny metody.</span><span class="sxs-lookup"><span data-stu-id="946e3-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="946e3-179">`Task` Proměnnou, `pendingWork`, dohlíží proces zobrazení a zabrání libovolnou skupinu přerušení operace zobrazení jinou skupinu.</span><span class="sxs-lookup"><span data-stu-id="946e3-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="946e3-180">Proměnnou znak `group`, popisků výstup z různých skupin k ověření, že výsledky se zobrazí v očekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="946e3-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="946e3-181">Obslužná rutina události kliknutí</span><span class="sxs-lookup"><span data-stu-id="946e3-181">The Click Event Handler</span></span>  
 <span data-ttu-id="946e3-182">Obslužné rutiny události `StartButton_Click`, zvýší písmeno skupiny pokaždé, když uživatel vybere **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="946e3-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="946e3-183">Potom volání obslužné rutiny `AccessTheWebAsync` spustit stahování operaci.</span><span class="sxs-lookup"><span data-stu-id="946e3-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
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
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="946e3-184">Metoda AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="946e3-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="946e3-185">Tento příklad rozdělí `AccessTheWebAsync` do dvou metod.</span><span class="sxs-lookup"><span data-stu-id="946e3-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="946e3-186">První metoda `AccessTheWebAsync`, spustí všechny úlohy stahování pro skupinu a nastavuje `pendingWork` řídit proces zobrazení.</span><span class="sxs-lookup"><span data-stu-id="946e3-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="946e3-187">Metoda používá integrované dotaz jazyka (dotaz LINQ) a <xref:System.Linq.Enumerable.ToArray%2A> spustit všechny úlohy stahování ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="946e3-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="946e3-188">`AccessTheWebAsync` pak zavolá `FinishOneGroupAsync` await dokončení každého stažení a zobrazit jeho délka.</span><span class="sxs-lookup"><span data-stu-id="946e3-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="946e3-189">`FinishOneGroupAsync` Vrátí úlohu, která je přiřazena k `pendingWork` v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="946e3-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="946e3-190">Že hodnota zabraňuje přerušení jinou operací před dokončením úlohy.</span><span class="sxs-lookup"><span data-stu-id="946e3-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
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
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="946e3-191">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="946e3-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="946e3-192">Tato metoda procházení stažení úlohy ve skupině, čeká na každé z nich, zobrazí délka stažené webu a přidá do celkové délka.</span><span class="sxs-lookup"><span data-stu-id="946e3-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="946e3-193">První příkaz v `FinishOneGroupAsync` používá `pendingWork` a ujistěte se, že zadáte metoda není v konfliktu se operace, která je již v zobrazení procesu nebo který je už čeká.</span><span class="sxs-lookup"><span data-stu-id="946e3-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="946e3-194">Pokud probíhá takové operace, vstup operace musí počkat jeho vypněte.</span><span class="sxs-lookup"><span data-stu-id="946e3-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
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
  
 <span data-ttu-id="946e3-195">Spuštěním tohoto příkladu vložením změny do kódu v [vytváření aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), nebo můžete podle pokynů v [stahování aplikace](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) stáhnout vzorek, a pak spusťte projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="946e3-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="946e3-196">Body zájmu</span><span class="sxs-lookup"><span data-stu-id="946e3-196">Points of Interest</span></span>  
 <span data-ttu-id="946e3-197">Informace řádky, které začínají křížek (#), ve výstupu vysvětlení, jak tento příklad funguje.</span><span class="sxs-lookup"><span data-stu-id="946e3-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="946e3-198">Výstup zobrazuje následující vzory.</span><span class="sxs-lookup"><span data-stu-id="946e3-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="946e3-199">Skupinu lze spustit skupinu předchozí zobrazit její výstup, ale proces se nepřerušil zobrazení předchozí skupině výstup.</span><span class="sxs-lookup"><span data-stu-id="946e3-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="946e3-200">`pendingWork` Úloha je `Nothing` na začátku `FinishOneGroupAsync` pouze pro skupiny A, což zahájení první.</span><span class="sxs-lookup"><span data-stu-id="946e3-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="946e3-201">Skupiny A zatím není dokončený výraz await, když se dosáhne `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="946e3-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="946e3-202">Proto se řízení nevrátí k `AccessTheWebAsync`a první přiřazení `pendingWork` nedošlo k.</span><span class="sxs-lookup"><span data-stu-id="946e3-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="946e3-203">Následující dva řádky vždy objeví spolu ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="946e3-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="946e3-204">Kód je nemohlo dojít k přerušení mezi skupině operaci počínaje `StartButton_Click` a přiřazení úloh pro skupinu do `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="946e3-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="946e3-205">Po zadání skupiny `StartButton_Click`, operace nedokončí výraz await, dokud zadá operaci `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="946e3-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="946e3-206">Žádné jiné operace. proto může získat kontrolu během tohoto segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="946e3-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="946e3-207">Kontrola a spuštění aplikace příklad</span><span class="sxs-lookup"><span data-stu-id="946e3-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="946e3-208">Abyste lépe pochopili, například aplikace, můžete ji stáhnout, vytvořit sami nebo zkontrolujte kód na konci tohoto tématu bez implementace aplikace.</span><span class="sxs-lookup"><span data-stu-id="946e3-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="946e3-209">Pokud chcete spustit v příkladu jako aplikace na ploše Windows Presentation Foundation (WPF), musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="946e3-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="946e3-210">Stažení aplikace</span><span class="sxs-lookup"><span data-stu-id="946e3-210">Downloading the App</span></span>  
  
1.  <span data-ttu-id="946e3-211">Stáhněte si komprimovaný soubor z [ukázky asynchronní: vícenásobný přístup v aplikacích .NET plochy](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="946e3-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="946e3-212">Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="946e3-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="946e3-213">Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="946e3-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="946e3-214">Přejděte do složky, která obsahuje dekomprimovaných ukázkový kód a pak otevřete soubor řešení (.sln).</span><span class="sxs-lookup"><span data-stu-id="946e3-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="946e3-215">V **Průzkumníku řešení**, otevřete místní nabídku pro projekt, který chcete spustit a potom vyberte **nastavit jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="946e3-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="946e3-216">Zvolte klávesy CTRL + F5 sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="946e3-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="946e3-217">Vytváření aplikace</span><span class="sxs-lookup"><span data-stu-id="946e3-217">Building the App</span></span>  
 <span data-ttu-id="946e3-218">Následující část obsahuje kód, který sestavení v příkladu jako aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="946e3-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="946e3-219">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="946e3-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="946e3-220">Start Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="946e3-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="946e3-221">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="946e3-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="946e3-222">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="946e3-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="946e3-223">V **nainstalovaných šablonách** podokně rozbalte **jazyka Visual Basic**a potom rozbalte **Windows**.</span><span class="sxs-lookup"><span data-stu-id="946e3-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="946e3-224">V seznamu typy projektů, vyberte **aplikaci WPF**.</span><span class="sxs-lookup"><span data-stu-id="946e3-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="946e3-225">Název projektu `WebsiteDownloadWPF`a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="946e3-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="946e3-226">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="946e3-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="946e3-227">V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.</span><span class="sxs-lookup"><span data-stu-id="946e3-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="946e3-228">Pokud na kartě není zobrazena, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="946e3-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="946e3-229">V **XAML** zobrazení MainWindow.xaml, nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="946e3-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="946e3-230">Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhu** zobrazení MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="946e3-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="946e3-231">Přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="946e3-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="946e3-232">V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.vb a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="946e3-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="946e3-233">V MainWindow.xaml.vb nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="946e3-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
  
11. <span data-ttu-id="946e3-234">Zvolte CTRL + F5 klíče pro spuštění programu a potom vyberte **spustit** tlačítko několikrát.</span><span class="sxs-lookup"><span data-stu-id="946e3-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="946e3-235">Proveďte změny z [zakázat tlačítko Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [zrušit a restartujte operaci](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), nebo [spustit více operací a fronty výstup](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pro zpracování vícenásobný přístup.</span><span class="sxs-lookup"><span data-stu-id="946e3-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946e3-236">Viz také</span><span class="sxs-lookup"><span data-stu-id="946e3-236">See Also</span></span>  
 [<span data-ttu-id="946e3-237">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946e3-237">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="946e3-238">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946e3-238">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
