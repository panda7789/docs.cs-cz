---
title: "Stavy spravovaných vláken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956472ef0e3b0bab85a4eb0b5585f1a4d1e0a991
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="managed-thread-states"></a><span data-ttu-id="dc9f7-102">Stavy spravovaných vláken</span><span class="sxs-lookup"><span data-stu-id="dc9f7-102">Managed Thread States</span></span>
<span data-ttu-id="dc9f7-103">Vlastnost <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> poskytuje bitová maska určující, aktuální stav vlákna.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-103">The property <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> provides a bit mask that indicates the thread's current state.</span></span> <span data-ttu-id="dc9f7-104">Vlákno je vždy alespoň v jedné z možných stavů v <xref:System.Threading.ThreadState> výčtu a může být ve více státech ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-104">A thread is always in at least one of the possible states in the <xref:System.Threading.ThreadState> enumeration, and can be in multiple states at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc9f7-105">Stav vlákna je pouze zájem o několik ladění scénáře.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-105">Thread state is only of interest in a few debugging scenarios.</span></span> <span data-ttu-id="dc9f7-106">Váš kód by měl stav vlákna nikdy používat k synchronizaci aktivity vláken.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-106">Your code should never use thread state to synchronize the activities of threads.</span></span>  
  
 <span data-ttu-id="dc9f7-107">Když vytvoříte spravované vlákno, je v <xref:System.Threading.ThreadState.Unstarted> stavu.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-107">When you create a managed thread, it is in the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="dc9f7-108">Vlákno zůstane v <xref:System.Threading.ThreadState.Unstarted> stavu, dokud je přesunut do spuštěného stavu v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-108">The thread remains in the <xref:System.Threading.ThreadState.Unstarted> state until it is moved into the started state by the operating system.</span></span> <span data-ttu-id="dc9f7-109">Volání metody <xref:System.Threading.Thread.Start%2A> umožňuje operační systém vědět, že lze spustit vlákno; nezmění stav vlákno.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-109">Calling <xref:System.Threading.Thread.Start%2A> lets the operating system know that the thread can be started; it does not change the state of the thread.</span></span>  
  
 <span data-ttu-id="dc9f7-110">Nespravované vláken, která zadejte spravované prostředí jsou již ve stavu spuštěna.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-110">Unmanaged threads that enter the managed environment are already in the started state.</span></span> <span data-ttu-id="dc9f7-111">Jakmile vlákno spuštěného stavu, může způsobit několik akcí změnit stavy.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-111">Once a thread is in the started state, a number of actions can cause it to change states.</span></span> <span data-ttu-id="dc9f7-112">V následující tabulce jsou uvedeny akce, které způsobit změnu stavu, spolu s odpovídající nový stav.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-112">The following table lists the actions that cause a change of state, along with the corresponding new state.</span></span>  
  
|<span data-ttu-id="dc9f7-113">Akce</span><span class="sxs-lookup"><span data-stu-id="dc9f7-113">Action</span></span>|<span data-ttu-id="dc9f7-114">Výsledný nový stav</span><span class="sxs-lookup"><span data-stu-id="dc9f7-114">Resulting new state</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="dc9f7-115">V konstruktoru pro <xref:System.Threading.Thread> třídy se nazývá.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-115">The constructor for the <xref:System.Threading.Thread> class is called.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="dc9f7-116">Jiné vlákno volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-116">Another thread calls <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="dc9f7-117">Vlákno odpoví na <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> a spuštění.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-117">The thread responds to <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> and starts running.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="dc9f7-118">Přístup z více vláken volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-118">The thread calls <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="dc9f7-119">Přístup z více vláken volání <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> na jiném objektu.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-119">The thread calls <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> on another object.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="dc9f7-120">Přístup z více vláken volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-120">The thread calls <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> on another thread.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="dc9f7-121">Jiné vlákno volání <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-121">Another thread calls <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.SuspendRequested>|  
|<span data-ttu-id="dc9f7-122">Vlákno odpoví <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> požadavku.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-122">The thread responds to a <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> request.</span></span>|<xref:System.Threading.ThreadState.Suspended>|  
|<span data-ttu-id="dc9f7-123">Jiné vlákno volání <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-123">Another thread calls <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="dc9f7-124">Jiné vlákno volání <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-124">Another thread calls <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.AbortRequested>|  
|<span data-ttu-id="dc9f7-125">Vlákno odpoví <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-125">The thread responds to an <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<span data-ttu-id="dc9f7-126"><xref:System.Threading.ThreadState.Aborted>, pak<xref:System.Threading.ThreadState.Stopped></span><span class="sxs-lookup"><span data-stu-id="dc9f7-126"><xref:System.Threading.ThreadState.Aborted>, then <xref:System.Threading.ThreadState.Stopped></span></span>|  
  
 <span data-ttu-id="dc9f7-127">Protože <xref:System.Threading.ThreadState.Running> stavu má hodnotu 0, není možné provést bit test ke zjištění tento stav.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-127">Because the <xref:System.Threading.ThreadState.Running> state has a value of 0, it is not possible to perform a bit test to discover this state.</span></span> <span data-ttu-id="dc9f7-128">Místo toho se dají použít následující testovací (v pseudo kód):</span><span class="sxs-lookup"><span data-stu-id="dc9f7-128">Instead, the following test (in pseudo-code) can be used:</span></span>  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 <span data-ttu-id="dc9f7-129">Vlákna jsou ve více než jeden stavu v každém okamžiku často.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-129">Threads are often in more than one state at any given time.</span></span> <span data-ttu-id="dc9f7-130">Například, pokud vlákno je na zablokovaný <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> volání a jiného vlákna volání <xref:System.Threading.Thread.Abort%2A> v daném vláknu stejné vlákno bude v obou <xref:System.Threading.ThreadState.WaitSleepJoin> a <xref:System.Threading.ThreadState.AbortRequested> stavy ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-130">For example, if a thread is blocked on a <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> call and another thread calls <xref:System.Threading.Thread.Abort%2A> on that same thread, the thread will be in both the <xref:System.Threading.ThreadState.WaitSleepJoin> and the <xref:System.Threading.ThreadState.AbortRequested> states at the same time.</span></span> <span data-ttu-id="dc9f7-131">V takovém případě také vlákno vrátí z volání <xref:System.Threading.Monitor.Wait%2A> nebo přerušit, se zobrazí <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-131">In that case, as soon as the thread returns from the call to <xref:System.Threading.Monitor.Wait%2A> or is interrupted, it will receive the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 <span data-ttu-id="dc9f7-132">Jakmile opustí vlákna <xref:System.Threading.ThreadState.Unstarted> stavu v důsledku volání <xref:System.Threading.Thread.Start%2A>, se nikdy může vrátit do <xref:System.Threading.ThreadState.Unstarted> stavu.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-132">Once a thread leaves the <xref:System.Threading.ThreadState.Unstarted> state as the result of a call to <xref:System.Threading.Thread.Start%2A>, it can never return to the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="dc9f7-133">Vlákno můžete nikdy neopustí <xref:System.Threading.ThreadState.Stopped> stavu.</span><span class="sxs-lookup"><span data-stu-id="dc9f7-133">A thread can never leave the <xref:System.Threading.ThreadState.Stopped> state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9f7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc9f7-134">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [<span data-ttu-id="dc9f7-135">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="dc9f7-135">Threading</span></span>](../../../docs/standard/threading/index.md)
