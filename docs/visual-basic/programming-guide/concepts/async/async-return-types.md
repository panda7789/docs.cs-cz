---
title: Asynchronní návratové typy
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 96d3a945a49a12f7c2d5d60e8ee59ce047a0bae6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347982"
---
# <a name="async-return-types-visual-basic"></a>Asynchronní návratové typy (Visual Basic)

Asynchronní metody mají tři možné návratové typy: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>a void. V Visual Basic typ vrácené hodnoty void je zapsán jako procedura [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) . Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Každý návratový typ je zkontrolován v jednom z následujících sekcí a můžete najít úplný příklad, který používá všechny tři typy na konci tématu.

> [!NOTE]
> Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

## <a name="BKMK_TaskTReturnType"></a>Návratový typ úlohy (T)

<xref:System.Threading.Tasks.Task%601> návratový typ se používá pro asynchronní metodu, která obsahuje příkaz [return](../../../../visual-basic/language-reference/statements/return-statement.md) , ve kterém je operand typu `TResult`.

V následujícím příkladu `TaskOfT_MethodAsync` asynchronní metoda obsahuje příkaz return, který vrací celé číslo. Proto musí deklarace metody určit návratový typ `Task(Of Integer)`.

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

Když je volána `TaskOfT_MethodAsync` v rámci výrazu await, výraz await načte celočíselnou hodnotu (hodnotu `leisureHours`), která je uložena v úloze, kterou vrací `TaskOfT_MethodAsync`. Další informace o výrazech await naleznete v tématu [operátor await](../../../../visual-basic/language-reference/operators/await-operator.md).

Následující kód volá metodu and očekává `TaskOfT_MethodAsync`. Výsledek je přiřazen proměnné `result1`.

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

Můžete lépe porozumět tomu, jak se to stane, oddělením volání `TaskOfT_MethodAsync` od aplikace `Await`, jak ukazuje následující kód. Volání metody `TaskOfT_MethodAsync`, které není okamžitě očekáváno, vrací `Task(Of Integer)`, jak byste očekávali od deklarace metody. Úloha je přiřazena k proměnné `integerTask` v příkladu. Vzhledem k tomu, že `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje vlastnost <xref:System.Threading.Tasks.Task%601.Result> typu `TResult`. V tomto případě TResult představuje typ Integer. Při použití `Await` pro `integerTask`se výraz await vyhodnocuje na obsah vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A> `integerTask`. Hodnota je přiřazena proměnné `result2`.

> [!WARNING]
> Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> je vlastnost blokující. Pokud se pokusíte o přístup k tomuto úkolu před jeho dokončením, bude vlákno, které je aktuálně aktivní, blokováno, dokud se úloha nedokončí a hodnota nebude k dispozici. Ve většině případů byste měli k hodnotě přistupovat pomocí `Await` místo přímého přístupu k vlastnosti.

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

Příkazy zobrazení v následujícím kódu ověřují, zda jsou hodnoty proměnné `result1`, `result2` proměnnou a vlastnost `Result` stejné. Mějte na paměti, že vlastnost `Result` je vlastnost blokující a neměla by k ní být přistupovaná před tím, než byla úloha očekávána.

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="BKMK_TaskReturnType"></a>Návratový typ úlohy

Asynchronní metody, které neobsahují příkaz return nebo obsahující příkaz return, který nevrací operand, obvykle mají návratový typ <xref:System.Threading.Tasks.Task>. Tyto metody by byly procedury [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , pokud byly zapsány pro spuštění synchronně. Použijete-li návratový typ `Task` pro asynchronní metodu, volající metoda může použít operátor `Await` k pozastavení dokončování volajícího až do dokončení volané asynchronní metody.

V následujícím příkladu asynchronní metoda `Task_MethodAsync` neobsahuje příkaz return. Proto zadáte návratový typ `Task` pro metodu, která umožňuje očekávat `Task_MethodAsync`. Definice typu `Task` neobsahuje vlastnost `Result` pro uložení návratové hodnoty.

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

`Task_MethodAsync` se volá a očekává se pomocí příkazu await namísto výrazu await, podobně jako volání příkazu pro synchronní `Sub` nebo metodu vracející typ void. Použití operátoru `Await` v tomto případě nevytvoří hodnotu.

Následující kód volá metodu and očekává `Task_MethodAsync`.

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

Stejně jako v předchozím příkladu <xref:System.Threading.Tasks.Task%601> můžete oddělit volání `Task_MethodAsync` od aplikace operátoru `Await`, jak ukazuje následující kód. Nezapomeňte však, že `Task` nemá vlastnost `Result` a že při použití operátoru await na `Task`není vytvořena žádná hodnota.

Následující kód odděluje volání `Task_MethodAsync` od čekání na úkol, který `Task_MethodAsync` vrací.

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a>Návratový typ void

Primární použití procedur `Sub` je v obslužných rutinách událostí, kde neexistuje návratový typ (v jiných jazycích se označuje jako návratový typ void). Návratový typ void také lze použít k přepsání metod vracejících anulování nebo pro metody, které provádějí aktivity, které mohou být zařazeny do kategorie "oheň a zapomenout". Měli byste však vracet `Task` všude, kde je to možné, protože asynchronní metodu vracející anulování nelze očekávat. Každý volající takové metody musí být schopný pokračovat v dokončování bez čekání na dokončení volané asynchronní metody a volající musí být nezávislý na všech hodnotách nebo výjimkách, které asynchronní metoda generuje.

Volající asynchronní metody vracející hodnotu void nemůže zachytit výjimky, které jsou vyvolány z metody, a tyto neošetřené výjimky pravděpodobně způsobí selhání aplikace. Pokud dojde k výjimce v asynchronní metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, je výjimka uložena v vrácené úloze a znovu vyvolána, když je úkol očekáván. Proto se ujistěte, že jakákoliv asynchronní metoda, která může vyvolat výjimku, má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávána.

Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

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

## <a name="BKMK_Example"></a>Kompletní příklad

Následující projekt Windows Presentation Foundation (WPF) obsahuje příklady kódu z tohoto tématu.

 Chcete-li spustit projekt, proveďte následující kroky:

1. Spusťte Visual Studio.

2. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V kategorii **nainstalováno**, **šablony** zvolte možnost **Visual Basic**a pak zvolte možnost **Windows**. V seznamu typů projektů vyberte možnost **aplikace WPF** .

4. Jako název projektu zadejte `AsyncReturnTypes` a pak klikněte na tlačítko **OK** .

     Nový projekt se zobrazí v **Průzkumník řešení**.

5. V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .

     Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **otevřít**.

6. V okně **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.

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

     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v okně **Návrh** souboru MainWindow. XAML.

7. V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.

8. Nahraďte kód v souboru MainWindow. XAML. vb následujícím kódem.

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
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

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
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .

     Měl by se zobrazit následující výstup:

    ```console
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
- [Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)
