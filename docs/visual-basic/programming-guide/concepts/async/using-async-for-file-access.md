---
title: Použití modifikátoru Async pro přístup k souborům
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 803d182f5b0f3071feb7aae4945bc3c0a1fd82c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349113"
---
# <a name="using-async-for-file-access-visual-basic"></a>Použití Async pro přístup k souborům (Visual Basic)
K přístupu k souborům můžete použít funkci Async. Pomocí asynchronní funkce můžete zavolat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu napříč více metodami nebo lambda výrazy. Chcete-li synchronní asynchronní kód, stačí zavolat asynchronní metodu namísto synchronní metody a přidat k kódu několik klíčových slov.  
  
 Při přidávání asynchronii do volání přístupu k souborům můžete zvážit následující důvody:  
  
- Asynchronii umožňuje aplikacím uživatelského rozhraní lépe reagovat, protože vlákno uživatelského rozhraní, které spouští operaci, může provádět i jinou práci. Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), může uživatelské rozhraní zablokovat až do dokončení vstupně-výstupních operací a vlákno uživatelského rozhraní může znovu zpracovat vstupy klávesnice a myši a další události.  
  
- Asynchronii zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací tím, že snižuje nutnost vláken. Pokud aplikace používá vyhrazené vlákno na reakci a tisíce požadavků jsou zpracovávány současně, je zapotřebí tisíce vláken. Asynchronní operace často nepotřebují použít vlákno během čekání. Na konci se krátce používají existující vlákna dokončení v/v.  
  
- Latence operace přístupu k souboru může být v rámci současných podmínek velmi nízká, ale latence může výrazně zvýšit i v budoucnu. Soubor může být například přesunut na server, který je na celém světě.  
  
- Přidaná režie použití asynchronní funkce je malá.  
  
- Asynchronní úlohy lze snadno spustit paralelně.  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Chcete-li spustit příklady v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **aplikaci model Windows Forms** a pak přidat **tlačítko**. V události `Click` tlačítka přidejte do prvního příkladu volání první metody.  
  
 V následujících příkladech zahrňte následující příkazy `Imports`.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Použití třídy FileStream  
 Příklady v tomto tématu používají třídu <xref:System.IO.FileStream>, která má možnost, která způsobí, že asynchronní vstupně-výstupní operace proběhne na úrovni operačního systému. Pomocí této možnosti se můžete vyhnout blokování vlákna fondu vláken v mnoha případech. Tuto možnost povolíte zadáním argumentu `useAsync=true` nebo `options=FileOptions.Asynchronous` ve volání konstruktoru.  
  
 Tuto možnost nelze použít u <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter>, pokud je otevřete přímo zadáním cesty k souboru. Tuto možnost však můžete použít, pokud jim poskytnete <xref:System.IO.Stream>, že se třída <xref:System.IO.FileStream> otevřela. Všimněte si, že asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že je vlákno nevláken blokované, protože během čekání není zablokované vlákno uživatelského rozhraní.  
  
## <a name="writing-text"></a>Zápis textu  
 Následující příklad zapisuje text do souboru. V každém příkazu await se metoda okamžitě ukončí. Po dokončení vstupně-výstupních operací se metoda obnoví v příkazu, který následuje po příkazu await. Všimněte si, že modifikátor Async je v definici metod, které používají příkaz await.  
  
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
  
 Původní příklad obsahuje příkaz `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, což je kontrakt následujících dvou příkazů:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 První příkaz vrátí úlohu a způsobí, že se zpracování souboru spustí. Druhý příkaz s operátorem await způsobí, že metoda okamžitě ukončí a vrátí jiný úkol. Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za operátorem await. Další informace najdete v tématu [řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Čtení textu  
 Následující příklad přečte text ze souboru. Text je uložen do vyrovnávací paměti a v tomto případě je umístěn do <xref:System.Text.StringBuilder>. Na rozdíl od předchozího příkladu vyhodnocení await vytvoří hodnotu. Metoda <xref:System.IO.Stream.ReadAsync%2A> vrátí <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, takže hodnocení Await vytvoří `Int32` hodnotu (`numRead`) po dokončení operace. Další informace naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstupně-výstupní operace  
 Následující příklad znázorňuje paralelní zpracování zápisem 10 textových souborů. Pro každý soubor metoda <xref:System.IO.Stream.WriteAsync%2A> vrátí úkol, který je poté přidán do seznamu úkolů. Příkaz `Await Task.WhenAll(tasks)` ukončí metodu a pokračuje v rámci metody, když je zpracování souborů dokončeno pro všechny úlohy.  
  
 Tento příklad uzavře všechny instance <xref:System.IO.FileStream> v bloku `Finally` po dokončení úkolů. Pokud byl každý `FileStream` vytvořen v příkazu `Imports`, `FileStream` může být odstraněn před dokončením úkolu.  
  
 Všimněte si, že veškeré zvýšení výkonu je prakticky zcela úplné od paralelního zpracování, nikoli z asynchronního zpracování. Výhody asynchronii jsou, že neodkazují na více vláken a že nevyužívají vlákno uživatelského rozhraní.  
  
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
  
 Při použití metod <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít k zrušení operace střední-Stream. Další informace najdete v tématu [jemné ladění asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
