---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 628d6a96606117d447c61d01595d13dd4a957ce4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138114"
---
# <a name="countdownevent"></a><span data-ttu-id="d7711-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="d7711-102">CountdownEvent</span></span>
<span data-ttu-id="d7711-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>je synchronizační primitiv, který odblokuje jeho čekající vlákna poté, co byla signalizována určitý počet opakování.</span><span class="sxs-lookup"><span data-stu-id="d7711-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="d7711-104"><xref:System.Threading.CountdownEvent>je určen pro scénáře, ve kterých <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim> byste jinak museli použít nebo nebo ručně dekrement proměnné před signalizací události.</span><span class="sxs-lookup"><span data-stu-id="d7711-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="d7711-105">Například ve scénáři rozteč/spojení můžete <xref:System.Threading.CountdownEvent> pouze vytvořit, který má počet signálů 5 a potom spustit pět <xref:System.Threading.CountdownEvent.Signal%2A> pracovních položek ve fondu vláken a mít každé volání pracovní položky po dokončení.</span><span class="sxs-lookup"><span data-stu-id="d7711-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="d7711-106">Každé volání <xref:System.Threading.CountdownEvent.Signal%2A> sníží počet signálů o 1.</span><span class="sxs-lookup"><span data-stu-id="d7711-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="d7711-107">V hlavním vlákně <xref:System.Threading.CountdownEvent.Wait%2A> bude volání blokovat, dokud nebude počet signálů nula.</span><span class="sxs-lookup"><span data-stu-id="d7711-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7711-108">Pro kód, který nemusí pracovat se staršími rozhraními API <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> synchronizace <xref:System.Threading.Tasks.Parallel.Invoke%2A> rozhraní .NET Framework, zvažte použití objektů nebo metody pro ještě snadnější přístup k vyjádření paralelismu spojení vložky.</span><span class="sxs-lookup"><span data-stu-id="d7711-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="d7711-109"><xref:System.Threading.CountdownEvent>má tyto další funkce:</span><span class="sxs-lookup"><span data-stu-id="d7711-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="d7711-110">Operace čekání může být zrušena pomocí tokenů zrušení.</span><span class="sxs-lookup"><span data-stu-id="d7711-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="d7711-111">Jeho počet signálu může být po vytvoření instance zpřísněn.</span><span class="sxs-lookup"><span data-stu-id="d7711-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="d7711-112">Instance lze znovu použít <xref:System.Threading.CountdownEvent.Wait%2A> po vrácené <xref:System.Threading.CountdownEvent.Reset%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="d7711-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="d7711-113">Instance vystavit <xref:System.Threading.WaitHandle> pro integraci s jinými rozhraní mise <xref:System.Threading.WaitHandle.WaitAll%2A>.NET Framework synchronizace rozhraní API, jako je například .</span><span class="sxs-lookup"><span data-stu-id="d7711-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="d7711-114">Základní použití</span><span class="sxs-lookup"><span data-stu-id="d7711-114">Basic Usage</span></span>  
 <span data-ttu-id="d7711-115">Následující příklad ukazuje, jak <xref:System.Threading.CountdownEvent> používat <xref:System.Threading.ThreadPool> s pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="d7711-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="d7711-116">CountdownEvent se zrušením</span><span class="sxs-lookup"><span data-stu-id="d7711-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="d7711-117">Následující příklad ukazuje, jak zrušit <xref:System.Threading.CountdownEvent> operaci čekání na pomocí tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="d7711-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="d7711-118">Základní vzor následuje model pro jednotné zrušení, který je zaveden v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7711-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="d7711-119">Další informace naleznete [v tématu Zrušení v tématu Spravovaná vlákna](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="d7711-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="d7711-120">Všimněte si, že operace čekání nezruší podprocesy, které jsou signalizace.</span><span class="sxs-lookup"><span data-stu-id="d7711-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="d7711-121">Obvykle zrušení se použije na logické operace a to může zahrnovat čekání na událost, stejně jako všechny pracovní položky, které čekání synchronizuje.</span><span class="sxs-lookup"><span data-stu-id="d7711-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="d7711-122">V tomto příkladu je každé pracovní položce předána kopie stejného tokenu zrušení tak, aby mohla reagovat na požadavek na zrušení.</span><span class="sxs-lookup"><span data-stu-id="d7711-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7711-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7711-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
