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
# <a name="how-to-use-a-thread-pool-c"></a>Postupy: použití fondu vláken (C#)
*Sdružování vláken* je forma více vláken v úkoly, které jsou přidány do fronty a automaticky spuštěn při vytvoření vláken. Další informace najdete v tématu [vláken sdružování (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md).  
  
 Následující příklad používá k výpočtu fondu vláken rozhraní .NET Framework `Fibonacci` výsledek deset čísel až 20, 40. Každý `Fibonacci` výsledek je reprezentována `Fibonacci` třídy, která poskytuje metodu s názvem `ThreadPoolCallback` který provede výpočet. Objekt, který reprezentuje všechny `Fibonacci` hodnota je vytvořena a `ThreadPoolCallback` předaný metoda <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, které přiřadí k dispozici přístup z více vláken ve fondu se mají spustit metodu.  
  
 Protože každý `Fibonacci` objektu je uveden polovičním náhodná hodnota k výpočtu a protože každé vlákno bude neslučitelných pro využití procesoru, nemůže vědět předem jak dlouho trvat pro všechny deset výsledky se vypočítá. To je důvod, proč každý `Fibonacci` objekt předá instance <xref:System.Threading.ManualResetEvent> třída během vytváření. Každý objekt signály objekt zadané události při jeho bude dokončen výpočet, který umožňuje primární vlákno k provádění bloku s <xref:System.Threading.WaitHandle.WaitAll%2A> až deset všechny `Fibonacci` objekty vypočítali výsledku. `Main` Metoda pak zobrazí každý `Fibonacci` výsledek.  
  
## <a name="example"></a>Příklad  
  
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
  
 Tady je příklad výstupu.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [Přístup z více vláken sdružování (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [Dělení na vlákna (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Zabezpečení](../../../../standard/security/index.md)
