---
title: Asynchronní návratové typy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 87ddab62543fae5442a15fc5f200ef914ab8d859
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352578"
---
# <a name="async-return-types-visual-basic"></a>Asynchronní návratové typy (Visual Basic)
Asynchronní metody mají tři možné návratové typy: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>a void. V jazyce Visual Basic je návratový typ void napsán jako [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postup. Další informace o metodách async naleznete v tématu [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Každý návratový typ je zkontrolován v jedné z následujících částí a najdete úplný příklad, který používá všechny tři typy na konci tohoto tématu.  
  
> [!NOTE]
>  Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
## <a name="BKMK_TaskTReturnType"></a> Návratový typ Task(T)  
 <xref:System.Threading.Tasks.Task%601> Typ vrácení se používá pro asynchronní metodu, která obsahuje [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkazem, ve kterém je operand typu `TResult`.  
  
 V následujícím příkladu `TaskOfT_MethodAsync` asynchronní metoda obsahuje příkaz return, který vrátí celé číslo. Proto deklarace metody musíte zadat návratový typ `Task(Of Integer)`.  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 Když `TaskOfT_MethodAsync` je volána z v rámci výrazu await výraz await získá celočíselnou hodnota (hodnotu `leisureHours`), která je uložena v úkolu, který je vrácený `TaskOfT_MethodAsync`. Další informace o výrazech await naleznete [operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 Následující kód volá a čeká metodu `TaskOfT_MethodAsync`. Výsledek je přiřazen k `result1` proměnné.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Můžete lépe pochopit, jak to probíhá oddělením volání `TaskOfT_MethodAsync` od aplikace `Await`, jak ukazuje následující kód. Volání metody `TaskOfT_MethodAsync` , které není okamžitě očekáváno, vrátí `Task(Of Integer)`, dle očekávání od deklarace metody. Úkol je přidělen `integerTask` proměnné v příkladu. Protože `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult`. V tomto případě TResult představuje typ integer. Když `Await` platí pro `integerTask`, výraz await se vyhodnocuje na obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost `integerTask`. Je hodnota přiřazená `result2` proměnné.  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastností je vlastnost blokování. Pokud se pokusíte o přístup k ní před dokončením její úlohy, blokovaný vláknem, které je právě aktivní až do dokončení úlohy a hodnota je k dispozici. Ve většině případů byste měli přistupovat k hodnotě pomocí `Await` namísto přímého přístupu.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 Zobrazení příkazů v následujícím kódu ověřte, že hodnoty `result1` proměnné, `result2` proměnnou a `Result` vlastnosti jsou stejné. Mějte na paměti, `Result` vlastností je vlastnost blokování a by neměl být přístupný, než bylo očekáváno úkolem.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
## <a name="BKMK_TaskReturnType"></a> Návratový typ úlohy  
 Asynchronní metody, které neobsahují příkaz return nebo obsahující příkaz return, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>. Tyto metody by měly [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postupy, pokud byly napsány, aby běžely synchronně. Pokud používáte `Task` návratový typ pro asynchronní metodu, volající metoda můžete použít `Await` operátor k pozastavení dokončení volajícího až do dokončení volané asynchronní metody.  
  
 V následujícím příkladu asynchronní metoda `Task_MethodAsync` neobsahuje příkaz return. Tedy zadáte návratový typ `Task` pro metodu, která umožňuje `Task_MethodAsync` do ní použít operátor await. Definice `Task` neobsahuje `Result` vlastnost k ukládání vrácené hodnoty.  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 `Task_MethodAsync` je volán a očekáván pomocí příkazu await namísto výrazu await, podobného volání příkazu pro synchronní `Sub` nebo metody vracející hodnotu void. Použití `Await` operátor v tomto případě nevytvoří hodnotu.  
  
 Následující kód volá a čeká metodu `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Stejně jako v předchozím <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit volání `Task_MethodAsync` od aplikace `Await` operátoru, jak ukazuje následující kód. Nezapomeňte však, že `Task` nemá `Result` vlastnost a že se při použití operátoru await nevytvoří žádná hodnota `Task`.  
  
 Následující kód oddělí volání `Task_MethodAsync` z čekajícího na úkol, který `Task_MethodAsync` vrátí.  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
## <a name="BKMK_VoidReturnType"></a> Návratový typ void  
 Primární použití `Sub` postupy je v obslužných rutinách událostí, kde neexistuje žádný návratový typ (označované jako návratový typ void v jiných jazycích). Vrácení void lze použít také k přepsání metod vracejících void nebo pro metody, které vykonávají činnosti, které lze označit jako "vypal a zapomeň." Nicméně, měli byste vrátit `Task` kdykoli je to možné, protože asynchronní metody vracející typ void nemůže být očekávána. Jakýkoli volající této metody musí být schopen pokračovat v dokončení bez čekání na dokončení volané asynchronní metody a volající musí být nezávislé na všech hodnotách nebo výjimkách, které generuje asynchronní metoda.  
  
 Volající asynchronní metody vracející typ void nemůže zachytit výjimky, které jsou vyvolány z metody a takové neošetřené výjimky mohou způsobit selhání aplikace. Pokud dojde k výjimce v asynchronní metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, výjimka je uložen v rámci vrácené úlohy a znovu vyvolána při očekávání úkolu. Proto se ujistěte, že asynchronní metody, které mohou způsobit výjimku má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávaná.  
  
 Další informace o tom, jak zachytávat výjimky v asynchronních metodách, naleznete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Následující kód definuje asynchronní obslužnou rutinu události.  
  
```vb  
' SUB EXAMPLE  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
    textBox1.Clear()  
  
    ' Start the process and await its completion. DriverAsync is a   
    ' Task-returning async method.  
    Await DriverAsync()  
  
    ' Say goodbye.  
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
End Sub  
```  
  
## <a name="BKMK_Example"></a> Kompletní příklad  
 Následující projekt Windows Presentation Foundation (WPF) obsahuje příklady kódů z tohoto tématu.  
  
 Spusťte projekt, proveďte následující kroky:  
  
1.  Spusťte Visual Studio.  
  
2.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3.  V **nainstalováno**, **šablony** kategorie, zvolte **jazyka Visual Basic**a klikněte na tlačítko **Windows**. Zvolte **aplikace WPF** ze seznamu typů projektů.  
  
4.  Zadejte `AsyncReturnTypes` jako název projektu a klikněte na tlačítko **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
5.  V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.  
  
     Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **otevřete**.  
  
6.  V **XAML** okno soubor mainwindow.XAML nahraďte kód následujícím kódem.  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** okna souboru mainwindow.XAML.  
  
7.  V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.  
  
8.  Nahraďte kód v souboru MainWindow.xaml.vb následujícím kódem.  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
     By se zobrazit následující výstup.  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Tok řízení v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)
