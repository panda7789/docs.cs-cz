---
title: Použití modifikátoru Async pro přístup k souborům (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 083a9113fc75c9e18646953a144b9e3d1bfd90ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328286"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="6467e-102">Použití modifikátoru Async pro přístup k souborům (C#)</span><span class="sxs-lookup"><span data-stu-id="6467e-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="6467e-103">Můžete použít funkci async pro přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="6467e-103">You can use the async feature to access files.</span></span> <span data-ttu-id="6467e-104">Pomocí funkce asynchronní můžete volat do asynchronní metody bez použití zpětná volání nebo rozdělení kódu mezi více metod nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="6467e-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="6467e-105">Chcete-li synchronní kód asynchronní, právě volání asynchronní metody místo synchronní metody a přidejte několik klíčových slov do kódu.</span><span class="sxs-lookup"><span data-stu-id="6467e-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="6467e-106">Můžete zvážit z následujících důvodů pro přidání asynchrony do souboru přístup volání:</span><span class="sxs-lookup"><span data-stu-id="6467e-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="6467e-107">Asynchrony zadává uživatelského rozhraní aplikace rychlejšího protože vlákna uživatelského rozhraní, která spustí operace můžete provádět jinou práci.</span><span class="sxs-lookup"><span data-stu-id="6467e-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="6467e-108">Pokud vlákna uživatelského rozhraní musí být spuštěn kód která trvá dlouhou dobu (například více než 50 milisekund), rozhraní může zmrazit až po dokončení vstupy/výstupy a vlákna uživatelského rozhraní můžete znovu zpracovat klávesnice a myši vstupní a dalších událostí.</span><span class="sxs-lookup"><span data-stu-id="6467e-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="6467e-109">Asynchrony zlepšuje škálovatelnost technologie ASP.NET a dalších serverových aplikací, protože snižuje potřebu vláken.</span><span class="sxs-lookup"><span data-stu-id="6467e-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="6467e-110">Pokud aplikace používá vyhrazený vlákno na jeden odpovědi a tisíce požadavky jsou právě zpracovávány současně, je potřeba tisíce vláken.</span><span class="sxs-lookup"><span data-stu-id="6467e-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="6467e-111">Asynchronní operace často není třeba použít během čekání vlákno.</span><span class="sxs-lookup"><span data-stu-id="6467e-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="6467e-112">Na konci stručně používají existující vlákno dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="6467e-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="6467e-113">Latence operace přístupu k souboru může být velmi nízkou v aktuální podmínkách, ale latence může výrazně zvýšit v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="6467e-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="6467e-114">Například může přesunout soubor na server, který je po celém světě.</span><span class="sxs-lookup"><span data-stu-id="6467e-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="6467e-115">Přidaném režijní náklady na použití funkce asynchronní je malá.</span><span class="sxs-lookup"><span data-stu-id="6467e-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="6467e-116">Asynchronní úlohy můžete spustit snadno paralelně.</span><span class="sxs-lookup"><span data-stu-id="6467e-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="6467e-117">Spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="6467e-117">Running the Examples</span></span>  
 <span data-ttu-id="6467e-118">Pokud chcete spustit v příkladech v tomto tématu, můžete vytvořit **aplikaci WPF** nebo **formulářové aplikace Windows** a poté přidejte **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="6467e-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="6467e-119">U tlačítka `Click` událostí, přidejte volání do první metodu v obou příkladech.</span><span class="sxs-lookup"><span data-stu-id="6467e-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="6467e-120">V následujících příkladech, patří `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="6467e-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="6467e-121">Použití třídy FileStream</span><span class="sxs-lookup"><span data-stu-id="6467e-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="6467e-122">V příkladech v tomto tématu <xref:System.IO.FileStream> třídy, která má možnost, která způsobí, že asynchronní vstupně-výstupních operací na úrovni operačního systému.</span><span class="sxs-lookup"><span data-stu-id="6467e-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="6467e-123">Pomocí této možnosti se můžete vyhnout blokování podproces fondu podprocesů v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="6467e-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="6467e-124">Chcete-li tuto možnost, zadejte `useAsync=true` nebo `options=FileOptions.Asynchronous` argument ve volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6467e-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="6467e-125">Nemůžete použít tuto možnost s <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> Pokud otevřít přímo tak, že zadáte cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="6467e-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="6467e-126">Ale můžete použít tuto možnost, pokud jste zadali, je <xref:System.IO.Stream> , <xref:System.IO.FileStream> třída otevřít.</span><span class="sxs-lookup"><span data-stu-id="6467e-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="6467e-127">Upozorňujeme, že asynchronní volání jsou rychlejší v uživatelském rozhraní aplikace i v případě, že fondu vláken je blokovaný, protože vlákna uživatelského rozhraní není blokován během čekání.</span><span class="sxs-lookup"><span data-stu-id="6467e-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="6467e-128">Zápis textu</span><span class="sxs-lookup"><span data-stu-id="6467e-128">Writing Text</span></span>  
 <span data-ttu-id="6467e-129">Následující příklad zapíše text do souboru.</span><span class="sxs-lookup"><span data-stu-id="6467e-129">The following example writes text to a file.</span></span> <span data-ttu-id="6467e-130">Na každé await prohlášení, metoda okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="6467e-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="6467e-131">Po dokončení soubor vstupně-výstupních operací na příkaz, který následuje příkaz await obnoví metodu.</span><span class="sxs-lookup"><span data-stu-id="6467e-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="6467e-132">Všimněte si, že se modifikátor asynchronní v definici metody, které používají příkaz await.</span><span class="sxs-lookup"><span data-stu-id="6467e-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async void ProcessWrite()  
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
  
 <span data-ttu-id="6467e-133">V původní příkladu má příkaz `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, což je zmenšení následující dva příkazy:</span><span class="sxs-lookup"><span data-stu-id="6467e-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="6467e-134">První příkaz vrátí úlohu a způsobí, že při zpracování souboru spustit.</span><span class="sxs-lookup"><span data-stu-id="6467e-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="6467e-135">Druhý příkaz se await způsobí, že metoda okamžitě ukončit a vrátit různých úloh.</span><span class="sxs-lookup"><span data-stu-id="6467e-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="6467e-136">Po dokončení zpracování později souborů provádění vrátí příkaz, který následuje await.</span><span class="sxs-lookup"><span data-stu-id="6467e-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="6467e-137">Další informace najdete v tématu [řízení toku v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="6467e-137">For more information, see  [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="6467e-138">Čtení textu</span><span class="sxs-lookup"><span data-stu-id="6467e-138">Reading Text</span></span>  
 <span data-ttu-id="6467e-139">Následující příklad načte text ze souboru.</span><span class="sxs-lookup"><span data-stu-id="6467e-139">The following example reads text from a file.</span></span> <span data-ttu-id="6467e-140">Text je uložená do vyrovnávací paměti a v takovém případě bude umístěn do <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="6467e-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="6467e-141">Na rozdíl od v předchozím příkladu vytvoří vyhodnocení await hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6467e-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="6467e-142"><xref:System.IO.Stream.ReadAsync%2A> Metoda vrátí <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, takže vytváří vyhodnocení await `Int32` hodnotu (`numRead`) po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="6467e-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="6467e-143">Další informace najdete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6467e-143">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
```csharp  
public async void ProcessRead()  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="6467e-144">Paralelní asynchronní vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="6467e-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="6467e-145">Následující příklad ukazuje paralelní zpracování napsáním 10 textových souborů.</span><span class="sxs-lookup"><span data-stu-id="6467e-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="6467e-146">Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> metoda vrátí úlohu, která se pak přidá do seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="6467e-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="6467e-147">`await Task.WhenAll(tasks);` Příkaz ukončí metodu a obnoví v rámci metody při zpracování souboru dokončete pro všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="6467e-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="6467e-148">Příklad zavření všech <xref:System.IO.FileStream> instancí v `finally` blokovat po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="6467e-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="6467e-149">Pokud každý `FileStream` místo toho byl vytvořen v `using` příkaz, `FileStream` může probíhat za před dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="6467e-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="6467e-150">Všimněte si, že žádné zvýšení výkonu je téměř úplně z paralelní zpracování a není asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="6467e-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="6467e-151">Výhody asynchrony jsou ho nebude vytížit více vláken a že není vytížit vlákna uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6467e-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async void ProcessWriteMult()  
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
  
 <span data-ttu-id="6467e-152">Při použití <xref:System.IO.Stream.WriteAsync%2A> a <xref:System.IO.Stream.ReadAsync%2A> metod, můžete zadat <xref:System.Threading.CancellationToken>, který můžete použít se zrušit operaci střední datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6467e-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="6467e-153">Další informace najdete v tématu [Fine-Tuning vaše aplikace Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) a [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="6467e-153">For more information, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6467e-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="6467e-154">See Also</span></span>  
 [<span data-ttu-id="6467e-155">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="6467e-155">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="6467e-156">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="6467e-156">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="6467e-157">Řízení toku v asynchronních programech (C#)</span><span class="sxs-lookup"><span data-stu-id="6467e-157">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
