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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac1f2283ad30499748511e6fed6d5ce98da7fd14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960109"
---
# <a name="countdownevent"></a><span data-ttu-id="fe6c1-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="fe6c1-102">CountdownEvent</span></span>
<span data-ttu-id="fe6c1-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>je primitiva synchronizace, která odblokuje čekající vlákna poté, co byla signalizována určitý počet opakování.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="fe6c1-104"><xref:System.Threading.CountdownEvent>je navržen pro scénáře, ve kterých byste jinak museli před signalizací <xref:System.Threading.ManualResetEventSlim> události použít <xref:System.Threading.ManualResetEvent> nebo ručně snížit proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="fe6c1-105">Například ve scénáři rozvětvení/spojení můžete vytvořit <xref:System.Threading.CountdownEvent> pouze ty, které mají počet signálů 5, a potom spustit pět pracovních položek ve fondu vláken a při dokončení každé pracovní položky zavolat. <xref:System.Threading.CountdownEvent.Signal%2A></span><span class="sxs-lookup"><span data-stu-id="fe6c1-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="fe6c1-106">Každé volání <xref:System.Threading.CountdownEvent.Signal%2A> snižuje počet signálů o 1.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="fe6c1-107">V hlavním vlákně <xref:System.Threading.CountdownEvent.Wait%2A> bude volání zablokováno, dokud není počet signálů nula.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe6c1-108">Pro kód, který nemusí pracovat se staršími rozhraními API pro synchronizaci .NET Framework, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zvažte použití objektů <xref:System.Threading.Tasks.Parallel.Invoke%2A> nebo metody pro snazší snadnější přístup k paralelnímu rozvětvení spojení.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="fe6c1-109"><xref:System.Threading.CountdownEvent>má tyto další funkce:</span><span class="sxs-lookup"><span data-stu-id="fe6c1-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="fe6c1-110">Operaci čekání lze zrušit pomocí tokenů zrušení.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="fe6c1-111">Po vytvoření instance se dá zvýšit počet signálů.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="fe6c1-112">Instance lze znovu použít poté, <xref:System.Threading.CountdownEvent.Wait%2A> co bylo vráceno <xref:System.Threading.CountdownEvent.Reset%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="fe6c1-113">Instance zveřejňují <xref:System.Threading.WaitHandle> integraci s jinými .NET Frameworkmi synchronizačními rozhraními <xref:System.Threading.WaitHandle.WaitAll%2A>API, jako je například.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="fe6c1-114">Základní využití</span><span class="sxs-lookup"><span data-stu-id="fe6c1-114">Basic Usage</span></span>  
 <span data-ttu-id="fe6c1-115">Následující příklad ukazuje, jak použít <xref:System.Threading.CountdownEvent> s <xref:System.Threading.ThreadPool> pracovními položkami.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="fe6c1-116">CountdownEvent s zrušením</span><span class="sxs-lookup"><span data-stu-id="fe6c1-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="fe6c1-117">Následující příklad ukazuje, jak zrušit operaci čekání na <xref:System.Threading.CountdownEvent> pomocí tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="fe6c1-118">Základní vzor následuje model pro sjednocení zrušení, který je představený v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="fe6c1-119">Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="fe6c1-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="fe6c1-120">Všimněte si, že operace wait neruší vlákna, která ji signalizuje.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="fe6c1-121">Zrušení je obvykle použito pro logickou operaci a může zahrnovat čekání na událost a také všechny pracovní položky, které čeká na synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="fe6c1-122">V tomto příkladu je každé pracovní položce předána kopie stejného tokenu zrušení, aby mohla reagovat na žádost o zrušení.</span><span class="sxs-lookup"><span data-stu-id="fe6c1-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6c1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe6c1-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
