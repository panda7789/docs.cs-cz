---
title: Asynchronní návratové typy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 0c6c02efd282f8581f3dc85905149acf7b3ea6ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644079"
---
# <a name="async-return-types-visual-basic"></a>Asynchronní návratové typy (Visual Basic)
Asynchronní metody mít tři možné návratové typy: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>a void. V jazyce Visual Basic, typ vrácené hodnoty void zapisuje jako [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postupu. Další informace o asynchronní metody najdete v tématu [asynchronní programování s Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 V jednom z těchto částí je zkontrolován každý návratový typ a najdete úplný příklad, který používá všechny tři typy na konci tohoto tématu.  
  
> [!NOTE]
>  Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.  
  
##  <a name="BKMK_TaskTReturnType"></a> Návratový typ Task(T)  
 <xref:System.Threading.Tasks.Task%601> Vrátí typ se používá pro asynchronní metody, která obsahuje [vrátit](../../../../visual-basic/language-reference/statements/return-statement.md) příkaz, ve kterém má operand typu `TResult`.  
  
 V následujícím příkladu `TaskOfT_MethodAsync` asynchronní metody obsahuje příkaz return, který vrátí celé číslo. Proto deklarace metody musíte zadat návratový typ `Task(Of Integer)`.  
  
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
  
 Když `TaskOfT_MethodAsync` je volána z ve výrazu await výraz await načte celočíselnou hodnotu (hodnota `leisureHours`) který je uložený v úloze, která je vrácena `TaskOfT_MethodAsync`. Další informace o await výrazy najdete v tématu [Await – operátor](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 Následující kód volá a čeká metoda `TaskOfT_MethodAsync`. Výsledkem je přiřazena k `result1` proměnné.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Můžete lépe pochopit, jak tomu oddělením volání `TaskOfT_MethodAsync` z používání `Await`, jak ukazuje následující kód. Volání metody `TaskOfT_MethodAsync` , není okamžitě očekávaná vrátí `Task(Of Integer)`, jak očekáváte od deklaraci metody. Úloha je přiřazená `integerTask` proměnné v příkladu. Protože `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult`. V takovém případě TResult představuje celočíselného typu. Když `Await` se použije pro `integerTask`, await vyhodnocen jako obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost `integerTask`. Hodnota je přiřazena k `result2` proměnné.  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Je blokování vlastnost. Pokud se pokusíte k němu přístup před dokončení úkolu, vláken, který je aktuálně aktivní je blokován, dokud úloha dokončí, a hodnota je k dispozici. Ve většině případů byste měli hodnota přistupovat pomocí `Await` místo přístupu k vlastnosti.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 Zobrazení příkazy v následujícím kódu ověřte, že hodnoty `result1` proměnnou `result2` proměnnou a `Result` vlastnosti jsou stejné. Nezapomeňte, že `Result` vlastnost je blokování vlastnost a neměli přístup než úkolu bylo očekáváno.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a> Návratový typ úlohy  
 Asynchronní metody, které neobsahují žádný příkaz return nebo obsahují příkaz return, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>. Tyto metody by [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) postupy napsané spustit synchronně. Pokud používáte `Task` návratový typ pro asynchronní metody, můžete použít volání metody `Await` operátor volajícího dokončení pozastavit, dokud volané asynchronní metody dokončení.  
  
 V následujícím příkladu, asynchronní metody `Task_MethodAsync` neobsahuje příkaz return. Proto můžete zadat návratový typ `Task` pro metodu, která umožňuje `Task_MethodAsync` k být očekáváno. Definice `Task` neobsahuje typ `Result` vlastnost k uložení návratovou hodnotu.  
  
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
  
 `Task_MethodAsync` je volána a očekávaná pomocí příkazu await místo await výrazu podobné volání příkazu pro synchronního `Sub` nebo metoda vrací void. Použití `Await` operátor v tomto případě neobsahuje hodnotu.  
  
 Následující kód volá a čeká metoda `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Stejně jako v předchozí <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit volání `Task_MethodAsync` z používání `Await` operátor, jak ukazuje následující kód. Nezapomeňte však, že `Task` nemá `Result` vlastnost a že při použití operátoru await vytváří žádná hodnota `Task`.  
  
 Následující kód odděluje volání `Task_MethodAsync` z čeká na úlohy, `Task_MethodAsync` vrátí.  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <a name="BKMK_VoidReturnType"></a> Typ vrácené hodnoty void  
 Primárním použitím `Sub` procedury je v obslužné rutiny událostí, kde není žádný návratový typ (označované jako typ vrácené hodnoty void v jiných jazycích). Void vrátit lze použít také k přepsání metody vrácení void nebo metod, které provádějí aktivity, které můžou být zařazené do kategorie jako "fire a zapomenete." Ale by měla vrátit `Task` kdykoli je to možné, protože nemůže být očekáváno asynchronní metody vrácení void. Všechny volající tato metoda musí být schopen dál dokončení bez čekání na volané asynchronní metody dokončení a volající musí být nezávislé na všechny hodnoty nebo které generuje asynchronní metody.  
  
 Volající asynchronní metody vrácení void nelze catch výjimky, které jsou vyvolány z metody a může způsobit selhání aplikace jsou takové neošetřené výjimky. Pokud dojde k výjimce v asynchronní metody, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, výjimka je uložen ve vrácené úloh a znovu vyvolány, když je očekáváno úlohu. Proto se ujistěte, že asynchronní metody, která může vytvořit výjimku má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že jsou očekáváno volání metody.  
  
 Další informace o tom, jak zachycení výjimek v asynchronní metody najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Následující kód definuje obslužnou rutinu události asynchronní.  
  
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
  
##  <a name="BKMK_Example"></a> Úplný příklad  
 Následující projekt Windows Presentation Foundation (WPF) obsahuje příklady kódu z tohoto tématu.  
  
 Pokud chcete spustit projekt, proveďte následující kroky:  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **nainstalovaná**, **šablony** kategorie, zvolte **jazyka Visual Basic**a potom zvolte **Windows**. Zvolte **aplikaci WPF** ze seznamu typy projektů.  
  
4.  Zadejte `AsyncReturnTypes` jako název projektu a klikněte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
5.  V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.  
  
     Pokud na kartě se nezobrazí, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **otevřete**.  
  
6.  V **XAML** okno MainWindow.xaml, nahraďte kód následujícím kódem.  
  
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
  
     Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhu** okno MainWindow.xaml.  
  
7.  V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.vb a potom zvolte **kód zobrazení**.  
  
8.  Nahraďte kód v MainWindow.xaml.vb následujícím kódem.  
  
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
  
9. Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
 [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)
