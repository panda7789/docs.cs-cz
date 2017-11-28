---
title: "Parametry a návratové hodnoty pro procedury ve více vláknech (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 071e0aa916e4b3464c7c0cbff6596cabc6b67906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="a4dff-102">Parametry a návratové hodnoty pro procedury ve více vláknech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4dff-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="a4dff-103">Poskytnutí a vrácení hodnot v Vícevláknová aplikace je složité, protože v konstruktoru pro třídu přístup z více vláken, musí být předán odkaz na procedury, která nezadávaly žádné argumenty a nevrací žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a4dff-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="a4dff-104">Následující části vysvětlují, některá jednoduché způsoby, jak zadat parametry a návratové hodnoty z procedury v samostatných vláknech.</span><span class="sxs-lookup"><span data-stu-id="a4dff-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="a4dff-105">Poskytuje parametry pro procedury ve více vláknech</span><span class="sxs-lookup"><span data-stu-id="a4dff-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="a4dff-106">Nejlepší způsob, jak zadat parametry pro volání metody s více vlákny je zabalit do cílové metody ve třídě a definování polí pro tuto třídu, která bude sloužit jako parametry pro nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="a4dff-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="a4dff-107">Výhodou tohoto přístupu je, že můžete vytvořit novou instanci třídy, s vlastní parametry, pokaždé, když chcete spustit nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="a4dff-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="a4dff-108">Předpokládejme například, že máte funkce pro výpočet oblasti trojúhelníku, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="a4dff-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="a4dff-109">Můžete napsat třídu, která zabalí `CalcArea` funkce a vytvoří pole k uložení vstupních parametrů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a4dff-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="a4dff-110">Použít `AreaClass`, můžete vytvořit `AreaClass` objektu a nastavte `Base` a `Height` vlastnosti, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="a4dff-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 <span data-ttu-id="a4dff-111">Všimněte si, že `TestArea` postup nekontroluje hodnotu `Area` pole po volání `CalcArea` metoda.</span><span class="sxs-lookup"><span data-stu-id="a4dff-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="a4dff-112">Protože `CalcArea` běží na samostatném vlákně, `Area` pole není zaručeno, nastavit, pokud zaškrtnete ihned po volání `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="a4dff-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="a4dff-113">Další část popisuje lepší způsob vrácení hodnoty z procedury ve více vláknech.</span><span class="sxs-lookup"><span data-stu-id="a4dff-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="a4dff-114">Vrácení hodnoty z procedury ve více vláknech</span><span class="sxs-lookup"><span data-stu-id="a4dff-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="a4dff-115">Vrácení hodnoty z procedury, které běží v samostatných vláknech ztěžuje skutečnost, že postupy nemůže být funkce a nemůžete použít `ByRef` argumenty.</span><span class="sxs-lookup"><span data-stu-id="a4dff-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="a4dff-116">Nejjednodušší způsob, jak vrátit hodnoty má používat <xref:System.ComponentModel.BackgroundWorker> součásti spravovat vaše vláken a vyvolat událost v případě, že po dokončení úkolu a zpracovat výsledky obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="a4dff-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="a4dff-117">Následující příklad vrací hodnotu podle vyvolání události z procedury systémem samostatné vláken:</span><span class="sxs-lookup"><span data-stu-id="a4dff-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 <span data-ttu-id="a4dff-118">Můžete zadat parametry a návratové hodnoty pro fond vláken vláken pomocí volitelného `ByVal` proměnná objekt stavu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a4dff-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="a4dff-119">Časovače vláken vláken také podporují objekt stavu pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="a4dff-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="a4dff-120">Informace o sdružování vláken a časovače vláken najdete v tématu [sdružování vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[sdružování vláken](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) a [časovače vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span><span class="sxs-lookup"><span data-stu-id="a4dff-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Thread Timers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4dff-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4dff-121">See Also</span></span>  
 [<span data-ttu-id="a4dff-122">Návod: Multithreading s komponentou BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4dff-122">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="a4dff-123">Přístup z více vláken sdružování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4dff-123">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="a4dff-124">Synchronizace vláken (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4dff-124">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="a4dff-125">Události</span><span class="sxs-lookup"><span data-stu-id="a4dff-125">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="a4dff-126">Vícevláknové aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4dff-126">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="a4dff-127">Delegáti</span><span class="sxs-lookup"><span data-stu-id="a4dff-127">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="a4dff-128">Více vláken v součásti</span><span class="sxs-lookup"><span data-stu-id="a4dff-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
