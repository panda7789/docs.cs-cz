---
title: "Parametry a návratové hodnoty pro procedury ve více vláknech (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fec0ad955439f0cd683ad56c8d6433eed2417304
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="2118d-102">Parametry a návratové hodnoty pro procedury ve více vláknech (C#)</span><span class="sxs-lookup"><span data-stu-id="2118d-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="2118d-103">Poskytnutí a vrácení hodnot v Vícevláknová aplikace je složité, protože v konstruktoru pro třídu přístup z více vláken, musí být předán odkaz na procedury, která nezadávaly žádné argumenty a nevrací žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2118d-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="2118d-104">Následující části vysvětlují, některá jednoduché způsoby, jak zadat parametry a návratové hodnoty z procedury v samostatných vláknech.</span><span class="sxs-lookup"><span data-stu-id="2118d-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="2118d-105">Poskytuje parametry pro procedury ve více vláknech</span><span class="sxs-lookup"><span data-stu-id="2118d-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="2118d-106">Nejlepší způsob, jak zadat parametry pro volání metody s více vlákny je zabalit do cílové metody ve třídě a definování polí pro tuto třídu, která bude sloužit jako parametry pro nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="2118d-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="2118d-107">Výhodou tohoto přístupu je, že můžete vytvořit novou instanci třídy, s vlastní parametry, pokaždé, když chcete spustit nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="2118d-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="2118d-108">Předpokládejme například, že máte funkce pro výpočet oblasti trojúhelníku, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="2118d-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="2118d-109">Můžete napsat třídu, která zabalí `CalcArea` funkce a vytvoří pole k uložení vstupních parametrů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2118d-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="2118d-110">Použít `AreaClass`, můžete vytvořit `AreaClass` objektu a nastavte `Base` a `Height` vlastnosti, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="2118d-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 <span data-ttu-id="2118d-111">Všimněte si, že `TestArea` postup nekontroluje hodnotu `Area` pole po volání `CalcArea` metoda.</span><span class="sxs-lookup"><span data-stu-id="2118d-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="2118d-112">Protože `CalcArea` běží na samostatném vlákně, `Area` pole není zaručeno, nastavit, pokud zaškrtnete ihned po volání `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="2118d-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="2118d-113">Další část popisuje lepší způsob vrácení hodnoty z procedury ve více vláknech.</span><span class="sxs-lookup"><span data-stu-id="2118d-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="2118d-114">Vrácení hodnoty z procedury ve více vláknech</span><span class="sxs-lookup"><span data-stu-id="2118d-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="2118d-115">Vrácení hodnoty z procedury, které běží v samostatných vláknech ztěžuje skutečnost, že postupy nemůže být funkce a nemůžete použít `ByRef` argumenty.</span><span class="sxs-lookup"><span data-stu-id="2118d-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="2118d-116">Nejjednodušší způsob, jak vrátit hodnoty má používat <xref:System.ComponentModel.BackgroundWorker> součásti spravovat vaše vláken a vyvolat událost v případě, že po dokončení úkolu a zpracovat výsledky obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="2118d-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="2118d-117">Následující příklad vrací hodnotu podle vyvolání události z procedury systémem samostatné vláken:</span><span class="sxs-lookup"><span data-stu-id="2118d-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 <span data-ttu-id="2118d-118">Můžete zadat parametry a návratové hodnoty pro fond vláken vláken pomocí volitelného `ByVal` proměnná objekt stavu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2118d-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="2118d-119">Časovače vláken vláken také podporují objekt stavu pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="2118d-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="2118d-120">Informace o sdružování vláken a časovače vláken najdete v tématu [sdružování vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) a [časovače vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span><span class="sxs-lookup"><span data-stu-id="2118d-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Thread Timers (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2118d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2118d-121">See Also</span></span>  
 [<span data-ttu-id="2118d-122">Návod: Multithreading s komponentou BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="2118d-122">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="2118d-123">Přístup z více vláken sdružování (C#)</span><span class="sxs-lookup"><span data-stu-id="2118d-123">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="2118d-124">Synchronizace vláken (C#)</span><span class="sxs-lookup"><span data-stu-id="2118d-124">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="2118d-125">Události</span><span class="sxs-lookup"><span data-stu-id="2118d-125">Events</span></span>](../../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="2118d-126">Vícevláknové aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="2118d-126">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="2118d-127">Delegáti</span><span class="sxs-lookup"><span data-stu-id="2118d-127">Delegates</span></span>](../../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="2118d-128">Více vláken v součásti</span><span class="sxs-lookup"><span data-stu-id="2118d-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
