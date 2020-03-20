---
title: dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: d3fe7d11657c2f9edd1fea7ff639f878f993d6b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174768"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="42ddf-102">dangerousThreadingAPI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="42ddf-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="42ddf-103">Spravovaný `dangerousThreadingAPI` pomocník pro ladění (MDA) <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> je aktivován, když je metoda volána v jiném vlákně než aktuálnívlákno.</span><span class="sxs-lookup"><span data-stu-id="42ddf-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="42ddf-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="42ddf-104">Symptoms</span></span>  
 <span data-ttu-id="42ddf-105">Aplikace neodpovídá nebo přestane reagovat neomezeně dlouho.</span><span class="sxs-lookup"><span data-stu-id="42ddf-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="42ddf-106">Data systému nebo aplikace mohou být dočasně ponechána v nepředvídatelném stavu nebo dokonce i po vypnutí aplikace.</span><span class="sxs-lookup"><span data-stu-id="42ddf-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="42ddf-107">Některé operace nejsou dokončeny podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="42ddf-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="42ddf-108">Příznaky se mohou značně lišit v důsledku náhodnosti vlastní problému.</span><span class="sxs-lookup"><span data-stu-id="42ddf-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="42ddf-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="42ddf-109">Cause</span></span>  
 <span data-ttu-id="42ddf-110">Podproces je asynchronně pozastavena jiným vláknem <xref:System.Threading.Thread.Suspend%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="42ddf-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="42ddf-111">Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiné vlákno, které může být uprostřed operace.</span><span class="sxs-lookup"><span data-stu-id="42ddf-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="42ddf-112">Pozastavení podprocesu může mít za následek poškození dat nebo přerušení invariants.</span><span class="sxs-lookup"><span data-stu-id="42ddf-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="42ddf-113">Pokud podproces být umístěn do pozastaveného stavu <xref:System.Threading.Thread.Resume%2A> a nikdy obnovena pomocí metody, aplikace může zavěsit neomezeně dlouho a případně poškodit data aplikace.</span><span class="sxs-lookup"><span data-stu-id="42ddf-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="42ddf-114">Tyto metody byly označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="42ddf-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="42ddf-115">Pokud synchronizační primitiva jsou drženy cílovým vláknem, zůstávají drženy během pozastavení.</span><span class="sxs-lookup"><span data-stu-id="42ddf-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="42ddf-116">To může vést k zablokování by měl jiný podproces, například vlákno provádějící <xref:System.Threading.Thread.Suspend%2A>, pokus o získání zámku na primitivní.</span><span class="sxs-lookup"><span data-stu-id="42ddf-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="42ddf-117">V této situaci problém projevuje jako zablokování.</span><span class="sxs-lookup"><span data-stu-id="42ddf-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="42ddf-118">Řešení</span><span class="sxs-lookup"><span data-stu-id="42ddf-118">Resolution</span></span>  
 <span data-ttu-id="42ddf-119">Vyhněte se návrhům, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="42ddf-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="42ddf-120">Pro spolupráci mezi vlákny použijte synchronizační <xref:System.Threading.ReaderWriterLock> <xref:System.Threading.Mutex>primitiva, například <xref:System.Threading.Monitor>, , nebo c# `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="42ddf-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="42ddf-121">Pokud je nutné použít tyto metody, snížit časové okno a minimalizovat množství kódu, který se spustí, zatímco vlákno je v pozastaveném stavu.</span><span class="sxs-lookup"><span data-stu-id="42ddf-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="42ddf-122">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="42ddf-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="42ddf-123">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="42ddf-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="42ddf-124">Pouze hlásí data o nebezpečných operacích podprocesu.</span><span class="sxs-lookup"><span data-stu-id="42ddf-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="42ddf-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="42ddf-125">Output</span></span>  
 <span data-ttu-id="42ddf-126">MDA identifikuje nebezpečnou metodu threadingu, která způsobila jeho aktivaci.</span><span class="sxs-lookup"><span data-stu-id="42ddf-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="42ddf-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="42ddf-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="42ddf-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="42ddf-128">Example</span></span>  
 <span data-ttu-id="42ddf-129">Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metody, která způsobuje `dangerousThreadingAPI`aktivaci .</span><span class="sxs-lookup"><span data-stu-id="42ddf-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="42ddf-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="42ddf-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="42ddf-131">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="42ddf-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="42ddf-132">lock – příkaz</span><span class="sxs-lookup"><span data-stu-id="42ddf-132">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
