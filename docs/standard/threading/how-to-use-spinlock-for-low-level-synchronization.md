---
title: 'Postupy: použití SpinLock nízké úrovně synchronizace'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff604b94ecef1ffec5fe9845df7c5ba35f5857d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934430"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="d01a2-102">Postupy: použití SpinLock nízké úrovně synchronizace</span><span class="sxs-lookup"><span data-stu-id="d01a2-102">How to: use SpinLock for low-level synchronization</span></span>

<span data-ttu-id="d01a2-103">Následující příklad ukazuje, jak používat <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="d01a2-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="d01a2-104">V tomto příkladu kritický oddíl provádí minimální množství práce, je vhodným kandidátem pro <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="d01a2-104">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="d01a2-105">Zvýšení práce s krátkým zvyšuje výkon <xref:System.Threading.SpinLock> oproti standardní zámku.</span><span class="sxs-lookup"><span data-stu-id="d01a2-105">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="d01a2-106">Je však bod, ve kterém bude dražší než standardní zámek struktuře SpinLock.</span><span class="sxs-lookup"><span data-stu-id="d01a2-106">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="d01a2-107">Pokud chcete zobrazit, jaký typ zámku poskytuje lepší výkon ve svém programu můžete použít funkce v nástrojích pro profilaci profilace souběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="d01a2-107">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="d01a2-108">Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="d01a2-108">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="d01a2-109"><xref:System.Threading.SpinLock> můžou být užitečné při zámek sdíleného prostředku není budete mít velmi dlouho.</span><span class="sxs-lookup"><span data-stu-id="d01a2-109"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="d01a2-110">V takových případech na vícejádrových počítačích může být efektivnější blokovaná vlákna aktivovat pro několik cyklů, dokud se zámek je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="d01a2-110">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="d01a2-111">Která umožňuje, vlákno není stát blokované, což je proces náročnou na procesor.</span><span class="sxs-lookup"><span data-stu-id="d01a2-111">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="d01a2-112"><xref:System.Threading.SpinLock> pokryjte za určitých podmínek, aby se zabránilo starvation logických procesorů nebo inverzi priority v systémech s technologií Hyper-Threading se zastaví.</span><span class="sxs-lookup"><span data-stu-id="d01a2-112"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="d01a2-113">V tomto příkladu <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třídy, které vyžaduje synchronizaci uživatelů pro vícevláknový přístup.</span><span class="sxs-lookup"><span data-stu-id="d01a2-113">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="d01a2-114">V aplikacích, které jsou cíleny rozhraní .NET Framework verze 4, Další možností je použít <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, který nevyžaduje žádné uzamčení uživatele.</span><span class="sxs-lookup"><span data-stu-id="d01a2-114">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="d01a2-115">Všimněte si použití `false` (`False` v jazyce Visual Basic) při volání funkce <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d01a2-115">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d01a2-116">To poskytuje nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="d01a2-116">This provides the best performance.</span></span> <span data-ttu-id="d01a2-117">Zadejte `true` (`True` v jazyce Visual Basic) na architektury IA64 používat ohrazení paměti, která vyprázdní vyrovnávací paměti zápis k zajištění, že zámek je teď k dispozici pro ostatní vlákna ukončíte.</span><span class="sxs-lookup"><span data-stu-id="d01a2-117">Specify `true` (`True` in Visual Basic) on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01a2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d01a2-118">See also</span></span>

- [<span data-ttu-id="d01a2-119">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="d01a2-119">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="d01a2-120">Lock – příkaz (C#)</span><span class="sxs-lookup"><span data-stu-id="d01a2-120">lock statement (C#)</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
- [<span data-ttu-id="d01a2-121">SyncLock – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d01a2-121">SyncLock statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/synclock-statement.md)
