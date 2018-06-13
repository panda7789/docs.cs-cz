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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af6e4e8d0d754b97478788422b4dd84eeddc6491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583276"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="1bc21-102">Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání</span><span class="sxs-lookup"><span data-stu-id="1bc21-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="1bc21-103">Následující příklad ukazuje, jak používat <xref:System.Threading.SpinWait?displayProperty=nameWithType> objektu k implementaci dvoufázové operace čekání.</span><span class="sxs-lookup"><span data-stu-id="1bc21-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="1bc21-104">V první fázi objekt synchronizace `Latch`, otáčí po několik cyklů při zkontroluje, jestli má k dispozici zámek.</span><span class="sxs-lookup"><span data-stu-id="1bc21-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="1bc21-105">V druhé fázi, pokud zámek k dispozici pak se `Wait` metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> čekání; provést, jinak hodnota `Wait` provádí čekání.</span><span class="sxs-lookup"><span data-stu-id="1bc21-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc21-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bc21-106">Example</span></span>  
 <span data-ttu-id="1bc21-107">Tento příklad ukazuje velmi základní implementace synchronizace západky primitivní.</span><span class="sxs-lookup"><span data-stu-id="1bc21-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="1bc21-108">Tato struktura dat můžete použít při očekávané velmi krátké době čekání.</span><span class="sxs-lookup"><span data-stu-id="1bc21-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="1bc21-109">V tomto příkladu je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="1bc21-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="1bc21-110">Pokud budete potřebovat západkou typu funkce v programu, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bc21-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="1bc21-111">Používá zámek <xref:System.Threading.SpinWait> objekt, který chcete číselníku zavedené pouze do další volání `SpinOnce` způsobí, že <xref:System.Threading.SpinWait> k yield časového intervalu vlákna.</span><span class="sxs-lookup"><span data-stu-id="1bc21-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="1bc21-112">V tomto bodě zámek způsobí vlastní přepnutí kontextu voláním <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> a předání ve zbývající části hodnoty časového limitu.</span><span class="sxs-lookup"><span data-stu-id="1bc21-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="1bc21-113">Protokolování výstupu ukazuje, jak často se zámek a zvyšuje výkon získávání zámek bez použití <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="1bc21-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc21-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bc21-114">See Also</span></span>  
 [<span data-ttu-id="1bc21-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="1bc21-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="1bc21-116">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="1bc21-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
