---
title: Parametry a návratové hodnoty pro procedury ve více vláknech (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: 218e297d192d37d55ff391045342262d7bf66a0c
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875121"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="9f6b5-102">Parametry a návratové hodnoty pro procedury ve více vláknech (C#)</span><span class="sxs-lookup"><span data-stu-id="9f6b5-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="9f6b5-103">Zadávání a vrací hodnoty ve vícevláknových aplikacích je složitější, protože konstruktor třídy vlákno musí být předán odkaz na proceduru, která nepřijímá žádné argumenty a nevrací žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="9f6b5-104">V následujících částech se dozvíte některé jednoduché způsoby, jak zadat parametry a návratové hodnoty z procedury v samostatných vláknech.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="9f6b5-105">Poskytuje parametry pro procedury ve více vláknech</span><span class="sxs-lookup"><span data-stu-id="9f6b5-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="9f6b5-106">Nejlepší způsob, jak zadat parametry pro volání metody s více vlákny je zabalit cílové metody ve třídě a definování polí pro danou třídu, která bude sloužit jako parametry pro nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="9f6b5-107">Výhodou tohoto přístupu je, že pokaždé, když chcete vytvořit nové vlákno, můžete vytvořit novou instanci třídy, s vlastní parametry.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="9f6b5-108">Předpokládejme například, že máte funkci, která vypočítá trojúhelník, stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="9f6b5-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="9f6b5-109">Můžete napsat třídu, která zabalí `CalcArea` funkce a vytvoří pole k uložení vstupních parametrů, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9f6b5-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
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
  
 <span data-ttu-id="9f6b5-110">Použít `AreaClass`, můžete vytvořit `AreaClass` objektu a nastavit `Base` a `Height` vlastnosti, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="9f6b5-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
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
  
 <span data-ttu-id="9f6b5-111">Všimněte si, že `TestArea` postup neprovede kontrolu hodnoty `Area` pole po volání `CalcArea` metody.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="9f6b5-112">Protože `CalcArea` běží v samostatném vlákně, `Area` není zaručeno, že pole lze nastavit, pokud zaškrtnete ihned po volání `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="9f6b5-113">Další část popisuje lepší způsob, jak vrácení hodnoty z procedury ve více vláknech.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="9f6b5-114">Vrácení hodnoty z procedury ve více vláknech</span><span class="sxs-lookup"><span data-stu-id="9f6b5-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="9f6b5-115">Vrácení hodnoty z procedury, které běží v samostatných vláknech je složité tím, že postupy nemůže být funkce nelze použít `ByRef` argumenty.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="9f6b5-116">Nejjednodušší způsob, jak vrátit hodnoty má používat <xref:System.ComponentModel.BackgroundWorker> součásti spravovat vlákna a vyvolat událost dokončení úkolu a zpracování výsledků s obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="9f6b5-117">Následující příklad vrátí hodnotu ve vyvolání události z běžící na samostatném vlákně procedury:</span><span class="sxs-lookup"><span data-stu-id="9f6b5-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
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
  
 <span data-ttu-id="9f6b5-118">Můžete zadat parametry a návratové hodnoty do vláken fondu vláken pomocí volitelného `ByVal` proměnné stavu objektu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="9f6b5-119">Vlákna vlákna časovače podporují také stav objektu pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="9f6b5-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="9f6b5-120">Informace o sdružování vláken a vlákna časovače, naleznete v tématu [sdružování vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) a [časovače](../../../../standard/threading/timers.md).</span><span class="sxs-lookup"><span data-stu-id="9f6b5-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Timers](../../../../standard/threading/timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6b5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f6b5-121">See Also</span></span>  
 [<span data-ttu-id="9f6b5-122">Návod: Multithreading s komponentou BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="9f6b5-122">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="9f6b5-123">Vlákno sdružování (C#)</span><span class="sxs-lookup"><span data-stu-id="9f6b5-123">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="9f6b5-124">Synchronizace vláken (C#)</span><span class="sxs-lookup"><span data-stu-id="9f6b5-124">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="9f6b5-125">Události</span><span class="sxs-lookup"><span data-stu-id="9f6b5-125">Events</span></span>](../../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="9f6b5-126">Vícevláknové aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="9f6b5-126">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="9f6b5-127">Delegáti</span><span class="sxs-lookup"><span data-stu-id="9f6b5-127">Delegates</span></span>](../../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="9f6b5-128">Multithreading u komponent</span><span class="sxs-lookup"><span data-stu-id="9f6b5-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
