---
title: Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 754fc6750e63f6d9f39da94041fc452829bca46d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591431"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="47fe6-102">Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.</span><span class="sxs-lookup"><span data-stu-id="47fe6-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>
<span data-ttu-id="47fe6-103">Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.</span><span class="sxs-lookup"><span data-stu-id="47fe6-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="47fe6-104">Zvažte použití operátoru 'Await' na výsledek volání.</span><span class="sxs-lookup"><span data-stu-id="47fe6-104">Consider applying the 'Await' operator to the result of the call.</span></span>  
  
 <span data-ttu-id="47fe6-105">Aktuální metoda volá asynchronní metody, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a se nevztahuje [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor na výsledek.</span><span class="sxs-lookup"><span data-stu-id="47fe6-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="47fe6-106">Volání asynchronní metody spustí asynchronní úlohu.</span><span class="sxs-lookup"><span data-stu-id="47fe6-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="47fe6-107">Ale protože žádné `Await` operátor se použije, program bude pokračovat bez čekání na dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="47fe6-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="47fe6-108">Ve většině případů není očekáván daná chování.</span><span class="sxs-lookup"><span data-stu-id="47fe6-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="47fe6-109">Obvykle další aspekty volání metody závisí na výsledcích volání nebo minimálně zavolat metoda očekává se dokončit před vrácením z metody, která obsahuje volání.</span><span class="sxs-lookup"><span data-stu-id="47fe6-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>  
  
 <span data-ttu-id="47fe6-110">Co se stane s výjimkami, které jsou vyvolány v volané asynchronní metody je stejně důležité problém.</span><span class="sxs-lookup"><span data-stu-id="47fe6-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="47fe6-111">Výjimka, která se vyvolá metoda, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> je uložen v vrácený úloh.</span><span class="sxs-lookup"><span data-stu-id="47fe6-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="47fe6-112">Pokud nemáte await úlohu nebo explicitně zkontrolovala pro výjimky, dojde ke ztrátě výjimku.</span><span class="sxs-lookup"><span data-stu-id="47fe6-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="47fe6-113">Pokud jste await úkol, je znovu vyvolány svou výjimku.</span><span class="sxs-lookup"><span data-stu-id="47fe6-113">If you await the task, its exception is rethrown.</span></span>  
  
 <span data-ttu-id="47fe6-114">Jako osvědčený postup by měla vždycky await volání.</span><span class="sxs-lookup"><span data-stu-id="47fe6-114">As a best practice, you should always await the call.</span></span>  
  
 <span data-ttu-id="47fe6-115">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="47fe6-115">By default, this message is a warning.</span></span> <span data-ttu-id="47fe6-116">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="47fe6-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="47fe6-117">**ID chyby:** BC42358</span><span class="sxs-lookup"><span data-stu-id="47fe6-117">**Error ID:** BC42358</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="47fe6-118">Pro vyřešení tohoto upozornění</span><span class="sxs-lookup"><span data-stu-id="47fe6-118">To address this warning</span></span>  
  
-   <span data-ttu-id="47fe6-119">Měli byste zvážit potlačení upozornění pouze v případě, že jste si jisti, že nechcete čekat na dokončení asynchronního volání a že zavolat metodu nevydá jakékoli výjimky.</span><span class="sxs-lookup"><span data-stu-id="47fe6-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="47fe6-120">V takovém případě můžete potlačit upozornění přiřazením úkolů výsledek volání proměnné.</span><span class="sxs-lookup"><span data-stu-id="47fe6-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>  
  
     <span data-ttu-id="47fe6-121">Následující příklad ukazuje, jak způsobit upozornění, jak ho potlačit a postup await volání.</span><span class="sxs-lookup"><span data-stu-id="47fe6-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>  
  
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
  
     <span data-ttu-id="47fe6-122">V příkladu, pokud se rozhodnete č. 1 volání nebo volání č. 2, unawaited asynchronní metody (`CalledMethodAsync`) dokončení po obou jeho volající (`CallingMethodAsync`) a volající volajícího (`StartButton_Click`) jsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="47fe6-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="47fe6-123">Po dokončení zavolat metodu ukazuje na posledním řádku následující výstup.</span><span class="sxs-lookup"><span data-stu-id="47fe6-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="47fe6-124">Vstupu a výstupu z obslužné rutiny události, která volá `CallingMethodAsync` v Úplný příklad označené ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="47fe6-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a><span data-ttu-id="47fe6-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="47fe6-125">Example</span></span>  
 <span data-ttu-id="47fe6-126">Následující aplikace Windows Presentation Foundation (WPF) obsahuje metody, které z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="47fe6-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="47fe6-127">Následující postup nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="47fe6-127">The following steps set up the application.</span></span>  
  
1.  <span data-ttu-id="47fe6-128">Vytvoření aplikace WPF a pojmenujte ji `AsyncWarning`.</span><span class="sxs-lookup"><span data-stu-id="47fe6-128">Create a WPF application, and name it `AsyncWarning`.</span></span>  
  
2.  <span data-ttu-id="47fe6-129">V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.</span><span class="sxs-lookup"><span data-stu-id="47fe6-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="47fe6-130">Pokud na kartě není zobrazena, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="47fe6-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
3.  <span data-ttu-id="47fe6-131">Nahraďte kód v **XAML** zobrazení MainWindow.xaml následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="47fe6-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>  
  
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
  
     <span data-ttu-id="47fe6-132">Jednoduché okno, které obsahuje tlačítka a v textovém poli se zobrazí v **návrhu** zobrazení MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="47fe6-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>  
  
     <span data-ttu-id="47fe6-133">Další informace o návrháři XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="47fe6-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="47fe6-134">Informace o tom, jak vytvořit jednoduché uživatelské rozhraní najdete v tématu "postup vytvoření aplikace WPF" a "návrhu jednoduché MainWindow WPF" části [návod: přístup k webu pomocí modifikátoru Async a Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span><span class="sxs-lookup"><span data-stu-id="47fe6-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span></span>  
  
4.  <span data-ttu-id="47fe6-135">Nahraďte kód v MainWindow.xaml.vb následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="47fe6-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
5.  <span data-ttu-id="47fe6-136">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="47fe6-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="47fe6-137">Očekávaný výstup se zobrazí na konci kód.</span><span class="sxs-lookup"><span data-stu-id="47fe6-137">The expected output appears at the end of the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47fe6-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="47fe6-138">See Also</span></span>  
 [<span data-ttu-id="47fe6-139">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="47fe6-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="47fe6-140">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="47fe6-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
