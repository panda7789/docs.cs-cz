---
title: 'Postupy: použití fondu vláken (C#)'
ms.date: 07/20/2015
ms.assetid: 210a9235-83a6-420b-af52-2d6a58e5133f
ms.openlocfilehash: c89093bcff82715482b2ddb822916cfa5ff8ed72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340473"
---
# <a name="how-to-use-a-thread-pool-c"></a><span data-ttu-id="f0b54-102">Postupy: použití fondu vláken (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b54-102">How to: Use a Thread Pool (C#)</span></span>
<span data-ttu-id="f0b54-103">*Sdružování vláken* je forma více vláken v úkoly, které jsou přidány do fronty a automaticky spuštěn při vytvoření vláken.</span><span class="sxs-lookup"><span data-stu-id="f0b54-103">*Thread pooling* is a form of multithreading in which tasks are added to a queue and automatically started when threads are created.</span></span> <span data-ttu-id="f0b54-104">Další informace najdete v tématu [vláken sdružování (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="f0b54-104">For more information, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md).</span></span>  
  
 <span data-ttu-id="f0b54-105">Následující příklad používá k výpočtu fondu vláken rozhraní .NET Framework `Fibonacci` výsledek deset čísel až 20, 40.</span><span class="sxs-lookup"><span data-stu-id="f0b54-105">The following example uses the .NET Framework thread pool to calculate the `Fibonacci` result for ten numbers between 20 and 40.</span></span> <span data-ttu-id="f0b54-106">Každý `Fibonacci` výsledek je reprezentována `Fibonacci` třídy, která poskytuje metodu s názvem `ThreadPoolCallback` který provede výpočet.</span><span class="sxs-lookup"><span data-stu-id="f0b54-106">Each `Fibonacci` result is represented by the `Fibonacci` class, which provides a method named `ThreadPoolCallback` that performs the calculation.</span></span> <span data-ttu-id="f0b54-107">Objekt, který reprezentuje všechny `Fibonacci` hodnota je vytvořena a `ThreadPoolCallback` předaný metoda <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, které přiřadí k dispozici přístup z více vláken ve fondu se mají spustit metodu.</span><span class="sxs-lookup"><span data-stu-id="f0b54-107">An object that represents each `Fibonacci` value is created, and the `ThreadPoolCallback` method is passed to <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, which assigns an available thread in the pool to execute the method.</span></span>  
  
 <span data-ttu-id="f0b54-108">Protože každý `Fibonacci` objektu je uveden polovičním náhodná hodnota k výpočtu a protože každé vlákno bude neslučitelných pro využití procesoru, nemůže vědět předem jak dlouho trvat pro všechny deset výsledky se vypočítá.</span><span class="sxs-lookup"><span data-stu-id="f0b54-108">Because each `Fibonacci` object is given a semi-random value to compute, and because each thread will be competing for processor time, you cannot know in advance how long it will take for all ten results to be calculated.</span></span> <span data-ttu-id="f0b54-109">To je důvod, proč každý `Fibonacci` objekt předá instance <xref:System.Threading.ManualResetEvent> třída během vytváření.</span><span class="sxs-lookup"><span data-stu-id="f0b54-109">That is why each `Fibonacci` object is passed an instance of the <xref:System.Threading.ManualResetEvent> class during construction.</span></span> <span data-ttu-id="f0b54-110">Každý objekt signály objekt zadané události při jeho bude dokončen výpočet, který umožňuje primární vlákno k provádění bloku s <xref:System.Threading.WaitHandle.WaitAll%2A> až deset všechny `Fibonacci` objekty vypočítali výsledku.</span><span class="sxs-lookup"><span data-stu-id="f0b54-110">Each object signals the provided event object when its calculation is complete, which allows the primary thread to block execution with <xref:System.Threading.WaitHandle.WaitAll%2A> until all ten `Fibonacci` objects have calculated a result.</span></span> <span data-ttu-id="f0b54-111">`Main` Metoda pak zobrazí každý `Fibonacci` výsledek.</span><span class="sxs-lookup"><span data-stu-id="f0b54-111">The `Main` method then displays each `Fibonacci` result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0b54-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0b54-112">Example</span></span>  
  
```csharp  
using System;  
using System.Threading;  
  
public class Fibonacci  
{  
    private int _n;  
    private int _fibOfN;  
    private ManualResetEvent _doneEvent;  
  
    public int N { get { return _n; } }  
    public int FibOfN { get { return _fibOfN; } }  
  
    // Constructor.  
    public Fibonacci(int n, ManualResetEvent doneEvent)  
    {  
        _n = n;  
        _doneEvent = doneEvent;  
    }  
  
    // Wrapper method for use with thread pool.  
    public void ThreadPoolCallback(Object threadContext)  
    {  
        int threadIndex = (int)threadContext;  
        Console.WriteLine("thread {0} started...", threadIndex);  
        _fibOfN = Calculate(_n);  
        Console.WriteLine("thread {0} result calculated...", threadIndex);  
        _doneEvent.Set();  
    }  
  
    // Recursive method that calculates the Nth Fibonacci number.  
    public int Calculate(int n)  
    {  
        if (n <= 1)  
        {  
            return n;  
        }  
  
        return Calculate(n - 1) + Calculate(n - 2);  
    }  
}  
  
public class ThreadPoolExample  
{  
    static void Main()  
    {  
        const int FibonacciCalculations = 10;  
  
        // One event is used for each Fibonacci object.  
        ManualResetEvent[] doneEvents = new ManualResetEvent[FibonacciCalculations];  
        Fibonacci[] fibArray = new Fibonacci[FibonacciCalculations];  
        Random r = new Random();  
  
        // Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations);  
        for (int i = 0; i < FibonacciCalculations; i++)  
        {  
            doneEvents[i] = new ManualResetEvent(false);  
            Fibonacci f = new Fibonacci(r.Next(20, 40), doneEvents[i]);  
            fibArray[i] = f;  
            ThreadPool.QueueUserWorkItem(f.ThreadPoolCallback, i);  
        }  
  
        // Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents);  
        Console.WriteLine("All calculations are complete.");  
  
        // Display the results.  
        for (int i= 0; i<FibonacciCalculations; i++)  
        {  
            Fibonacci f = fibArray[i];  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f0b54-113">Tady je příklad výstupu.</span><span class="sxs-lookup"><span data-stu-id="f0b54-113">Following is an example of the output.</span></span>  
  
```  
launching 10 tasks...  
thread 0 started...  
thread 1 started...  
thread 1 result calculated...  
thread 2 started...  
thread 2 result calculated...  
thread 3 started...  
thread 3 result calculated...  
thread 4 started...  
thread 0 result calculated...  
thread 5 started...  
thread 5 result calculated...  
thread 6 started...  
thread 4 result calculated...  
thread 7 started...  
thread 6 result calculated...  
thread 8 started...  
thread 8 result calculated...  
thread 9 started...  
thread 9 result calculated...  
thread 7 result calculated...  
All calculations are complete.  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(25) = 75025  
Fibonacci(22) = 17711  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(29) = 514229  
Fibonacci(38) = 39088169  
Fibonacci(21) = 10946  
Fibonacci(27) = 196418  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0b54-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0b54-114">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="f0b54-115">Přístup z více vláken sdružování (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b54-115">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="f0b54-116">Dělení na vlákna (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b54-116">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="f0b54-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f0b54-117">Security</span></span>](../../../../standard/security/index.md)
