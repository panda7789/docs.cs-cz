---
title: 'Postupy: Synchronizace souběh operací pomocí bariéry'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972134"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="ec682-102">Postupy: Synchronizace souběh operací pomocí bariéry</span><span class="sxs-lookup"><span data-stu-id="ec682-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="ec682-103">Následující příklad ukazuje, jak synchronizovat souběžné úkoly se <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="ec682-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec682-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec682-104">Example</span></span>  
 <span data-ttu-id="ec682-105">Účelem následující program se mají spočítat, kolik iterací (nebo fáze) jsou vyžadovaných pro dvěma vlákny na každé hledání své polovině řešení v stejné fázi pomocí algoritmu randomizing změnit pořadí slova.</span><span class="sxs-lookup"><span data-stu-id="ec682-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="ec682-106">Po každé vlákno má které se náhodně pomíchají jeho slova, porovnává operaci po fázi barrier dva výsledky zobrazíte, pokud bylo ve správném pořadí slov vykresleno kompletní věta.</span><span class="sxs-lookup"><span data-stu-id="ec682-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="ec682-107">A <xref:System.Threading.Barrier> je objekt, který brání jednotlivé úkoly v rámci paralelní operace pokračovat, dokud všechny úkoly nezobrazí odbourejte překážky bránící.</span><span class="sxs-lookup"><span data-stu-id="ec682-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="ec682-108">To je užitečné, když paralelní operace probíhá ve fázích a jednotlivé fáze vyžaduje synchronizaci mezi úkoly.</span><span class="sxs-lookup"><span data-stu-id="ec682-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="ec682-109">V tomto příkladu existují dvě fáze operace.</span><span class="sxs-lookup"><span data-stu-id="ec682-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="ec682-110">Každý úkol v první fázi, vyplní její části vyrovnávací paměti s daty.</span><span class="sxs-lookup"><span data-stu-id="ec682-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="ec682-111">Když každý úkol dokončí, naplnění jeho části, úloha signály barrier, která bude chtít pokračovat a potom počká.</span><span class="sxs-lookup"><span data-stu-id="ec682-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="ec682-112">Když všechny úlohy mají signalizován bariéry, se odblokuje a spustí druhé fáze.</span><span class="sxs-lookup"><span data-stu-id="ec682-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="ec682-113">Odbourejte překážky bránící je nezbytné, protože druhé fáze vyžaduje, aby každý úkol mají přístup ke všem datům generovaný do tohoto bodu.</span><span class="sxs-lookup"><span data-stu-id="ec682-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="ec682-114">Bez bariéry může první úkoly k dokončení pokusí číst z vyrovnávací paměti, které nebyly byl vyplněn ještě další úkoly.</span><span class="sxs-lookup"><span data-stu-id="ec682-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="ec682-115">Libovolný počet fází tímto způsobem můžete synchronizovat.</span><span class="sxs-lookup"><span data-stu-id="ec682-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec682-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec682-116">See also</span></span>

- [<span data-ttu-id="ec682-117">Datové struktury pro paralelní programování</span><span class="sxs-lookup"><span data-stu-id="ec682-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
