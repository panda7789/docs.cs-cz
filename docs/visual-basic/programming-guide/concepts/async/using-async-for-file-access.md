---
title: Použití modifikátoru Async pro přístup k souborům (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: dac3348657310a38284d9b6680082050a07e19bb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642423"
---
# <a name="using-async-for-file-access-visual-basic"></a>Použití modifikátoru Async pro přístup k souborům (Visual Basic)
Můžete použít funkci Async pro přístup k souborům. Pomocí asynchronní funkce může volat do asynchronní metody bez pomocí zpětných volání a rozdělení kódu mezi více metodách a výrazech lambda. Aby synchronního kódu asynchronní, stačí volání asynchronní metody namísto synchronní metody a do kódu přidat několik klíčových slov.  
  
 Můžete zvážit následující důvody pro přidání asynchronii volání přístup k souboru:  
  
- Asynchronie urychluje uživatelského rozhraní aplikace odezvu vzhledem k tomu, že vlákno uživatelského rozhraní, který se spustí operace můžete provádět jinou práci. Pokud vlákno uživatelského rozhraní musí být spuštěn kód, který trvá moc dlouho (například více než 50 MS), uživatelské rozhraní může zablokovat až do dokončení vstupy/výstupy a znovu zpracovávat klávesnice a myš události vstupu a jiné vlákno uživatelského rozhraní.  
  
- Asynchronie zlepšuje škálovatelnost technologie ASP.NET a jiných serverových aplikací tím, že snižuje potřebu vlákna. Pokud aplikace používá vyhrazeném vlákně na odpověď a jsou právě tisíc požadavky zpracovávány současně, nejsou potřeba tisíc vlákna. Asynchronních operací často není nutné používat vlákno při čekání. Na konci stručně používají existující vlákno dokončení vstupně-výstupních operací.  
  
- Latence operace přístupu k souboru může být velmi nízkou pod aktuální podmínky, ale latence může výrazně zlepšit v budoucnu. Soubor může například přesunout na server, který je po celém světě.  
  
- Přidaný režijní náklady na použití asynchronní funkce je malý.  
  
- Asynchronní úlohy můžete snadno spouštět paralelně.  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Pro spuštění příkladů v tomto tématu, můžete vytvořit **aplikace WPF** nebo **formulářová aplikace Windows** a pak přidejte **tlačítko**. Na tlačítku `Click` události, přidejte volání metody první v obou příkladech.  
  
 V následujících příkladech, patří `Imports` příkazy.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Použijte datový proud souboru třídy  
 V příkladech v tomto tématu <xref:System.IO.FileStream> třídu, která má možnost, která způsobí, že asynchronní vstupně-výstupních operací na úrovni operačního systému. Pomocí této možnosti byste se vyhnout blokování vlákna fondu vláken v mnoha případech. Chcete-li povolit tuto možnost, zadejte `useAsync=true` nebo `options=FileOptions.Asynchronous` argument ve volání konstruktoru.  
  
 Tuto možnost s nelze použít <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> Pokud otevřít přímo zadáním cesty k souboru. Ale můžete použít tuto možnost, pokud jim poskytujete <xref:System.IO.Stream> , který <xref:System.IO.FileStream> třídy otevřít. Všimněte si, že byla zahájena asynchronní volání jsou rychlejší v uživatelském rozhraní aplikace i v případě, že vláken fondu vláken se zablokuje, protože vlákno uživatelského rozhraní není blokována během čekání.  
  
## <a name="writing-text"></a>Zápis textu  
 Následující příklad zapíše text do souboru. V každé await příkaz, metoda se okamžitě ukončí. Po dokončení vstupně-výstupní operace souboru se bude pokračovat na příkazu následujícímu příkazu await metodu. Všimněte si, že modifikátor async je v definici metody, které pomocí příkazu await.  
  
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
  
 Původní příklad obsahuje příkaz `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, což je snížení následující dva příkazy:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 První příkaz vrátí úkol a způsobí, že při zpracování souboru ke spuštění. Druhý příkaz s await způsobí, že metoda okamžitě ukončit a vrátit jiný úkol. Po dokončení zpracování později souborů, spuštění se vrátí k příkazu, který následuje await. Další informace najdete v tématu [tok řízení v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Čtení textu  
 Následující příklad přečte text ze souboru. Text je uložená do vyrovnávací paměti a v takovém případě se umístí do <xref:System.Text.StringBuilder>. Na rozdíl od předchozího příkladu, vytvoří hodnocení await hodnotu. <xref:System.IO.Stream.ReadAsync%2A> Metoda vrátí hodnotu <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vytváří hodnocení await `Int32` hodnotu (`numRead`) po dokončení operace. Další informace najdete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstupně-výstupních operací  
 Následující příklad ukazuje paralelní zpracování napsáním 10 textové soubory. Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úlohu, která se pak přidá do seznamu úkolů. `Await Task.WhenAll(tasks)` Příkaz ukončí metodu a obnoví v rámci metody při zpracování souboru Dokončit pro všechny úlohy.  
  
 V příkladu zavře všechna <xref:System.IO.FileStream> instance `Finally` blokovat po dokončení úlohy. Pokud každý `FileStream` místo toho byl vytvořen v `Imports` příkazu `FileStream` může zrušit, před dokončením úkolu.  
  
 Všimněte si, že všechny zvýšení výkonu je téměř zcela v paralelní zpracování a není asynchronní zpracování. Výhody asynchronie je, že nebude vytížit více vláken a že není vytížit vlákně uživatelského rozhraní.  
  
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
  
 Při použití <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> metody, můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít pro zrušení operace uprostřed datového proudu. Další informace najdete v tématu [asynchronní aplikace Fine-Tuning (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Tok řízení v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
