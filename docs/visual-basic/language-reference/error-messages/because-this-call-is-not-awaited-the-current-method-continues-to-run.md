---
title: Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 5870a9a3a598c67badc9868af1486b52c76a9906
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523908"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="abc7e-102">Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.</span><span class="sxs-lookup"><span data-stu-id="abc7e-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>

<span data-ttu-id="abc7e-103">Protože toto volání není očekáváno, vykonání aktuální metody pokračuje před dokončením volání.</span><span class="sxs-lookup"><span data-stu-id="abc7e-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="abc7e-104">Zvažte použití operátoru await na výsledek volání.</span><span class="sxs-lookup"><span data-stu-id="abc7e-104">Consider applying the 'Await' operator to the result of the call.</span></span>

<span data-ttu-id="abc7e-105">Aktuální metoda volá asynchronní metodu, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a nepoužije operátor [await](../../../visual-basic/language-reference/operators/await-operator.md) na výsledek.</span><span class="sxs-lookup"><span data-stu-id="abc7e-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="abc7e-106">Volání asynchronní metody spustí asynchronní úlohu.</span><span class="sxs-lookup"><span data-stu-id="abc7e-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="abc7e-107">Protože však není použit žádný operátor `Await`, program pokračuje bez čekání na dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="abc7e-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="abc7e-108">Ve většině případů se toto chování neočekává.</span><span class="sxs-lookup"><span data-stu-id="abc7e-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="abc7e-109">Obvykle jiné aspekty volající metody závisí na výsledcích volání nebo, je-li metoda volaná, je očekávána před návratem z metody, která obsahuje volání.</span><span class="sxs-lookup"><span data-stu-id="abc7e-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>

<span data-ttu-id="abc7e-110">Stejně důležitý problém je to, co se stane s výjimkami, které jsou vyvolány v volané asynchronní metodě.</span><span class="sxs-lookup"><span data-stu-id="abc7e-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="abc7e-111">Výjimka, která je vyvolána v metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, je uložena v vrácené úloze.</span><span class="sxs-lookup"><span data-stu-id="abc7e-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="abc7e-112">Pokud neočekáváte úlohu nebo explicitně kontrolujete výjimky, výjimka se ztratí.</span><span class="sxs-lookup"><span data-stu-id="abc7e-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="abc7e-113">Pokud očekáváte úlohu, její výjimka se znovu vyvolá.</span><span class="sxs-lookup"><span data-stu-id="abc7e-113">If you await the task, its exception is rethrown.</span></span>

<span data-ttu-id="abc7e-114">V souladu s osvědčeným postupem byste měli vždy očekávat volání.</span><span class="sxs-lookup"><span data-stu-id="abc7e-114">As a best practice, you should always await the call.</span></span>

<span data-ttu-id="abc7e-115">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="abc7e-115">By default, this message is a warning.</span></span> <span data-ttu-id="abc7e-116">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="abc7e-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="abc7e-117">**ID chyby:** BC42358</span><span class="sxs-lookup"><span data-stu-id="abc7e-117">**Error ID:** BC42358</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="abc7e-118">Řešení tohoto upozornění</span><span class="sxs-lookup"><span data-stu-id="abc7e-118">To address this warning</span></span>

- <span data-ttu-id="abc7e-119">Upozornění byste měli potlačit jenom v případě, že si jste jistí, že nechcete čekat na dokončení asynchronního volání a že volaná metoda nevyvolá žádné výjimky.</span><span class="sxs-lookup"><span data-stu-id="abc7e-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="abc7e-120">V takovém případě můžete upozornění potlačit přiřazením výsledku úlohy volání proměnné.</span><span class="sxs-lookup"><span data-stu-id="abc7e-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>

     <span data-ttu-id="abc7e-121">Následující příklad ukazuje, jak vyvolat upozornění, jak ho potlačit a jak očekávat volání.</span><span class="sxs-lookup"><span data-stu-id="abc7e-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>

    ```vb
    Async Function CallingMethodAsync() As Task

        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."

        ' Variable delay is used to slow down the called method so that you
        ' can distinguish between awaiting and not awaiting in the program's output.
        ' You can adjust the value to produce the output that this topic shows
        ' after the code.
        Dim delay = 5000

        ' Call #1.
        ' Call an async method. Because you don't await it, its completion isn't
        ' coordinated with the current method, CallingMethodAsync.
        ' The following line causes the warning.
        CalledMethodAsync(delay)

        ' Call #2.
        ' To suppress the warning without awaiting, you can assign the
        ' returned task to a variable. The assignment doesn't change how
        ' the program runs. However, the recommended practice is always to
        ' await a call to an async method.
        ' Replace Call #1 with the following line.
        'Task delayTask = CalledMethodAsync(delay)

        ' Call #3
        ' To contrast with an awaited call, replace the unawaited call
        ' (Call #1 or Call #2) with the following awaited call. The best
        ' practice is to await the call.

        'Await CalledMethodAsync(delay)

        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync
        ' continues to run and, in this example, finishes its work and returns
        ' to its caller.
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."
    End Function

    Async Function CalledMethodAsync(howLong As Integer) As Task

        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."
        ' Slow the process down a little so you can distinguish between awaiting
        ' and not awaiting. Adjust the value for howLong if necessary.
        Await Task.Delay(howLong)
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."
    End Function
    ```

     <span data-ttu-id="abc7e-122">Pokud v příkladu zvolíte volání #1 nebo volání #2, neočekávaná asynchronní metoda (`CalledMethodAsync`) se dokončí po jeho volajícím (`CallingMethodAsync`) a volajícím (`StartButton_Click`) jsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="abc7e-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="abc7e-123">Poslední řádek v následujícím výstupu ukazuje, kdy se volaná metoda dokončí.</span><span class="sxs-lookup"><span data-stu-id="abc7e-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="abc7e-124">Vstup a výstup z obslužné rutiny události, která volá `CallingMethodAsync` v úplném příkladu, je označena ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="abc7e-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>

    ```console
    Entering the Click event handler.
      Entering calling method.
        Entering called method, starting and awaiting Task.Delay.
      Returning from calling method.
    Exiting the Click event handler.
        Task.Delay is finished--returning from called method.
    ```

