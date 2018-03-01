---
title: "Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0d0a5e7c50bacc657a3f54a7f08036ede59cbfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a>Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.
Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání. Zvažte použití operátoru 'Await' na výsledek volání.  
  
 Aktuální metoda volá asynchronní metody, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a se nevztahuje [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor na výsledek. Volání asynchronní metody spustí asynchronní úlohu. Ale protože žádné `Await` operátor se použije, program bude pokračovat bez čekání na dokončení úlohy. Ve většině případů není očekáván daná chování. Obvykle další aspekty volání metody závisí na výsledcích volání nebo minimálně zavolat metoda očekává se dokončit před vrácením z metody, která obsahuje volání.  
  
 Co se stane s výjimkami, které jsou vyvolány v volané asynchronní metody je stejně důležité problém. Výjimka, která se vyvolá metoda, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> je uložen v vrácený úloh. Pokud nemáte await úlohu nebo explicitně zkontrolovala pro výjimky, dojde ke ztrátě výjimku. Pokud jste await úkol, je znovu vyvolány svou výjimku.  
  
 Jako osvědčený postup by měla vždycky await volání.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42358  
  
### <a name="to-address-this-warning"></a>Pro vyřešení tohoto upozornění  
  
-   Měli byste zvážit potlačení upozornění pouze v případě, že jste si jisti, že nechcete čekat na dokončení asynchronního volání a že zavolat metodu nevydá jakékoli výjimky. V takovém případě můžete potlačit upozornění přiřazením úkolů výsledek volání proměnné.  
  
     Následující příklad ukazuje, jak způsobit upozornění, jak ho potlačit a postup await volání.  
  
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
  
     V příkladu, pokud se rozhodnete č. 1 volání nebo volání č. 2, unawaited asynchronní metody (`CalledMethodAsync`) dokončení po obou jeho volající (`CallingMethodAsync`) a volající volajícího (`StartButton_Click`) jsou dokončeny. Po dokončení zavolat metodu ukazuje na posledním řádku následující výstup. Vstupu a výstupu z obslužné rutiny události, která volá `CallingMethodAsync` v Úplný příklad označené ve výstupu.  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a>Příklad  
 Následující aplikace Windows Presentation Foundation (WPF) obsahuje metody, které z předchozího příkladu. Následující postup nastavení aplikace.  
  
1.  Vytvoření aplikace WPF a pojmenujte ji `AsyncWarning`.  
  
2.  V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.  
  
     Pokud na kartě není zobrazena, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.  
  
3.  Nahraďte kód v **XAML** zobrazení MainWindow.xaml následujícím kódem.  
  
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
  
     Jednoduché okno, které obsahuje tlačítka a v textovém poli se zobrazí v **návrhu** zobrazení MainWindow.xaml.  
  
     Další informace o návrháři XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio). Informace o tom, jak vytvořit jednoduché uživatelské rozhraní najdete v tématu "postup vytvoření aplikace WPF" a "návrhu jednoduché MainWindow WPF" části [návod: přístup k webu pomocí modifikátoru Async a Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).  
  
4.  Nahraďte kód v MainWindow.xaml.vb následujícím kódem.  
  
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
  
5.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
     Očekávaný výstup se zobrazí na konci kód.  
  
## <a name="see-also"></a>Viz také  
 [Await – operátor](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../visual-basic/programming-guide/concepts/async/index.md)
