---
title: Použití Async pro přístup k souborůmC#()
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 6ca47157575ef4569a43f334dae4f99a1986a7ce
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330947"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="c3d0d-102">Použití Async pro přístup k souborůmC#()</span><span class="sxs-lookup"><span data-stu-id="c3d0d-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="c3d0d-103">K přístupu k souborům můžete použít funkci Async.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-103">You can use the async feature to access files.</span></span> <span data-ttu-id="c3d0d-104">Pomocí asynchronní funkce můžete zavolat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu napříč více metodami nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="c3d0d-105">Chcete-li synchronní asynchronní kód, stačí zavolat asynchronní metodu namísto synchronní metody a přidat k kódu několik klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="c3d0d-106">Při přidávání asynchronii do volání přístupu k souborům můžete zvážit následující důvody:</span><span class="sxs-lookup"><span data-stu-id="c3d0d-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="c3d0d-107">Asynchronii umožňuje aplikacím uživatelského rozhraní lépe reagovat, protože vlákno uživatelského rozhraní, které spouští operaci, může provádět i jinou práci.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="c3d0d-108">Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), může uživatelské rozhraní zablokovat až do dokončení vstupně-výstupních operací a vlákno uživatelského rozhraní může znovu zpracovat vstupy klávesnice a myši a další události.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="c3d0d-109">Asynchronii zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací tím, že snižuje nutnost vláken.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="c3d0d-110">Pokud aplikace používá vyhrazené vlákno na reakci a tisíce požadavků jsou zpracovávány současně, je zapotřebí tisíce vláken.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="c3d0d-111">Asynchronní operace často nepotřebují použít vlákno během čekání.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="c3d0d-112">Na konci se krátce používají existující vlákna dokončení v/v.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="c3d0d-113">Latence operace přístupu k souboru může být v rámci současných podmínek velmi nízká, ale latence může výrazně zvýšit i v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="c3d0d-114">Soubor může být například přesunut na server, který je na celém světě.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="c3d0d-115">Přidaná režie použití asynchronní funkce je malá.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="c3d0d-116">Asynchronní úlohy lze snadno spustit paralelně.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="c3d0d-117">Spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="c3d0d-117">Running the Examples</span></span>  
 <span data-ttu-id="c3d0d-118">Chcete-li spustit příklady v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **aplikaci model Windows Forms** a pak přidat **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="c3d0d-119">V `Click` události tlačítka přidejte do prvního příkladu volání první metody.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="c3d0d-120">V následujících příkladech zahrňte následující `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="c3d0d-121">Použití třídy FileStream</span><span class="sxs-lookup"><span data-stu-id="c3d0d-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="c3d0d-122">Příklady v tomto tématu používají <xref:System.IO.FileStream> třídu, která má možnost, která způsobuje asynchronní vstupně-výstupní operace na úrovni operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="c3d0d-123">Pomocí této možnosti se můžete vyhnout blokování vlákna fondu vláken v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="c3d0d-124">Chcete-li povolit tuto možnost, zadejte `useAsync=true` argument `options=FileOptions.Asynchronous` nebo ve volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="c3d0d-125">Tuto možnost nemůžete použít <xref:System.IO.StreamReader> s <xref:System.IO.StreamWriter> a, pokud je otevřete přímo zadáním cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="c3d0d-126">Tuto možnost však můžete použít <xref:System.IO.Stream> <xref:System.IO.FileStream> , pokud jim poskytnete třídu, kterou otevřela.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="c3d0d-127">Všimněte si, že asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že je vlákno nevláken blokované, protože během čekání není zablokované vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="c3d0d-128">Zápis textu</span><span class="sxs-lookup"><span data-stu-id="c3d0d-128">Writing Text</span></span>  
 <span data-ttu-id="c3d0d-129">Následující příklad zapisuje text do souboru.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-129">The following example writes text to a file.</span></span> <span data-ttu-id="c3d0d-130">V každém příkazu await se metoda okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="c3d0d-131">Po dokončení vstupně-výstupních operací se metoda obnoví v příkazu, který následuje po příkazu await.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="c3d0d-132">Všimněte si, že modifikátor Async je v definici metod, které používají příkaz await.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="c3d0d-133">Původní příklad obsahuje příkaz `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, který je kontraktem následujících dvou příkazů:</span><span class="sxs-lookup"><span data-stu-id="c3d0d-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="c3d0d-134">První příkaz vrátí úlohu a způsobí, že se zpracování souboru spustí.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="c3d0d-135">Druhý příkaz s operátorem await způsobí, že metoda okamžitě ukončí a vrátí jiný úkol.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="c3d0d-136">Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za operátorem await.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="c3d0d-137">Další informace najdete v tématu [tok řízení v části Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="c3d0d-137">For more information, see  [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="c3d0d-138">Čtení textu</span><span class="sxs-lookup"><span data-stu-id="c3d0d-138">Reading Text</span></span>  
 <span data-ttu-id="c3d0d-139">Následující příklad přečte text ze souboru.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-139">The following example reads text from a file.</span></span> <span data-ttu-id="c3d0d-140">Text je uložen do vyrovnávací paměti a v tomto případě je umístěn do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="c3d0d-141">Na rozdíl od předchozího příkladu vyhodnocení await vytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="c3d0d-142">`Int32` `numRead`Metoda <xref:System.IO.Stream.ReadAsync%2A> vrací>,takže<xref:System.Threading.Tasks.Task>vyhodnocení metody await vytvoří hodnotu () po dokončení operace. \< <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="c3d0d-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="c3d0d-143">Další informace naleznete v tématu [Async Return TypesC#()](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="c3d0d-143">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="c3d0d-144">Paralelní asynchronní vstupně-výstupní operace</span><span class="sxs-lookup"><span data-stu-id="c3d0d-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="c3d0d-145">Následující příklad znázorňuje paralelní zpracování zápisem 10 textových souborů.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="c3d0d-146">Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úkol, který je poté přidán do seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="c3d0d-147">`await Task.WhenAll(tasks);` Příkaz ukončí metodu a pokračuje v rámci metody, když je zpracování souborů dokončeno pro všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="c3d0d-148">Příklad zavře všechny <xref:System.IO.FileStream> instance `finally` v bloku po dokončení úkolů.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="c3d0d-149">Pokud byl `FileStream` každý z nich vytvořen `using` v příkazu, `FileStream` může být odstraněn před dokončením úkolu.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="c3d0d-150">Všimněte si, že veškeré zvýšení výkonu je prakticky zcela úplné od paralelního zpracování, nikoli z asynchronního zpracování.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="c3d0d-151">Výhody asynchronii jsou, že neodkazují na více vláken a že nevyužívají vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="c3d0d-152">Při použití <xref:System.IO.Stream.WriteAsync%2A> metod a <xref:System.IO.Stream.ReadAsync%2A> můžete zadat <xref:System.Threading.CancellationToken>, které můžete použít k zrušení operace střední-Stream.</span><span class="sxs-lookup"><span data-stu-id="c3d0d-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="c3d0d-153">Další informace najdete v tématu [jemné vyladění asynchronní aplikace (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="c3d0d-153">For more information, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d0d-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3d0d-154">See also</span></span>

- [<span data-ttu-id="c3d0d-155">Asynchronní programování s modifikátorem Async aC#operátoru Await ()</span><span class="sxs-lookup"><span data-stu-id="c3d0d-155">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="c3d0d-156">Asynchronní návratové typyC#()</span><span class="sxs-lookup"><span data-stu-id="c3d0d-156">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="c3d0d-157">Řízení toku v asynchronních programechC#()</span><span class="sxs-lookup"><span data-stu-id="c3d0d-157">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
