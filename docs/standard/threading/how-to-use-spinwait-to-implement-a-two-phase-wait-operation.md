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
ms.openlocfilehash: 4b2bc79a7b652c34334d5a78d9c9af328993ff44
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279203"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="3758f-102">Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání</span><span class="sxs-lookup"><span data-stu-id="3758f-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="3758f-103">Následující příklad ukazuje, jak použít <xref:System.Threading.SpinWait?displayProperty=nameWithType> objekt k implementaci dvoufázové operace čekání.</span><span class="sxs-lookup"><span data-stu-id="3758f-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="3758f-104">V první fázi se synchronizační objekt, a `Latch` , se rozpíná za několik cyklů, zatímco kontroluje, zda je zámek k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3758f-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="3758f-105">Ve druhé fázi, pokud je zámek k dispozici, pak `Wait` Metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> k provedení čekání; v opačném případě `Wait` provede čekání.</span><span class="sxs-lookup"><span data-stu-id="3758f-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3758f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3758f-106">Example</span></span>  
 <span data-ttu-id="3758f-107">Tento příklad ukazuje velmi základní implementaci primitiva synchronizace západ.</span><span class="sxs-lookup"><span data-stu-id="3758f-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="3758f-108">Tuto datovou strukturu můžete použít, pokud se očekává, že čekací časy budou velmi krátké.</span><span class="sxs-lookup"><span data-stu-id="3758f-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="3758f-109">Tento příklad je určen pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="3758f-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="3758f-110">Pokud v programu požadujete funkce typu západ, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3758f-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="3758f-111">Západku používá <xref:System.Threading.SpinWait> objekt k rozmístění pouze do dalšího volání, které způsobí, že by se vyvolal `SpinOnce` <xref:System.Threading.SpinWait> časový úsek vlákna.</span><span class="sxs-lookup"><span data-stu-id="3758f-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="3758f-112">V tomto okamžiku západ vyvolá svůj vlastní kontextový přepínač voláním metody <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.ManualResetEvent> a procházející zbytkem hodnoty časového limitu.</span><span class="sxs-lookup"><span data-stu-id="3758f-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="3758f-113">Výstup protokolování ukazuje, jak často bylo západ moci zvýšit výkon tím, že získá zámek bez použití <xref:System.Threading.ManualResetEvent> .</span><span class="sxs-lookup"><span data-stu-id="3758f-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3758f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3758f-114">See also</span></span>

- [<span data-ttu-id="3758f-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="3758f-115">SpinWait</span></span>](spinwait.md)
- [<span data-ttu-id="3758f-116">Dělení objektů a funkcí</span><span class="sxs-lookup"><span data-stu-id="3758f-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)
