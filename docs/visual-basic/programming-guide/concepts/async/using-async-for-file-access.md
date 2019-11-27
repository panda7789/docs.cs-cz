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
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="79038-102">Použití Async pro přístup k souborům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79038-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="79038-103">K přístupu k souborům můžete použít funkci Async.</span><span class="sxs-lookup"><span data-stu-id="79038-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="79038-104">Pomocí asynchronní funkce můžete zavolat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu napříč více metodami nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="79038-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="79038-105">Chcete-li synchronní asynchronní kód, stačí zavolat asynchronní metodu namísto synchronní metody a přidat k kódu několik klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="79038-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="79038-106">Při přidávání asynchronii do volání přístupu k souborům můžete zvážit následující důvody:</span><span class="sxs-lookup"><span data-stu-id="79038-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="79038-107">Asynchronii umožňuje aplikacím uživatelského rozhraní lépe reagovat, protože vlákno uživatelského rozhraní, které spouští operaci, může provádět i jinou práci.</span><span class="sxs-lookup"><span data-stu-id="79038-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="79038-108">Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), může uživatelské rozhraní zablokovat až do dokončení vstupně-výstupních operací a vlákno uživatelského rozhraní může znovu zpracovat vstupy klávesnice a myši a další události.</span><span class="sxs-lookup"><span data-stu-id="79038-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="79038-109">Asynchronii zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací tím, že snižuje nutnost vláken.</span><span class="sxs-lookup"><span data-stu-id="79038-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="79038-110">Pokud aplikace používá vyhrazené vlákno na reakci a tisíce požadavků jsou zpracovávány současně, je zapotřebí tisíce vláken.</span><span class="sxs-lookup"><span data-stu-id="79038-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="79038-111">Asynchronní operace často nepotřebují použít vlákno během čekání.</span><span class="sxs-lookup"><span data-stu-id="79038-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="79038-112">Na konci se krátce používají existující vlákna dokončení v/v.</span><span class="sxs-lookup"><span data-stu-id="79038-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="79038-113">Latence operace přístupu k souboru může být v rámci současných podmínek velmi nízká, ale latence může výrazně zvýšit i v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="79038-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="79038-114">Soubor může být například přesunut na server, který je na celém světě.</span><span class="sxs-lookup"><span data-stu-id="79038-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="79038-115">Přidaná režie použití asynchronní funkce je malá.</span><span class="sxs-lookup"><span data-stu-id="79038-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="79038-116">Asynchronní úlohy lze snadno spustit paralelně.</span><span class="sxs-lookup"><span data-stu-id="79038-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="79038-117">Spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="79038-117">Running the Examples</span></span>  
 <span data-ttu-id="79038-118">Chcete-li spustit příklady v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **aplikaci model Windows Forms** a pak přidat **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="79038-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="79038-119">V události `Click` tlačítka přidejte do prvního příkladu volání první metody.</span><span class="sxs-lookup"><span data-stu-id="79038-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="79038-120">V následujících příkladech zahrňte následující příkazy `Imports`.</span><span class="sxs-lookup"><span data-stu-id="79038-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="79038-121">Použití třídy FileStream</span><span class="sxs-lookup"><span data-stu-id="79038-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="79038-122">Příklady v tomto tématu používají třídu <xref:System.IO.FileStream>, která má možnost, která způsobí, že asynchronní vstupně-výstupní operace proběhne na úrovni operačního systému.</span><span class="sxs-lookup"><span data-stu-id="79038-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="79038-123">Pomocí této možnosti se můžete vyhnout blokování vlákna fondu vláken v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="79038-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="79038-124">Tuto možnost povolíte zadáním argumentu `useAsync=true` nebo `options=FileOptions.Asynchronous` ve volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="79038-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="79038-125">Tuto možnost nelze použít u <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter>, pokud je otevřete přímo zadáním cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="79038-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="79038-126">Tuto možnost však můžete použít, pokud jim poskytnete <xref:System.IO.Stream>, že se třída <xref:System.IO.FileStream> otevřela.</span><span class="sxs-lookup"><span data-stu-id="79038-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="79038-127">Všimněte si, že asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že je vlákno nevláken blokované, protože během čekání není zablokované vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="79038-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="79038-128">Zápis textu</span><span class="sxs-lookup"><span data-stu-id="79038-128">Writing Text</span></span>  
 <span data-ttu-id="79038-129">Následující příklad zapisuje text do souboru.</span><span class="sxs-lookup"><span data-stu-id="79038-129">The following example writes text to a file.</span></span> <span data-ttu-id="79038-130">V každém příkazu await se metoda okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="79038-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="79038-131">Po dokončení vstupně-výstupních operací se metoda obnoví v příkazu, který následuje po příkazu await.</span><span class="sxs-lookup"><span data-stu-id="79038-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="79038-132">Všimněte si, že modifikátor Async je v definici metod, které používají příkaz await.</span><span class="sxs-lookup"><span data-stu-id="79038-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="79038-133">Původní příklad obsahuje příkaz `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, což je kontrakt následujících dvou příkazů:</span><span class="sxs-lookup"><span data-stu-id="79038-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="79038-134">První příkaz vrátí úlohu a způsobí, že se zpracování souboru spustí.</span><span class="sxs-lookup"><span data-stu-id="79038-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="79038-135">Druhý příkaz s operátorem await způsobí, že metoda okamžitě ukončí a vrátí jiný úkol.</span><span class="sxs-lookup"><span data-stu-id="79038-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="79038-136">Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za operátorem await.</span><span class="sxs-lookup"><span data-stu-id="79038-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="79038-137">Další informace najdete v tématu [řízení toku v asynchronních programech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="79038-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="79038-138">Čtení textu</span><span class="sxs-lookup"><span data-stu-id="79038-138">Reading Text</span></span>  
 <span data-ttu-id="79038-139">Následující příklad přečte text ze souboru.</span><span class="sxs-lookup"><span data-stu-id="79038-139">The following example reads text from a file.</span></span> <span data-ttu-id="79038-140">Text je uložen do vyrovnávací paměti a v tomto případě je umístěn do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="79038-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="79038-141">Na rozdíl od předchozího příkladu vyhodnocení await vytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="79038-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="79038-142">Metoda <xref:System.IO.Stream.ReadAsync%2A> vrátí <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, takže hodnocení Await vytvoří `Int32` hodnotu (`numRead`) po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="79038-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="79038-143">Další informace naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="79038-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="79038-144">Paralelní asynchronní vstupně-výstupní operace</span><span class="sxs-lookup"><span data-stu-id="79038-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="79038-145">Následující příklad znázorňuje paralelní zpracování zápisem 10 textových souborů.</span><span class="sxs-lookup"><span data-stu-id="79038-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="79038-146">Pro každý soubor metoda <xref:System.IO.Stream.WriteAsync%2A> vrátí úkol, který je poté přidán do seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="79038-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="79038-147">Příkaz `Await Task.WhenAll(tasks)` ukončí metodu a pokračuje v rámci metody, když je zpracování souborů dokončeno pro všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="79038-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="79038-148">Tento příklad uzavře všechny instance <xref:System.IO.FileStream> v bloku `Finally` po dokončení úkolů.</span><span class="sxs-lookup"><span data-stu-id="79038-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="79038-149">Pokud byl každý `FileStream` vytvořen v příkazu `Imports`, `FileStream` může být odstraněn před dokončením úkolu.</span><span class="sxs-lookup"><span data-stu-id="79038-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="79038-150">Všimněte si, že veškeré zvýšení výkonu je prakticky zcela úplné od paralelního zpracování, nikoli z asynchronního zpracování.</span><span class="sxs-lookup"><span data-stu-id="79038-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="79038-151">Výhody asynchronii jsou, že neodkazují na více vláken a že nevyužívají vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="79038-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="79038-152">Při použití metod <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít k zrušení operace střední-Stream.</span><span class="sxs-lookup"><span data-stu-id="79038-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="79038-153">Další informace najdete v tématu [jemné ladění asynchronní aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="79038-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79038-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79038-154">See also</span></span>

- [<span data-ttu-id="79038-155">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79038-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="79038-156">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79038-156">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="79038-157">Řízení toku v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79038-157">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
