---
title: 'Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137939"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="07c2c-102">Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání</span><span class="sxs-lookup"><span data-stu-id="07c2c-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="07c2c-103">Následující příklad ukazuje, jak <xref:System.Threading.SpinWait?displayProperty=nameWithType> použít objekt k implementaci dvoufázové operace čekání.</span><span class="sxs-lookup"><span data-stu-id="07c2c-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="07c2c-104">V první fázi, objekt synchronizace `Latch`, se točí po dobu několika cyklů, zatímco zkontroluje, zda zámek je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="07c2c-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="07c2c-105">Ve druhé fázi, pokud zámek k `Wait` dispozici, pak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> metoda vrátí bez použití provést jeho čekání; v `Wait` opačném případě provede čekání.</span><span class="sxs-lookup"><span data-stu-id="07c2c-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c2c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="07c2c-106">Example</span></span>  
 <span data-ttu-id="07c2c-107">Tento příklad ukazuje velmi základní implementaci primitivní synchronizace zámku.</span><span class="sxs-lookup"><span data-stu-id="07c2c-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="07c2c-108">Tuto datovou strukturu můžete použít, když se očekává, že čekací doby budou velmi krátké.</span><span class="sxs-lookup"><span data-stu-id="07c2c-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="07c2c-109">Tento příklad je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="07c2c-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="07c2c-110">Pokud v programu požadujete funkci typu zámku, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>aplikace .</span><span class="sxs-lookup"><span data-stu-id="07c2c-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="07c2c-111">Západka používá <xref:System.Threading.SpinWait> objekt točit na místě pouze `SpinOnce` do <xref:System.Threading.SpinWait> další volání způsobí, že výnos časový úsek vlákna.</span><span class="sxs-lookup"><span data-stu-id="07c2c-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="07c2c-112">V tomto okamžiku západka způsobí vlastní <xref:System.Threading.WaitHandle.WaitOne%2A> přepínač <xref:System.Threading.ManualResetEvent> kontextu voláním a předání mj.</span><span class="sxs-lookup"><span data-stu-id="07c2c-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="07c2c-113">Výstup protokolování ukazuje, jak často západka byla schopna zvýšit <xref:System.Threading.ManualResetEvent>výkon získáním zámku bez použití .</span><span class="sxs-lookup"><span data-stu-id="07c2c-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c2c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="07c2c-114">See also</span></span>

- [<span data-ttu-id="07c2c-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="07c2c-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="07c2c-116">Objekty a prvky zřetězení</span><span class="sxs-lookup"><span data-stu-id="07c2c-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
