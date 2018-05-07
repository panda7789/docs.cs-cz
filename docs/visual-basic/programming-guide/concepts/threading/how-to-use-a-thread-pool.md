---
title: 'Postupy: použití fondu vláken (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 90a0bb24-39f8-41f5-a217-b52a7d4fed0b
ms.openlocfilehash: a61defc2e40662d7fdadb40693e757fa559adb6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-thread-pool-visual-basic"></a>Postupy: použití fondu vláken (Visual Basic)
*Sdružování vláken* je forma více vláken v úkoly, které jsou přidány do fronty a automaticky spuštěn při vytvoření vláken. Další informace najdete v tématu [vláken sdružování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md).  
  
 Následující příklad používá k výpočtu fondu vláken rozhraní .NET Framework `Fibonacci` výsledek deset čísel až 20, 40. Každý `Fibonacci` výsledek je reprezentována `Fibonacci` třídy, která poskytuje metodu s názvem `ThreadPoolCallback` který provede výpočet. Objekt, který reprezentuje všechny `Fibonacci` hodnota je vytvořena a `ThreadPoolCallback` předaný metoda <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, které přiřadí k dispozici přístup z více vláken ve fondu se mají spustit metodu.  
  
 Protože každý `Fibonacci` objektu je uveden polovičním náhodná hodnota k výpočtu a protože každé vlákno bude neslučitelných pro využití procesoru, nemůže vědět předem jak dlouho trvat pro všechny deset výsledky se vypočítá. To je důvod, proč každý `Fibonacci` objekt předá instance <xref:System.Threading.ManualResetEvent> třída během vytváření. Každý objekt signály objekt zadané události při jeho bude dokončen výpočet, který umožňuje primární vlákno k provádění bloku s <xref:System.Threading.WaitHandle.WaitAll%2A> až deset všechny `Fibonacci` objekty vypočítali výsledku. `Main` Metoda pak zobrazí každý `Fibonacci` výsledek.  
  
## <a name="example"></a>Příklad  
  
```vb  
Imports System.Threading  
  
Module Module1  
  
    Public Class Fibonacci  
        Private _n As Integer  
        Private _fibOfN  
        Private _doneEvent As ManualResetEvent  
  
        Public ReadOnly Property N() As Integer  
            Get  
                Return _n  
            End Get  
        End Property  
  
        Public ReadOnly Property FibOfN() As Integer  
            Get  
                Return _fibOfN  
            End Get  
        End Property  
  
        Sub New(ByVal n As Integer, ByVal doneEvent As ManualResetEvent)  
            _n = n  
            _doneEvent = doneEvent  
        End Sub  
  
        ' Wrapper method for use with the thread pool.  
        Public Sub ThreadPoolCallBack(ByVal threadContext As Object)  
            Dim threadIndex As Integer = CType(threadContext, Integer)  
            Console.WriteLine("thread {0} started...", threadIndex)  
            _fibOfN = Calculate(_n)  
            Console.WriteLine("thread {0} result calculated...", threadIndex)  
            _doneEvent.Set()  
        End Sub  
  
        Public Function Calculate(ByVal n As Integer) As Integer  
            If n <= 1 Then  
                Return n  
            End If  
            Return Calculate(n - 1) + Calculate(n - 2)  
        End Function  
  
    End Class  
  
    <MTAThread()>   
    Sub Main()  
        Const FibonacciCalculations As Integer = 9 ' 0 to 9  
  
        ' One event is used for each Fibonacci object  
        Dim doneEvents(FibonacciCalculations) As ManualResetEvent  
        Dim fibArray(FibonacciCalculations) As Fibonacci  
        Dim r As New Random()  
  
        ' Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations)  
  
        For i As Integer = 0 To FibonacciCalculations  
            doneEvents(i) = New ManualResetEvent(False)  
            Dim f = New Fibonacci(r.Next(20, 40), doneEvents(i))  
            fibArray(i) = f  
            ThreadPool.QueueUserWorkItem(AddressOf f.ThreadPoolCallBack, i)  
        Next  
  
        ' Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents)  
        Console.WriteLine("All calculations are complete.")  
  
        ' Display the results.  
        For i As Integer = 0 To FibonacciCalculations  
            Dim f As Fibonacci = fibArray(i)  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN)  
        Next  
    End Sub  
  
End Module  
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
 [Přístup z více vláken sdružování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Dělení na vlákna (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Zabezpečení](../../../../standard/security/index.md)
