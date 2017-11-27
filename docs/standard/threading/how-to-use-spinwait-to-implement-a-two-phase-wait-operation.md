---
title: "Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="95082-102">Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání</span><span class="sxs-lookup"><span data-stu-id="95082-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="95082-103">Následující příklad ukazuje, jak používat <xref:System.Threading.SpinWait?displayProperty=nameWithType> objektu k implementaci dvoufázové operace čekání.</span><span class="sxs-lookup"><span data-stu-id="95082-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="95082-104">V první fázi objekt synchronizace `Latch`, otáčí po několik cyklů při zkontroluje, jestli má k dispozici zámek.</span><span class="sxs-lookup"><span data-stu-id="95082-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="95082-105">V druhé fázi, pokud zámek k dispozici pak se `Wait` metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> čekání; provést, jinak hodnota `Wait` provádí čekání.</span><span class="sxs-lookup"><span data-stu-id="95082-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95082-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="95082-106">Example</span></span>  
 <span data-ttu-id="95082-107">Tento příklad ukazuje velmi základní implementace synchronizace západky primitivní.</span><span class="sxs-lookup"><span data-stu-id="95082-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="95082-108">Tato struktura dat můžete použít při očekávané velmi krátké době čekání.</span><span class="sxs-lookup"><span data-stu-id="95082-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="95082-109">V tomto příkladu je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="95082-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="95082-110">Pokud budete potřebovat západkou typu funkce v programu, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95082-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="95082-111">Používá zámek <xref:System.Threading.SpinWait> objekt, který chcete číselníku zavedené pouze do další volání `SpinOnce` způsobí, že <xref:System.Threading.SpinWait> k yield časového intervalu vlákna.</span><span class="sxs-lookup"><span data-stu-id="95082-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="95082-112">V tomto bodě zámek způsobí vlastní přepnutí kontextu voláním <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> a předání ve zbývající části hodnoty časového limitu.</span><span class="sxs-lookup"><span data-stu-id="95082-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="95082-113">Protokolování výstupu ukazuje, jak často se zámek a zvyšuje výkon získávání zámek bez použití <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="95082-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95082-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="95082-114">See Also</span></span>  
 [<span data-ttu-id="95082-115">Objektu SpinWait</span><span class="sxs-lookup"><span data-stu-id="95082-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="95082-116">Dělení na vlákna objektů a funkcí</span><span class="sxs-lookup"><span data-stu-id="95082-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
