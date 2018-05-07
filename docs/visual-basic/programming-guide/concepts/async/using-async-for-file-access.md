---
title: Použití modifikátoru Async pro přístup k souborům (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: e12eaa57d0f7186e9d281b89ec3abd26280e12ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-async-for-file-access-visual-basic"></a>Použití modifikátoru Async pro přístup k souborům (Visual Basic)
Můžete použít funkci Async pro přístup k souborům. Pomocí funkce asynchronní můžete volat do asynchronní metody bez použití zpětná volání nebo rozdělení kódu mezi více metod nebo výrazy lambda. Chcete-li synchronní kód asynchronní, právě volání asynchronní metody místo synchronní metody a přidejte několik klíčových slov do kódu.  
  
 Můžete zvážit z následujících důvodů pro přidání asynchrony do souboru přístup volání:  
  
-   Asynchrony zadává uživatelského rozhraní aplikace rychlejšího protože vlákna uživatelského rozhraní, která spustí operace můžete provádět jinou práci. Pokud vlákna uživatelského rozhraní musí být spuštěn kód která trvá dlouhou dobu (například více než 50 milisekund), rozhraní může zmrazit až po dokončení vstupy/výstupy a vlákna uživatelského rozhraní můžete znovu zpracovat klávesnice a myši vstupní a dalších událostí.  
  
-   Asynchrony zlepšuje škálovatelnost technologie ASP.NET a dalších serverových aplikací, protože snižuje potřebu vláken. Pokud aplikace používá vyhrazený vlákno na jeden odpovědi a tisíce požadavky jsou právě zpracovávány současně, je potřeba tisíce vláken. Asynchronní operace často není třeba použít během čekání vlákno. Na konci stručně používají existující vlákno dokončení vstupně-výstupní operace.  
  
-   Latence operace přístupu k souboru může být velmi nízkou v aktuální podmínkách, ale latence může výrazně zvýšit v budoucnu. Například může přesunout soubor na server, který je po celém světě.  
  
-   Přidaném režijní náklady na použití funkce asynchronní je malá.  
  
-   Asynchronní úlohy můžete spustit snadno paralelně.  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Pokud chcete spustit v příkladech v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **formulářové aplikace Windows** a poté přidejte **tlačítko**. U tlačítka `Click` událostí, přidejte volání do první metodu v obou příkladech.  
  
 V následujících příkladech, patří `Imports` příkazy.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Použití třídy FileStream  
 V příkladech v tomto tématu <xref:System.IO.FileStream> třídy, která má možnost, která způsobí, že asynchronní vstupně-výstupních operací na úrovni operačního systému. Pomocí této možnosti se můžete vyhnout blokování podproces fondu podprocesů v mnoha případech. Chcete-li tuto možnost, zadejte `useAsync=true` nebo `options=FileOptions.Asynchronous` argument ve volání konstruktoru.  
  
 Nemůžete použít tuto možnost s <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> Pokud otevřít přímo tak, že zadáte cestu k souboru. Ale můžete použít tuto možnost, pokud jste zadali, je <xref:System.IO.Stream> , <xref:System.IO.FileStream> třída otevřít. Upozorňujeme, že asynchronní volání jsou rychlejší v uživatelském rozhraní aplikace i v případě, že fondu vláken je blokovaný, protože vlákna uživatelského rozhraní není blokován během čekání.  
  
## <a name="writing-text"></a>Zápis textu  
 Následující příklad zapíše text do souboru. Na každé await prohlášení, metoda okamžitě ukončí. Po dokončení soubor vstupně-výstupních operací na příkaz, který následuje příkaz await obnoví metodu. Všimněte si, že se modifikátor asynchronní v definici metody, které používají příkaz await.  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 V původní příkladu má příkaz `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, což je zmenšení následující dva příkazy:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 První příkaz vrátí úlohu a způsobí, že při zpracování souboru spustit. Druhý příkaz se await způsobí, že metoda okamžitě ukončit a vrátit různých úloh. Po dokončení zpracování později souborů provádění vrátí příkaz, který následuje await. Další informace najdete v tématu [řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Čtení textu  
 Následující příklad načte text ze souboru. Text je uložená do vyrovnávací paměti a v takovém případě bude umístěn do <xref:System.Text.StringBuilder>. Na rozdíl od v předchozím příkladu vytvoří vyhodnocení await hodnotu. <xref:System.IO.Stream.ReadAsync%2A> Metoda vrátí <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vytváří vyhodnocení await `Int32` hodnotu (`numRead`) po dokončení operace. Další informace najdete v tématu [asynchronní vrátit typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstup-výstup  
 Následující příklad ukazuje paralelní zpracování napsáním 10 textových souborů. Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úlohu, která se pak přidá do seznamu úloh. `Await Task.WhenAll(tasks)` Příkaz ukončí metodu a obnoví v rámci metody při zpracování souboru dokončete pro všechny úlohy.  
  
 Příklad zavření všech <xref:System.IO.FileStream> instancí v `Finally` blokovat po dokončení úlohy. Pokud každý `FileStream` místo toho byl vytvořen v `Imports` příkaz, `FileStream` může probíhat za před dokončení úlohy.  
  
 Všimněte si, že žádné zvýšení výkonu je téměř úplně z paralelní zpracování a není asynchronní zpracování. Výhody asynchrony jsou ho nebude vytížit více vláken a že není vytížit vlákna uživatelského rozhraní.  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 Při použití <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> metod, můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít se zrušit operaci střední datového proudu. Další informace najdete v tématu [Fine-Tuning vaše asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [Řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