## <a name="example"></a><span data-ttu-id="abc7e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="abc7e-125">Example</span></span>

<span data-ttu-id="abc7e-126">Následující aplikace Windows Presentation Foundation (WPF) obsahuje metody z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="abc7e-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="abc7e-127">Následující postup nastaví aplikaci.</span><span class="sxs-lookup"><span data-stu-id="abc7e-127">The following steps set up the application.</span></span>

1. <span data-ttu-id="abc7e-128">Vytvořte aplikaci WPF a pojmenujte ji `AsyncWarning`.</span><span class="sxs-lookup"><span data-stu-id="abc7e-128">Create a WPF application, and name it `AsyncWarning`.</span></span>

2. <span data-ttu-id="abc7e-129">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="abc7e-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="abc7e-130">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="abc7e-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

3. <span data-ttu-id="abc7e-131">Nahraďte kód v zobrazení **XAML** souboru MainWindow. XAML následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="abc7e-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="abc7e-132">Jednoduché okno obsahující tlačítko a textové pole se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="abc7e-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>

     <span data-ttu-id="abc7e-133">Další informace o Návrhář XAML najdete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="abc7e-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="abc7e-134">Informace o tom, jak vytvořit vlastní jednoduché uživatelské rozhraní, naleznete v části "Vytvoření aplikace WPF" a "Návrh jednoduchého MainWindow WPF" v tématu [Postupy: přístup k webu pomocí modifikátoru Async a operátoru await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="abc7e-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

4. <span data-ttu-id="abc7e-135">Nahraďte kód v souboru MainWindow. XAML. vb následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="abc7e-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

    ```vb
    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."
            Await CallingMethodAsync()
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."
        End Sub

        Async Function CallingMethodAsync() As Task

            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."

            ' Variable delay is used to slow down the called method so that you
            ' can distinguish between awaiting and not awaiting in the program's output.
            ' You can adjust the value to produce the output that this topic shows
            ' after the code.
            Dim delay = 5000

            ' Call #1.
            ' Call an async method. Because you don't await it, its completion isn't
            ' coordinated with the current method, CallingMethodAsync.
            ' The following line causes the warning.
            CalledMethodAsync(delay)

            ' Call #2.
            ' To suppress the warning without awaiting, you can assign the
            ' returned task to a variable. The assignment doesn't change how
            ' the program runs. However, the recommended practice is always to
            ' await a call to an async method.

            ' Replace Call #1 with the following line.
            'Task delayTask = CalledMethodAsync(delay)

            ' Call #3
            ' To contrast with an awaited call, replace the unawaited call
            ' (Call #1 or Call #2) with the following awaited call. The best
            ' practice is to await the call.

            'Await CalledMethodAsync(delay)

            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync
            ' continues to run and, in this example, finishes its work and returns
            ' to its caller.
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."
        End Function

        Async Function CalledMethodAsync(howLong As Integer) As Task

            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."
            ' Slow the process down a little so you can distinguish between awaiting
            ' and not awaiting. Adjust the value for howLong if necessary.
            Await Task.Delay(howLong)
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."
        End Function

    End Class

    ' Output

    ' Entering the Click event handler.
    '   Entering calling method.
    '     Entering called method, starting and awaiting Task.Delay.
    '   Returning from calling method.
    ' Exiting the Click event handler.
    '     Task.Delay is finished--returning from called method.

    ' Output

    ' Entering the Click event handler.
    '   Entering calling method.
    '     Entering called method, starting and awaiting Task.Delay.
    '     Task.Delay is finished--returning from called method.
    '   Returning from calling method.
    ' Exiting the Click event handler.
    ```

5. <span data-ttu-id="abc7e-136">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="abc7e-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="abc7e-137">Očekávaný výstup se zobrazí na konci kódu.</span><span class="sxs-lookup"><span data-stu-id="abc7e-137">The expected output appears at the end of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="abc7e-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abc7e-138">See also</span></span>

- [<span data-ttu-id="abc7e-139">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="abc7e-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="abc7e-140">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="abc7e-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
