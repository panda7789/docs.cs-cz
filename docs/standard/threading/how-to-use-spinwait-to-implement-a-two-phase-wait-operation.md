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
ms.openlocfilehash: dcb2fbf5e0a310156fdc6fac5fe736692e8ec133
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135338"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="350da-102">Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání</span><span class="sxs-lookup"><span data-stu-id="350da-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="350da-103">Následující příklad ukazuje způsob použití <xref:System.Threading.SpinWait?displayProperty=nameWithType> objektu pro implementaci dvoufázové operace čekání.</span><span class="sxs-lookup"><span data-stu-id="350da-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="350da-104">V první fázi synchronizační objekt `Latch`, otáčí pro několik cyklů při kontrole, jestli má zámek k dispozici.</span><span class="sxs-lookup"><span data-stu-id="350da-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="350da-105">Ve druhé fázi, pokud zámek přestane být k dispozici pak bude `Wait` metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> provádět jeho čekání; v opačném případě `Wait` provádí čekání.</span><span class="sxs-lookup"><span data-stu-id="350da-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="350da-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="350da-106">Example</span></span>  
 <span data-ttu-id="350da-107">Tento příklad ukazuje velmi základní implementaci zámek synchronizace primitivní.</span><span class="sxs-lookup"><span data-stu-id="350da-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="350da-108">Tato struktura dat můžete použít při velmi krátké očekávané době čekání.</span><span class="sxs-lookup"><span data-stu-id="350da-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="350da-109">V tomto příkladu je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="350da-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="350da-110">Pokud vyžadujete funkce západkou typu ve svém programu, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="350da-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="350da-111">Používá zámek <xref:System.Threading.SpinWait> objektu, abyste mohli spustit na místě pouze až do příštího volání metody `SpinOnce` způsobí, že <xref:System.Threading.SpinWait> výnosu časovém intervalu vlákna.</span><span class="sxs-lookup"><span data-stu-id="350da-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="350da-112">V tomto okamžiku západku způsobí, že vlastní přepnutí kontextu voláním <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> a předávání do zbývající část hodnoty časového limitu.</span><span class="sxs-lookup"><span data-stu-id="350da-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="350da-113">Protokolování výstupu ukazuje, jak často se podařilo a zvyšuje výkon získání zámku bez použití Zámek <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="350da-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="350da-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="350da-114">See also</span></span>

- [<span data-ttu-id="350da-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="350da-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
- [<span data-ttu-id="350da-116">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="350da-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
