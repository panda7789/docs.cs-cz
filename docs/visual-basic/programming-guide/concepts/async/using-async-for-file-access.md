---
title: Použití modifikátoru Async pro přístup k souborům (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 0b2b95f1e4f9bc120acdad606b0f15503285057a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814546"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="e23f3-102">Použití modifikátoru Async pro přístup k souborům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e23f3-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="e23f3-103">Můžete použít funkci Async pro přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="e23f3-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="e23f3-104">Pomocí asynchronní funkce může volat do asynchronní metody bez pomocí zpětných volání a rozdělení kódu mezi více metodách a výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="e23f3-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="e23f3-105">Aby synchronního kódu asynchronní, stačí volání asynchronní metody namísto synchronní metody a do kódu přidat několik klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="e23f3-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="e23f3-106">Můžete zvážit následující důvody pro přidání asynchronii volání přístup k souboru:</span><span class="sxs-lookup"><span data-stu-id="e23f3-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="e23f3-107">Asynchronie urychluje uživatelského rozhraní aplikace odezvu vzhledem k tomu, že vlákno uživatelského rozhraní, který se spustí operace můžete provádět jinou práci.</span><span class="sxs-lookup"><span data-stu-id="e23f3-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="e23f3-108">Pokud vlákno uživatelského rozhraní musí být spuštěn kód, který trvá moc dlouho (například více než 50 MS), uživatelské rozhraní může zablokovat až do dokončení vstupy/výstupy a znovu zpracovávat klávesnice a myš události vstupu a jiné vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e23f3-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="e23f3-109">Asynchronie zlepšuje škálovatelnost technologie ASP.NET a jiných serverových aplikací tím, že snižuje potřebu vlákna.</span><span class="sxs-lookup"><span data-stu-id="e23f3-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="e23f3-110">Pokud aplikace používá vyhrazeném vlákně na odpověď a jsou právě tisíc požadavky zpracovávány současně, nejsou potřeba tisíc vlákna.</span><span class="sxs-lookup"><span data-stu-id="e23f3-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="e23f3-111">Asynchronních operací často není nutné používat vlákno při čekání.</span><span class="sxs-lookup"><span data-stu-id="e23f3-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="e23f3-112">Na konci stručně používají existující vlákno dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="e23f3-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="e23f3-113">Latence operace přístupu k souboru může být velmi nízkou pod aktuální podmínky, ale latence může výrazně zlepšit v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="e23f3-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="e23f3-114">Soubor může například přesunout na server, který je po celém světě.</span><span class="sxs-lookup"><span data-stu-id="e23f3-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="e23f3-115">Přidaný režijní náklady na použití asynchronní funkce je malý.</span><span class="sxs-lookup"><span data-stu-id="e23f3-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="e23f3-116">Asynchronní úlohy můžete snadno spouštět paralelně.</span><span class="sxs-lookup"><span data-stu-id="e23f3-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="e23f3-117">Spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="e23f3-117">Running the Examples</span></span>  
 <span data-ttu-id="e23f3-118">Pro spuštění příkladů v tomto tématu, můžete vytvořit **aplikace WPF** nebo **formulářová aplikace Windows** a pak přidejte **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="e23f3-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="e23f3-119">Na tlačítku `Click` události, přidejte volání metody první v obou příkladech.</span><span class="sxs-lookup"><span data-stu-id="e23f3-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="e23f3-120">V následujících příkladech, patří `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e23f3-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="e23f3-121">Použijte datový proud souboru třídy</span><span class="sxs-lookup"><span data-stu-id="e23f3-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="e23f3-122">V příkladech v tomto tématu <xref:System.IO.FileStream> třídu, která má možnost, která způsobí, že asynchronní vstupně-výstupních operací na úrovni operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e23f3-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="e23f3-123">Pomocí této možnosti byste se vyhnout blokování vlákna fondu vláken v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="e23f3-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="e23f3-124">Chcete-li povolit tuto možnost, zadejte `useAsync=true` nebo `options=FileOptions.Asynchronous` argument ve volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e23f3-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="e23f3-125">Tuto možnost s nelze použít <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> Pokud otevřít přímo zadáním cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="e23f3-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="e23f3-126">Ale můžete použít tuto možnost, pokud jim poskytujete <xref:System.IO.Stream> , který <xref:System.IO.FileStream> třídy otevřít.</span><span class="sxs-lookup"><span data-stu-id="e23f3-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="e23f3-127">Všimněte si, že byla zahájena asynchronní volání jsou rychlejší v uživatelském rozhraní aplikace i v případě, že vláken fondu vláken se zablokuje, protože vlákno uživatelského rozhraní není blokována během čekání.</span><span class="sxs-lookup"><span data-stu-id="e23f3-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="e23f3-128">Zápis textu</span><span class="sxs-lookup"><span data-stu-id="e23f3-128">Writing Text</span></span>  
 <span data-ttu-id="e23f3-129">Následující příklad zapíše text do souboru.</span><span class="sxs-lookup"><span data-stu-id="e23f3-129">The following example writes text to a file.</span></span> <span data-ttu-id="e23f3-130">V každé await příkaz, metoda se okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="e23f3-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="e23f3-131">Po dokončení vstupně-výstupní operace souboru se bude pokračovat na příkazu následujícímu příkazu await metodu.</span><span class="sxs-lookup"><span data-stu-id="e23f3-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="e23f3-132">Všimněte si, že modifikátor async je v definici metody, které pomocí příkazu await.</span><span class="sxs-lookup"><span data-stu-id="e23f3-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="e23f3-133">Původní příklad obsahuje příkaz `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, což je snížení následující dva příkazy:</span><span class="sxs-lookup"><span data-stu-id="e23f3-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="e23f3-134">První příkaz vrátí úkol a způsobí, že při zpracování souboru ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="e23f3-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="e23f3-135">Druhý příkaz s await způsobí, že metoda okamžitě ukončit a vrátit jiný úkol.</span><span class="sxs-lookup"><span data-stu-id="e23f3-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="e23f3-136">Po dokončení zpracování později souborů, spuštění se vrátí k příkazu, který následuje await.</span><span class="sxs-lookup"><span data-stu-id="e23f3-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="e23f3-137">Další informace najdete v tématu [tok řízení v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="e23f3-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="e23f3-138">Čtení textu</span><span class="sxs-lookup"><span data-stu-id="e23f3-138">Reading Text</span></span>  
 <span data-ttu-id="e23f3-139">Následující příklad přečte text ze souboru.</span><span class="sxs-lookup"><span data-stu-id="e23f3-139">The following example reads text from a file.</span></span> <span data-ttu-id="e23f3-140">Text je uložená do vyrovnávací paměti a v takovém případě se umístí do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="e23f3-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="e23f3-141">Na rozdíl od předchozího příkladu, vytvoří hodnocení await hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e23f3-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="e23f3-142"><xref:System.IO.Stream.ReadAsync%2A> Metoda vrátí hodnotu <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vytváří hodnocení await `Int32` hodnotu (`numRead`) po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="e23f3-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="e23f3-143">Další informace najdete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="e23f3-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="e23f3-144">Paralelní asynchronní vstupně-výstupních operací</span><span class="sxs-lookup"><span data-stu-id="e23f3-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="e23f3-145">Následující příklad ukazuje paralelní zpracování napsáním 10 textové soubory.</span><span class="sxs-lookup"><span data-stu-id="e23f3-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="e23f3-146">Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úlohu, která se pak přidá do seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="e23f3-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="e23f3-147">`Await Task.WhenAll(tasks)` Příkaz ukončí metodu a obnoví v rámci metody při zpracování souboru Dokončit pro všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="e23f3-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="e23f3-148">V příkladu zavře všechna <xref:System.IO.FileStream> instance `Finally` blokovat po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="e23f3-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="e23f3-149">Pokud každý `FileStream` místo toho byl vytvořen v `Imports` příkazu `FileStream` může zrušit, před dokončením úkolu.</span><span class="sxs-lookup"><span data-stu-id="e23f3-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="e23f3-150">Všimněte si, že všechny zvýšení výkonu je téměř zcela v paralelní zpracování a není asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="e23f3-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="e23f3-151">Výhody asynchronie je, že nebude vytížit více vláken a že není vytížit vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e23f3-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="e23f3-152">Při použití <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> metody, můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít pro zrušení operace uprostřed datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e23f3-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="e23f3-153">Další informace najdete v tématu [asynchronní aplikace Fine-Tuning (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="e23f3-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23f3-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e23f3-154">See also</span></span>

- [<span data-ttu-id="e23f3-155">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e23f3-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="e23f3-156">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e23f3-156">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="e23f3-157">Tok řízení v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e23f3-157">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
