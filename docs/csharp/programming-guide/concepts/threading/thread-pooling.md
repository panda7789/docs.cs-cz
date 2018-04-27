---
title: Přístup z více vláken sdružování (C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: 5
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56fba1197fe81e60e27f300ec43879569d0a9d48
ms.sourcegitcommit: 68b60d38043e50104ccc90c76f8599b1ffe18346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="thread-pooling-c"></a><span data-ttu-id="e9b66-102">Přístup z více vláken sdružování (C#)</span><span class="sxs-lookup"><span data-stu-id="e9b66-102">Thread Pooling (C#)</span></span>
<span data-ttu-id="e9b66-103">A *fondu vláken* je kolekce vláken, které lze použít k provedení některých úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e9b66-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="e9b66-104">(Viz [zřetězení (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) základní informace.) Zůstane primární bezplatné provést další úlohy asynchronně vlákno.</span><span class="sxs-lookup"><span data-stu-id="e9b66-104">(See [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="e9b66-105">Fondy vláken jsou často používané v serverových aplikací.</span><span class="sxs-lookup"><span data-stu-id="e9b66-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="e9b66-106">Každého příchozího požadavku je přiřazen k vlákno z fondu podprocesů tak, aby požadavek může zpracovat asynchronně, bez třeba zadávat primární vlákno nebo zpozdit zpracování následných žádostí.</span><span class="sxs-lookup"><span data-stu-id="e9b66-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="e9b66-107">Po dokončení úkolu vláken ve fondu se vrátí do fronty čekání vláken, kde ji můžete znovu použít.</span><span class="sxs-lookup"><span data-stu-id="e9b66-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="e9b66-108">Tato opakované použití umožňuje aplikacím vyhnout náklady na vytvoření nové vlákno pro každou úlohu.</span><span class="sxs-lookup"><span data-stu-id="e9b66-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="e9b66-109">Fondy vláken obvykle mají maximální počet vláken.</span><span class="sxs-lookup"><span data-stu-id="e9b66-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="e9b66-110">Pokud jsou všechna vlákna zaneprázdněný, další úkoly jsou umístěna do fronty, dokud se zpracováním vláken dostupná.</span><span class="sxs-lookup"><span data-stu-id="e9b66-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="e9b66-111">Můžete implementovat vlastní fond vláken, ale je jednodušší použít poskytované rozhraní .NET Framework prostřednictvím fondu vláken <xref:System.Threading.ThreadPool> třídy.</span><span class="sxs-lookup"><span data-stu-id="e9b66-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="e9b66-112">S sdružování vláken zavoláte <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> metoda s delegáta pro postup, který chcete spustit, a C# vytvoří vlákno a spustí procedury.</span><span class="sxs-lookup"><span data-stu-id="e9b66-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and C# creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="e9b66-113">Příklad sdružování vláken</span><span class="sxs-lookup"><span data-stu-id="e9b66-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="e9b66-114">Následující příklad ukazuje, jak je možné používat vlákno sdružování spustit několik úloh.</span><span class="sxs-lookup"><span data-stu-id="e9b66-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 <span data-ttu-id="e9b66-115">Jednou z výhod sdružování vláken je, že můžete předat argumenty v objektu stavu k postupu úloh.</span><span class="sxs-lookup"><span data-stu-id="e9b66-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="e9b66-116">Pokud jsou volání procedura vyžaduje více než jeden argument, může odevzdat strukturou nebo instance třídy do `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="e9b66-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="e9b66-117">Vlákno fondu parametry a návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="e9b66-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="e9b66-118">Vrácení hodnoty z vlákna, fondu vláken není jasné.</span><span class="sxs-lookup"><span data-stu-id="e9b66-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="e9b66-119">Standardní způsob vrácení hodnot z volání funkce není povolena, protože `Sub` postupy jsou jediným typem procedury, která může zařazených do fronty pro fond vláken.</span><span class="sxs-lookup"><span data-stu-id="e9b66-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="e9b66-120">Jedním ze způsobů, můžete zadat parametry a vrátí hodnoty, je zabalení parametry, vrácených hodnot, a metody v obálce třídy, jak je popsáno v [parametry a vrátí hodnoty pro procedury ve více vláknech (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e9b66-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="e9b66-121">Snadný způsob, jak zadat parametry a návratové hodnoty je pomocí volitelného `ByVal` proměnné objektu stavu systému <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e9b66-121">An easier way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="e9b66-122">Pokud použijete tuto proměnnou k předání odkaz na instanci třídy, můžete členů instance upraveném vlákno fondu vláken a použít jako návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e9b66-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="e9b66-123">Zpočátku nemusí být zřejmé, že můžete upravit objekt, na kterou odkazuje proměnná, která je předaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e9b66-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="e9b66-124">To můžete provést, protože pouze odkaz na objekt je předaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e9b66-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="e9b66-125">Pokud provedete změny členům objektu, na kterou odkazuje odkaz na objekt, použít změny instance třídy skutečný.</span><span class="sxs-lookup"><span data-stu-id="e9b66-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="e9b66-126">Struktury nelze použít k návratu hodnot uvnitř stavu objektů.</span><span class="sxs-lookup"><span data-stu-id="e9b66-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="e9b66-127">Protože struktury jsou typy hodnot, neměňte změny, které provede asynchronní proces členů původní struktura.</span><span class="sxs-lookup"><span data-stu-id="e9b66-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="e9b66-128">Návratové hodnoty nejsou potřebné zajistit parametry používejte struktury.</span><span class="sxs-lookup"><span data-stu-id="e9b66-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b66-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9b66-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="e9b66-130">Postupy: použití fondu vláken (C#)</span><span class="sxs-lookup"><span data-stu-id="e9b66-130">How to: Use a Thread Pool (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="e9b66-131">Dělení na vlákna (C#)</span><span class="sxs-lookup"><span data-stu-id="e9b66-131">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="e9b66-132">Vícevláknové aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="e9b66-132">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="e9b66-133">Synchronizace vláken (C#)</span><span class="sxs-lookup"><span data-stu-id="e9b66-133">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
