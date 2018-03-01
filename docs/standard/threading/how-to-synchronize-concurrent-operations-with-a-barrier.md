---
title: "Postupy: Synchronizace souběh operací pomocí bariéry"
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
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 616229abed93c6793b392724d038d8f9160cd6ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="6f3b8-102">Postupy: Synchronizace souběh operací pomocí bariéry</span><span class="sxs-lookup"><span data-stu-id="6f3b8-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="6f3b8-103">Následující příklad ukazuje, jak synchronizovat souběžné úlohy s <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f3b8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f3b8-104">Example</span></span>  
 <span data-ttu-id="6f3b8-105">Účelem následující program je počítat se jak velký počet iterací (nebo fáze) vyžadovaných pro dvěma vlákny na každý najít jejich polovině řešení v fázi stejné pomocí randomizing algoritmus Chcete-li změnit pořadí slova.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="6f3b8-106">Po každé vlákno je na nesprávním místě jeho slova, porovná operaci po fáze bariéry oba výsledky, které chcete zobrazit, pokud bylo ve správném pořadí word vykresleno kompletní věta.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="6f3b8-107">A <xref:System.Threading.Barrier> je objekt, který brání jednotlivé úkoly v rámci paralelní operace pokračovat, dokud všechny úlohy nezobrazí bariéry.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="6f3b8-108">Je užitečná při paralelní operace probíhá ve fázích a jednotlivé fáze vyžaduje synchronizaci mezi úkoly.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="6f3b8-109">V tomto příkladu jsou dvě fáze pro operaci.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="6f3b8-110">Každý úkol v první fázi doplní jeho části vyrovnávací paměti s daty.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="6f3b8-111">Když každý úkol dokončí naplnění jeho části, úloha signály bariéry, který je připraven k pokračovat a potom počká.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="6f3b8-112">Pokud všechny úlohy mají signalizovala bariéry, jsou odblokuje a spustí druhé fáze.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="6f3b8-113">Bariéry je nutné, protože druhé fáze vyžaduje, aby každý úkol měl přístup ke všem datům, která byla vygenerována k tomuto bodu.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="6f3b8-114">Bez bariéry může první na dokončení úloh pokusit číst z vyrovnávací paměti, které nebyly vyplněno ještě další věci.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="6f3b8-115">Můžete synchronizovat libovolný počet fáze tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="6f3b8-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3b8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f3b8-116">See Also</span></span>  
 [<span data-ttu-id="6f3b8-117">Datové struktury pro paralelní programování</span><span class="sxs-lookup"><span data-stu-id="6f3b8-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
