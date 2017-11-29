---
title: "Použití modifikátoru Async pro přístup k souborům (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 329ae43f8752fbe8a7167b57cb710cc53c0ec247
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="6967d-102">Použití modifikátoru Async pro přístup k souborům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6967d-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="6967d-103">Můžete použít funkci Async pro přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="6967d-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="6967d-104">Pomocí funkce asynchronní můžete volat do asynchronní metody bez použití zpětná volání nebo rozdělení kódu mezi více metod nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="6967d-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="6967d-105">Chcete-li synchronní kód asynchronní, právě volání asynchronní metody místo synchronní metody a přidejte několik klíčových slov do kódu.</span><span class="sxs-lookup"><span data-stu-id="6967d-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="6967d-106">Můžete zvážit z následujících důvodů pro přidání asynchrony do souboru přístup volání:</span><span class="sxs-lookup"><span data-stu-id="6967d-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="6967d-107">Asynchrony zadává uživatelského rozhraní aplikace rychlejšího protože vlákna uživatelského rozhraní, která spustí operace můžete provádět jinou práci.</span><span class="sxs-lookup"><span data-stu-id="6967d-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="6967d-108">Pokud vlákna uživatelského rozhraní musí být spuštěn kód která trvá dlouhou dobu (například více než 50 milisekund), rozhraní může zmrazit až po dokončení vstupy/výstupy a vlákna uživatelského rozhraní můžete znovu zpracovat klávesnice a myši vstupní a dalších událostí.</span><span class="sxs-lookup"><span data-stu-id="6967d-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="6967d-109">Asynchrony zlepšuje škálovatelnost technologie ASP.NET a dalších serverových aplikací, protože snižuje potřebu vláken.</span><span class="sxs-lookup"><span data-stu-id="6967d-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="6967d-110">Pokud aplikace používá vyhrazený vlákno na jeden odpovědi a tisíce požadavky jsou právě zpracovávány současně, je potřeba tisíce vláken.</span><span class="sxs-lookup"><span data-stu-id="6967d-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="6967d-111">Asynchronní operace často není třeba použít během čekání vlákno.</span><span class="sxs-lookup"><span data-stu-id="6967d-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="6967d-112">Na konci stručně používají existující vlákno dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="6967d-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="6967d-113">Latence operace přístupu k souboru může být velmi nízkou v aktuální podmínkách, ale latence může výrazně zvýšit v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="6967d-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="6967d-114">Například může přesunout soubor na server, který je po celém světě.</span><span class="sxs-lookup"><span data-stu-id="6967d-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="6967d-115">Přidaném režijní náklady na použití funkce asynchronní je malá.</span><span class="sxs-lookup"><span data-stu-id="6967d-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="6967d-116">Asynchronní úlohy můžete spustit snadno paralelně.</span><span class="sxs-lookup"><span data-stu-id="6967d-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="6967d-117">Spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="6967d-117">Running the Examples</span></span>  
 <span data-ttu-id="6967d-118">Pokud chcete spustit v příkladech v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **formulářové aplikace Windows** a poté přidejte **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="6967d-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="6967d-119">U tlačítka `Click` událostí, přidejte volání do první metodu v obou příkladech.</span><span class="sxs-lookup"><span data-stu-id="6967d-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="6967d-120">V následujících příkladech, patří `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="6967d-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="6967d-121">Použití třídy FileStream</span><span class="sxs-lookup"><span data-stu-id="6967d-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="6967d-122">V příkladech v tomto tématu <xref:System.IO.FileStream> třídy, která má možnost, která způsobí, že asynchronní vstupně-výstupních operací na úrovni operačního systému.</span><span class="sxs-lookup"><span data-stu-id="6967d-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="6967d-123">Pomocí této možnosti se můžete vyhnout blokování podproces fondu podprocesů v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="6967d-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="6967d-124">Chcete-li tuto možnost, zadejte `useAsync=true` nebo `options=FileOptions.Asynchronous` argument ve volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6967d-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="6967d-125">Nemůžete použít tuto možnost s <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> Pokud otevřít přímo tak, že zadáte cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="6967d-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="6967d-126">Ale můžete použít tuto možnost, pokud jste zadali, je <xref:System.IO.Stream> , <xref:System.IO.FileStream> třída otevřít.</span><span class="sxs-lookup"><span data-stu-id="6967d-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="6967d-127">Upozorňujeme, že asynchronní volání jsou rychlejší v uživatelském rozhraní aplikace i v případě, že fondu vláken je blokovaný, protože vlákna uživatelského rozhraní není blokován během čekání.</span><span class="sxs-lookup"><span data-stu-id="6967d-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="6967d-128">Zápis textu</span><span class="sxs-lookup"><span data-stu-id="6967d-128">Writing Text</span></span>  
 <span data-ttu-id="6967d-129">Následující příklad zapíše text do souboru.</span><span class="sxs-lookup"><span data-stu-id="6967d-129">The following example writes text to a file.</span></span> <span data-ttu-id="6967d-130">Na každé await prohlášení, metoda okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="6967d-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="6967d-131">Po dokončení soubor vstupně-výstupních operací na příkaz, který následuje příkaz await obnoví metodu.</span><span class="sxs-lookup"><span data-stu-id="6967d-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="6967d-132">Všimněte si, že se modifikátor asynchronní v definici metody, které používají příkaz await.</span><span class="sxs-lookup"><span data-stu-id="6967d-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="6967d-133">V původní příkladu má příkaz `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, což je zmenšení následující dva příkazy:</span><span class="sxs-lookup"><span data-stu-id="6967d-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="6967d-134">První příkaz vrátí úlohu a způsobí, že při zpracování souboru spustit.</span><span class="sxs-lookup"><span data-stu-id="6967d-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="6967d-135">Druhý příkaz se await způsobí, že metoda okamžitě ukončit a vrátit různých úloh.</span><span class="sxs-lookup"><span data-stu-id="6967d-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="6967d-136">Po dokončení zpracování později souborů provádění vrátí příkaz, který následuje await.</span><span class="sxs-lookup"><span data-stu-id="6967d-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="6967d-137">Další informace najdete v tématu [řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="6967d-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="6967d-138">Čtení textu</span><span class="sxs-lookup"><span data-stu-id="6967d-138">Reading Text</span></span>  
 <span data-ttu-id="6967d-139">Následující příklad načte text ze souboru.</span><span class="sxs-lookup"><span data-stu-id="6967d-139">The following example reads text from a file.</span></span> <span data-ttu-id="6967d-140">Text je uložená do vyrovnávací paměti a v takovém případě bude umístěn do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="6967d-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="6967d-141">Na rozdíl od v předchozím příkladu vytvoří vyhodnocení await hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6967d-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="6967d-142"><xref:System.IO.Stream.ReadAsync%2A> Metoda vrátí <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vytváří vyhodnocení await `Int32` hodnotu (`numRead`) po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="6967d-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="6967d-143">Další informace najdete v tématu [asynchronní vrátit typy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6967d-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="6967d-144">Paralelní asynchronní vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="6967d-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="6967d-145">Následující příklad ukazuje paralelní zpracování napsáním 10 textových souborů.</span><span class="sxs-lookup"><span data-stu-id="6967d-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="6967d-146">Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úlohu, která se pak přidá do seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="6967d-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="6967d-147">`Await Task.WhenAll(tasks)` Příkaz ukončí metodu a obnoví v rámci metody při zpracování souboru dokončete pro všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="6967d-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="6967d-148">Příklad zavření všech <xref:System.IO.FileStream> instancí v `Finally` blokovat po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="6967d-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="6967d-149">Pokud každý `FileStream` místo toho byl vytvořen v `Imports` příkaz, `FileStream` může probíhat za před dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="6967d-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="6967d-150">Všimněte si, že žádné zvýšení výkonu je téměř úplně z paralelní zpracování a není asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="6967d-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="6967d-151">Výhody asynchrony jsou ho nebude vytížit více vláken a že není vytížit vlákna uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6967d-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="6967d-152">Při použití <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> metod, můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít se zrušit operaci střední datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6967d-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="6967d-153">Další informace najdete v tématu [Fine-Tuning vaše asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="6967d-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6967d-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="6967d-154">See Also</span></span>  
 [<span data-ttu-id="6967d-155">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6967d-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="6967d-156">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6967d-156">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="6967d-157">Řízení toku v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6967d-157">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
