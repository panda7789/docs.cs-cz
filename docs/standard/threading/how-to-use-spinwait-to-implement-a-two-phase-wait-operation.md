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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137939"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="1cd37-102">Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání</span><span class="sxs-lookup"><span data-stu-id="1cd37-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="1cd37-103">Následující příklad ukazuje, jak použít objekt <xref:System.Threading.SpinWait?displayProperty=nameWithType> k implementaci dvoufázové operace čekání.</span><span class="sxs-lookup"><span data-stu-id="1cd37-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="1cd37-104">V první fázi se objekt synchronizace, `Latch`, rozpíná několik cyklů, zatímco kontroluje, zda je zámek k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1cd37-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="1cd37-105">Pokud je zámek k dispozici ve druhé fázi, `Wait` metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> k provedení čekání; v opačném případě `Wait` provede čekání.</span><span class="sxs-lookup"><span data-stu-id="1cd37-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd37-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cd37-106">Example</span></span>  
 <span data-ttu-id="1cd37-107">Tento příklad ukazuje velmi základní implementaci primitiva synchronizace západ.</span><span class="sxs-lookup"><span data-stu-id="1cd37-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="1cd37-108">Tuto datovou strukturu můžete použít, pokud se očekává, že čekací časy budou velmi krátké.</span><span class="sxs-lookup"><span data-stu-id="1cd37-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="1cd37-109">Tento příklad je určen pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="1cd37-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="1cd37-110">Pokud v programu požadujete funkce typu západ, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1cd37-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="1cd37-111">Západ používá objekt <xref:System.Threading.SpinWait> k rozmístění pouze do chvíle, kdy další volání `SpinOnce` způsobí, že <xref:System.Threading.SpinWait> zaznamená časový úsek vlákna.</span><span class="sxs-lookup"><span data-stu-id="1cd37-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="1cd37-112">V tomto okamžiku západ vyvolá svůj vlastní kontextový přepínač voláním <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> a předáním zbývající část hodnoty časového limitu.</span><span class="sxs-lookup"><span data-stu-id="1cd37-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="1cd37-113">Výstup protokolování ukazuje, jak často byla západ moci zvýšit výkon tím, že získá zámek bez použití <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="1cd37-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd37-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1cd37-114">See also</span></span>

- [<span data-ttu-id="1cd37-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="1cd37-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="1cd37-116">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="1cd37-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
