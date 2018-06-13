---
title: Časovače vláken (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
ms.openlocfilehash: 019b8372be63b9a9fdbcee134834a34f6bef2b74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646889"
---
# <a name="thread-timers-visual-basic"></a><span data-ttu-id="c404d-102">Časovače vláken (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c404d-102">Thread Timers (Visual Basic)</span></span>
<span data-ttu-id="c404d-103"><xref:System.Threading.Timer?displayProperty=nameWithType> Třída je užitečná pro pravidelně spuštění úlohy na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="c404d-103">The <xref:System.Threading.Timer?displayProperty=nameWithType> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="c404d-104">Časovače vláken můžete například použít ke kontrole stavu a integritu databáze, nebo k zálohování důležitých souborů.</span><span class="sxs-lookup"><span data-stu-id="c404d-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="c404d-105">Příklad časovače vláken</span><span class="sxs-lookup"><span data-stu-id="c404d-105">Thread Timer Example</span></span>  
 <span data-ttu-id="c404d-106">V následujícím příkladu spustí úlohu každých dvou sekund a používá příznak zahájíte <xref:System.IDisposable.Dispose%2A> metoda, která ukončí časovač.</span><span class="sxs-lookup"><span data-stu-id="c404d-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="c404d-107">Tento příklad odešle stav do okna výstupu.</span><span class="sxs-lookup"><span data-stu-id="c404d-107">This example posts status to the output window.</span></span>  
  
```vb  
Private Class StateObjClass  
    ' Used to hold parameters for calls to TimerTask.  
    Public SomeValue As Integer  
    Public TimerReference As System.Threading.Timer  
    Public TimerCanceled As Boolean  
End Class  
  
Public Sub RunTimer()  
    Dim StateObj As New StateObjClass  
    StateObj.TimerCanceled = False  
    StateObj.SomeValue = 1  
    Dim TimerDelegate As New System.Threading.TimerCallback(AddressOf TimerTask)  
    ' Create a timer that calls a procedure every 2 seconds.  
    ' Note: There is no Start method; the timer starts running as soon as   
    ' the instance is created.  
    Dim TimerItem As New System.Threading.Timer(TimerDelegate, StateObj,  
                                                2000, 2000)  
    ' Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem  
  
    ' Run for ten loops.  
    While StateObj.SomeValue < 10  
        ' Wait one second.  
        System.Threading.Thread.Sleep(1000)  
    End While  
  
    ' Request Dispose of the timer object.  
    StateObj.TimerCanceled = True  
End Sub  
  
Private Sub TimerTask(ByVal StateObj As Object)  
    Dim State As StateObjClass = CType(StateObj, StateObjClass)  
    ' Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(State.SomeValue)  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " & Now.ToString)  
    If State.TimerCanceled Then  
        ' Dispose Requested.  
        State.TimerReference.Dispose()  
        System.Diagnostics.Debug.WriteLine("Done  " & Now)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="c404d-108">Časovače vláken jsou obzvláště užitečná, když <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> objektu není k dispozici, například když vyvíjíte konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="c404d-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c404d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c404d-109">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="c404d-110">Vícevláknové aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c404d-110">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
