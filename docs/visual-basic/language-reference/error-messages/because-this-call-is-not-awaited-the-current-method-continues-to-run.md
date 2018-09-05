---
title: Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: a07955363ea5ca1ca8785c241b0de58149f329ba
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745577"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a>Protože toto volání není očekáváno, spouštění aktuální metody pokračuje před dokončením volání.
Protože toto volání neočekává, vykonávání aktuální metody pokračuje před dokončením volání. Jestli nebude lepší uplatňovat operátor 'Await' na výsledek volání.  
  
 Aktuální metoda volání asynchronní metody vracející <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a nevztahuje se [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor k výsledku. Volání asynchronní metody spustí asynchronní úlohu. Ale protože žádné `Await` je použit operátor, program bude pokračovat bez čekání na dokončení úkolu. Ve většině případů se neočekává chování. Obvykle další aspekty volání metody závisí na výsledky volání nebo minimálně volané metody se očekává před vrácení z metody, která obsahuje volání.  
  
 Stejně důležité je, co se stane s výjimkami, které jsou vyvolány v volané asynchronní metody. Výjimka, která je vyvolána metoda, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> je uložen v rámci vrácené úlohy. Pokud nevidíte await úkolu nebo explicitně zjišťovat výjimky, dojde ke ztrátě výjimku. Pokud očekáváte úkol, je jeho výjimka znovu vyvolána.  
  
 Jako osvědčený postup můžete vždy měli očekávat volání.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42358  
  
### <a name="to-address-this-warning"></a>Chcete-li vyřešit tato upozornění  
  
-   Měli byste zvážit potlačení upozornění pouze v případě, že jste si jisti, že nechcete čekat na dokončení asynchronního volání a že volané metody nevyvolá žádné výjimky. V takovém případě lze potlačit upozornění přiřazením úkolu výsledek volání do proměnné.  
  
     Následující příklad ukazuje, jak vyvolat upozornění, jak ho potlačit a jak očekávat volání.  
  
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
  
     V příkladu, pokud se rozhodnete volání č. 1 nebo volání č. 2, unawaited asynchronní metody (`CalledMethodAsync`) skončí za oba volající funkci (`CallingMethodAsync`) a volající volajícího (`StartButton_Click`) jsou dokončeny. Poslední řádek v následující výstup ukazuje dokončení volané metody. Vstupu a výstupu z obslužné rutiny události, která volá `CallingMethodAsync` v úplném příkladu jsou označeny jako výstup.  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a>Příklad  
 Následující aplikace Windows Presentation Foundation (WPF) obsahuje metodu z předchozího příkladu. Následující kroky nastavení aplikace.  
  
1.  Vytvoření aplikace WPF a pojmenujte ho `AsyncWarning`.  
  
2.  V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.  
  
     Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.  
  
3.  Nahraďte kód v **XAML** zobrazení souboru mainwindow.XAML následujícím kódem.  
  
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
  
     Jednoduché okno obsahující tlačítko a textové pole se zobrazí v **návrhu** zobrazení souboru MainWindow.xaml.  
  
     Další informace o návrháři XAML, naleznete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio). Informace o tom, jak vytvořit jednoduché uživatelské rozhraní, najdete v článku "postup vytvoření aplikace WPF" a "pro návrh jednoduchého hlavního okna MainWindow WPF" části [návod: přístup k webu pomocí Async a Await](https://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).  
  
4.  Nahraďte kód v souboru MainWindow.xaml.vb následujícím kódem.  
  
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
  
5.  Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
     Kódu na konci se zobrazuje očekávaný výstup.  
  
## <a name="see-also"></a>Viz také  
 [Operátor Await](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../visual-basic/programming-guide/concepts/async/index.md)
