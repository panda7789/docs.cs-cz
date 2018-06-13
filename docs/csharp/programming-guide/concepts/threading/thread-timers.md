---
title: Časovače vláken (C#)
ms.date: 07/20/2015
ms.assetid: 52ed71e8-4fd9-43a4-ae40-04cce7cff23f
ms.openlocfilehash: c2be9fef0b3f6f3db7ae8c9a519ece0cb64b6f49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323440"
---
# <a name="thread-timers-c"></a><span data-ttu-id="72a76-102">Časovače vláken (C#)</span><span class="sxs-lookup"><span data-stu-id="72a76-102">Thread Timers (C#)</span></span>
<span data-ttu-id="72a76-103"><xref:System.Threading.Timer?displayProperty=nameWithType> Třída je užitečná pro pravidelně spuštění úlohy na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="72a76-103">The <xref:System.Threading.Timer?displayProperty=nameWithType> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="72a76-104">Časovače vláken můžete například použít ke kontrole stavu a integritu databáze, nebo k zálohování důležitých souborů.</span><span class="sxs-lookup"><span data-stu-id="72a76-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="72a76-105">Příklad časovače vláken</span><span class="sxs-lookup"><span data-stu-id="72a76-105">Thread Timer Example</span></span>  
 <span data-ttu-id="72a76-106">V následujícím příkladu spustí úlohu každých dvou sekund a používá příznak zahájíte <xref:System.IDisposable.Dispose%2A> metoda, která ukončí časovač.</span><span class="sxs-lookup"><span data-stu-id="72a76-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="72a76-107">Tento příklad odešle stav do okna výstupu.</span><span class="sxs-lookup"><span data-stu-id="72a76-107">This example posts status to the output window.</span></span>  
  
```csharp  
private class StateObjClass  
{  
    // Used to hold parameters for calls to TimerTask.  
    public int SomeValue;  
    public System.Threading.Timer TimerReference;  
    public bool TimerCanceled;  
}  
  
public void RunTimer()  
{  
    StateObjClass StateObj = new StateObjClass();  
    StateObj.TimerCanceled = false;  
    StateObj.SomeValue = 1;  
    System.Threading.TimerCallback TimerDelegate =  
        new System.Threading.TimerCallback(TimerTask);  
  
    // Create a timer that calls a procedure every 2 seconds.  
    // Note: There is no Start method; the timer starts running as soon as   
    // the instance is created.  
    System.Threading.Timer TimerItem =  
        new System.Threading.Timer(TimerDelegate, StateObj, 2000, 2000);  
  
    // Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem;    
  
    // Run for ten loops.  
    while (StateObj.SomeValue < 10)   
    {  
        // Wait one second.  
        System.Threading.Thread.Sleep(1000);    
    }  
  
    // Request Dispose of the timer object.  
    StateObj.TimerCanceled = true;    
}  
  
private void TimerTask(object StateObj)  
{  
    StateObjClass State = (StateObjClass)StateObj;  
    // Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(ref State.SomeValue);  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " + DateTime.Now.ToString());  
    if (State.TimerCanceled)      
    // Dispose Requested.  
    {  
        State.TimerReference.Dispose();  
        System.Diagnostics.Debug.WriteLine("Done  " + DateTime.Now.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="72a76-108">Časovače vláken jsou obzvláště užitečná, když <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> objektu není k dispozici, například když vyvíjíte konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="72a76-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a76-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="72a76-109">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="72a76-110">Vícevláknové aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="72a76-110">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)
