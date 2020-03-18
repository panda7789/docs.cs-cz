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
ms.openlocfilehash: 33098878764c2f8a8c1f83a122028da40b984243
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137965"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="90e2d-102">Postupy: Synchronizace souběh operací pomocí bariéry</span><span class="sxs-lookup"><span data-stu-id="90e2d-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="90e2d-103">Následující příklad ukazuje, jak synchronizovat <xref:System.Threading.Barrier>souběžné úkoly s aplikací .</span><span class="sxs-lookup"><span data-stu-id="90e2d-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90e2d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="90e2d-104">Example</span></span>  
 <span data-ttu-id="90e2d-105">Účelem následujícího programu je spočítat, kolik iterací (nebo fází) je vyžadováno pro dvě vlákna, aby každá z nich našla svou polovinu řešení ve stejné fázi pomocí randomizačního algoritmu pro opětovné uspořádání slov.</span><span class="sxs-lookup"><span data-stu-id="90e2d-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="90e2d-106">Poté, co každé vlákno zamíchá svá slova, bariéra po fázové operaci porovná dva výsledky, aby zjistila, zda byla celá věta vykreslena ve správném pořadí slov.</span><span class="sxs-lookup"><span data-stu-id="90e2d-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="90e2d-107">A <xref:System.Threading.Barrier> je objekt, který zabraňuje pokračování jednotlivých úloh v paralelní operaci, dokud všechny úkoly nedosáhnou bariéry.</span><span class="sxs-lookup"><span data-stu-id="90e2d-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="90e2d-108">Je užitečné, když paralelní operace probíhá ve fázích a každá fáze vyžaduje synchronizaci mezi úkoly.</span><span class="sxs-lookup"><span data-stu-id="90e2d-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="90e2d-109">V tomto příkladu existují dvě fáze operace.</span><span class="sxs-lookup"><span data-stu-id="90e2d-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="90e2d-110">V první fázi každý úkol vyplní svou část vyrovnávací paměti daty.</span><span class="sxs-lookup"><span data-stu-id="90e2d-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="90e2d-111">Po dokončení plnění každého úkolu úloha signalizuje bariéru, že je připravena pokračovat, a poté čeká.</span><span class="sxs-lookup"><span data-stu-id="90e2d-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="90e2d-112">Když všechny úkoly signalizovaly bariéru, jsou odblokovány a druhá fáze začíná.</span><span class="sxs-lookup"><span data-stu-id="90e2d-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="90e2d-113">Bariéra je nezbytná, protože druhá fáze vyžaduje, aby každý úkol měl přístup ke všem datům, která byla do tohoto okamžiku vygenerována.</span><span class="sxs-lookup"><span data-stu-id="90e2d-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="90e2d-114">Bez bariéry první úkoly k dokončení může pokusit číst z vyrovnávacích pamětí, které nebyly vyplněny ještě jiné úkoly.</span><span class="sxs-lookup"><span data-stu-id="90e2d-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="90e2d-115">Tímto způsobem můžete synchronizovat libovolný počet fází.</span><span class="sxs-lookup"><span data-stu-id="90e2d-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e2d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="90e2d-116">See also</span></span>

- [<span data-ttu-id="90e2d-117">Datové struktury pro paralelní programování</span><span class="sxs-lookup"><span data-stu-id="90e2d-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
