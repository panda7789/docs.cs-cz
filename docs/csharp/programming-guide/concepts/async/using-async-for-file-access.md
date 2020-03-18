---
title: Použití aplikace Async pro přístup k souborům (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: e6b0370049d9b9315de6a72d0e84c080aac12481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595544"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="80de1-102">Použití aplikace Async pro přístup k souborům (C#)</span><span class="sxs-lookup"><span data-stu-id="80de1-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="80de1-103">Funkci asynchronní můžete použít pro přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="80de1-103">You can use the async feature to access files.</span></span> <span data-ttu-id="80de1-104">Pomocí funkce async můžete volat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu mezi více metod nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="80de1-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="80de1-105">Chcete-li synchronní kód asynchronní, stačí volat asynchronní metodu namísto synchronní metody a přidat několik klíčových slov do kódu.</span><span class="sxs-lookup"><span data-stu-id="80de1-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="80de1-106">Můžete zvážit následující důvody pro přidání asynchrony do volání přístupu k souborům:</span><span class="sxs-lookup"><span data-stu-id="80de1-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="80de1-107">Asynchrony umožňuje aplikace uživatelského rozhraní citlivější, protože vlákno uživatelského rozhraní, které spustí operaci může provádět jinou práci.</span><span class="sxs-lookup"><span data-stu-id="80de1-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="80de1-108">Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), uživatelské rozhraní může zamrznout, dokud není dokončeno vstupně-v., a vlákno uživatelského rozhraní může znovu zpracovat vstup klávesnice a myši a další události.</span><span class="sxs-lookup"><span data-stu-id="80de1-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="80de1-109">Asynchrony zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací snížením potřeby podprocesů.</span><span class="sxs-lookup"><span data-stu-id="80de1-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="80de1-110">Pokud aplikace používá vyhrazené vlákno na odpověď a tisíce požadavků jsou zpracovávány současně, jsou potřeba tisíce podprocesů.</span><span class="sxs-lookup"><span data-stu-id="80de1-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="80de1-111">Asynchronní operace často není nutné použít vlákno během čekání.</span><span class="sxs-lookup"><span data-stu-id="80de1-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="80de1-112">Na konci krátce použijí existující vlákno pro dokončení vstupně-doo.</span><span class="sxs-lookup"><span data-stu-id="80de1-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="80de1-113">Latence operace přístupu k souborům může být velmi nízká za aktuálních podmínek, ale latence může výrazně zvýšit v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="80de1-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="80de1-114">Soubor může být například přesunut na server, který je po celém světě.</span><span class="sxs-lookup"><span data-stu-id="80de1-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="80de1-115">Přidaná režie použití funkce Async je malá.</span><span class="sxs-lookup"><span data-stu-id="80de1-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="80de1-116">Asynchronní úlohy lze snadno spustit paralelně.</span><span class="sxs-lookup"><span data-stu-id="80de1-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="80de1-117">Spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="80de1-117">Running the Examples</span></span>  
 <span data-ttu-id="80de1-118">Chcete-li spustit příklady v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **aplikaci Windows Forms** a potom přidat **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="80de1-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="80de1-119">V `Click` události tlačítka přidejte volání k první metodě v každém příkladu.</span><span class="sxs-lookup"><span data-stu-id="80de1-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="80de1-120">V následujících příkladech uveďte následující `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="80de1-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="80de1-121">Použití třídy FileStream</span><span class="sxs-lookup"><span data-stu-id="80de1-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="80de1-122">Příklady v tomto tématu používají třídu, <xref:System.IO.FileStream> která má možnost, která způsobí, že asynchronní vstupně-v.,O dojít na úrovni operačního systému.</span><span class="sxs-lookup"><span data-stu-id="80de1-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="80de1-123">Pomocí této možnosti se můžete v mnoha případech vyhnout blokování vlákna ThreadPool.</span><span class="sxs-lookup"><span data-stu-id="80de1-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="80de1-124">Chcete-li povolit tuto `useAsync=true` `options=FileOptions.Asynchronous` možnost, zadejte argument nebo ve volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="80de1-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="80de1-125">Tuto možnost nelze použít <xref:System.IO.StreamReader> s <xref:System.IO.StreamWriter> a pokud je otevřete přímo zadáním cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="80de1-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="80de1-126">Tuto možnost však můžete použít, <xref:System.IO.Stream> pokud <xref:System.IO.FileStream> jim poskytnete a že třída otevřena.</span><span class="sxs-lookup"><span data-stu-id="80de1-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="80de1-127">Všimněte si, že asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že vlákno ThreadPool je blokován, protože vlákno uživatelského rozhraní není blokován během čekání.</span><span class="sxs-lookup"><span data-stu-id="80de1-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="80de1-128">Psaní textu</span><span class="sxs-lookup"><span data-stu-id="80de1-128">Writing Text</span></span>  
 <span data-ttu-id="80de1-129">Následující příklad zapisuje text do souboru.</span><span class="sxs-lookup"><span data-stu-id="80de1-129">The following example writes text to a file.</span></span> <span data-ttu-id="80de1-130">Na každém příkazu await metoda okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="80de1-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="80de1-131">Po dokončení vstupně-videa souboru metoda pokračuje na příkaz, který následuje await prohlášení.</span><span class="sxs-lookup"><span data-stu-id="80de1-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="80de1-132">Všimněte si, že asynchronní modifikátor je v definici metod, které používají příkaz await.</span><span class="sxs-lookup"><span data-stu-id="80de1-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="80de1-133">Původní příklad má `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`prohlášení , což je kontrakce následujících dvou prohlášení:</span><span class="sxs-lookup"><span data-stu-id="80de1-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="80de1-134">První příkaz vrátí úlohu a způsobí spuštění zpracování souboru.</span><span class="sxs-lookup"><span data-stu-id="80de1-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="80de1-135">Druhý příkaz s await způsobí, že metoda okamžitě ukončit a vrátit jiný úkol.</span><span class="sxs-lookup"><span data-stu-id="80de1-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="80de1-136">Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za await.</span><span class="sxs-lookup"><span data-stu-id="80de1-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="80de1-137">Další informace naleznete [v tématu Řízení toku v asynchronních programech (C#)](./control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="80de1-137">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="80de1-138">Čtení textu</span><span class="sxs-lookup"><span data-stu-id="80de1-138">Reading Text</span></span>  
 <span data-ttu-id="80de1-139">Následující příklad přečte text ze souboru.</span><span class="sxs-lookup"><span data-stu-id="80de1-139">The following example reads text from a file.</span></span> <span data-ttu-id="80de1-140">Text je uložen do vyrovnávací paměti a <xref:System.Text.StringBuilder>v tomto případě umístěn do .</span><span class="sxs-lookup"><span data-stu-id="80de1-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="80de1-141">Na rozdíl od předchozího příkladu hodnocení await vytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="80de1-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="80de1-142">Metoda <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.Tasks.Task> \< <xref:System.Int32> vrátí>, takže vyhodnocení await vytvoří `Int32` hodnotu`numRead`( ) po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="80de1-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="80de1-143">Další informace naleznete [v tématu Asynchronní návratové typy (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="80de1-143">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="80de1-144">Paralelní asynchronní vstupně-nosné</span><span class="sxs-lookup"><span data-stu-id="80de1-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="80de1-145">Následující příklad ukazuje paralelní zpracování zápisem 10 textových souborů.</span><span class="sxs-lookup"><span data-stu-id="80de1-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="80de1-146">Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úkol, který je pak přidán do seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="80de1-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="80de1-147">Příkaz `await Task.WhenAll(tasks);` ukončí metodu a pokračuje v rámci metody po dokončení zpracování souboru pro všechny úkoly.</span><span class="sxs-lookup"><span data-stu-id="80de1-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="80de1-148">Příklad zavře všechny <xref:System.IO.FileStream> instance v `finally` bloku po dokončení úkolů.</span><span class="sxs-lookup"><span data-stu-id="80de1-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="80de1-149">Pokud `FileStream` byl vytvořen v `using` příkazu, `FileStream` může být uvolněn před dokončením úkolu.</span><span class="sxs-lookup"><span data-stu-id="80de1-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="80de1-150">Všimněte si, že jakékoli zvýšení výkonu je téměř výhradně z paralelní zpracování a nikoli asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="80de1-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="80de1-151">Výhody asynchrony jsou, že neváže více vláken a že neváže vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="80de1-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="80de1-152">Při použití <xref:System.IO.Stream.WriteAsync%2A> <xref:System.IO.Stream.ReadAsync%2A> metody a můžete <xref:System.Threading.CancellationToken>zadat , který můžete použít ke zrušení operace uprostřed datového proudu.</span><span class="sxs-lookup"><span data-stu-id="80de1-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="80de1-153">Další informace naleznete v [tématu Jemné doladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="80de1-153">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80de1-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="80de1-154">See also</span></span>

- [<span data-ttu-id="80de1-155">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="80de1-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="80de1-156">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="80de1-156">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="80de1-157">Tok řízení v asynchronních programech (C#)</span><span class="sxs-lookup"><span data-stu-id="80de1-157">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
