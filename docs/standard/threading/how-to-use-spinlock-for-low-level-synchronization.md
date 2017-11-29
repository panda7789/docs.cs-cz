---
title: "Postupy: Použití SpinLock pro synchronizaci nízké úrovně"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="a0b3c-102">Postupy: Použití SpinLock pro synchronizaci nízké úrovně</span><span class="sxs-lookup"><span data-stu-id="a0b3c-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="a0b3c-103">Následující příklad ukazuje, jak používat <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b3c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0b3c-104">Example</span></span>  
 <span data-ttu-id="a0b3c-105">V tomto příkladu kritická sekce provede minimální množství práce, což usnadňuje vhodným kandidátem <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="a0b3c-106">Zvýšení práce malou zvyšuje výkon <xref:System.Threading.SpinLock> ve srovnání s standardní zámku.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="a0b3c-107">Je však bod, ve kterém bude SpinLock dražší než standardní zámku.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="a0b3c-108">Profilace funkce v nástrojích pro profilaci souběžného zpracování můžete zobrazit, jaký typ zámku poskytuje lepší výkon v programu.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="a0b3c-109">Další informace najdete v tématu [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="a0b3c-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="a0b3c-110"><xref:System.Threading.SpinLock>můžou být užitečné při uzamčení sdíleného prostředku není budete mít velmi náročná.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="a0b3c-111">V takových případech na počítačích s více jádry může být efektivní pro blokované vlákno k číselníku po několik cyklů, dokud se uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="a0b3c-112">Podle roztočený, vlákno stane neblokován, což je proces náročná na prostředky procesoru.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="a0b3c-113"><xref:System.Threading.SpinLock>Zastaví roztočený za určitých podmínek, aby se zabránilo nedostatku prostředků logických procesorů nebo v inverzi priority na systémy s technologií Hyper-Threading.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="a0b3c-114">Tento příklad používá <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třídy, která vyžaduje synchronizaci uživatelů pro vícevláknové přístup.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="a0b3c-115">V aplikacích, které cílí na rozhraní .NET Framework verze 4, Další možností je použít <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, který nevyžaduje žádné uživatele zámky.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="a0b3c-116">Všimněte si použití `false` (`False` v jazyce Visual Basic) ve volání <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="a0b3c-117">To poskytuje nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-117">This provides the best performance.</span></span> <span data-ttu-id="a0b3c-118">Zadejte `true` (`True`) na architektury IA64 používat ochranná paměti, která vyprázdní vyrovnávací paměti zápisu zajistit, že zámek je nyní k dispozici pro další vlákna ukončíte.</span><span class="sxs-lookup"><span data-stu-id="a0b3c-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b3c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0b3c-119">See Also</span></span>  
 [<span data-ttu-id="a0b3c-120">Dělení na vlákna objektů a funkcí</span><span class="sxs-lookup"><span data-stu-id="a0b3c-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
