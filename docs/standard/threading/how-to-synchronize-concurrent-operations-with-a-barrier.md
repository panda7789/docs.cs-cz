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
ms.openlocfilehash: 2e13dfb277807eb0a9f256f74c2845f5a4d2a047
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279294"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="cf407-102">Postupy: Synchronizace souběh operací pomocí bariéry</span><span class="sxs-lookup"><span data-stu-id="cf407-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="cf407-103">Následující příklad ukazuje, jak synchronizovat souběžné úlohy s <xref:System.Threading.Barrier> .</span><span class="sxs-lookup"><span data-stu-id="cf407-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf407-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf407-104">Example</span></span>  
 <span data-ttu-id="cf407-105">Účelem následujícího programu je zjistit, kolik iterací (nebo fází) se vyžaduje pro dvě vlákna při hledání jejich poloviny řešení ve stejné fázi pomocí náhodného algoritmu k opakovanému rozmísení slov.</span><span class="sxs-lookup"><span data-stu-id="cf407-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="cf407-106">Poté, co každé vlákno přeruší svá slova, porovná operace po fázi povýšení těchto dvou výsledků, aby bylo možné zjistit, zda byla úplná věta vykreslena ve správném textovém pořadí.</span><span class="sxs-lookup"><span data-stu-id="cf407-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="cf407-107">A <xref:System.Threading.Barrier> je objekt, který brání jednotlivým úlohám v paralelní operaci pokračovat, dokud všechny úlohy nedosáhnou bariéry.</span><span class="sxs-lookup"><span data-stu-id="cf407-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="cf407-108">Je užitečné v případě, že dojde k paralelní operaci ve fázích a každá fáze vyžaduje synchronizaci mezi úlohami.</span><span class="sxs-lookup"><span data-stu-id="cf407-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="cf407-109">V tomto příkladu existují dvě fáze operace.</span><span class="sxs-lookup"><span data-stu-id="cf407-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="cf407-110">V první fázi každý úkol vyplní svou část vyrovnávací paměti daty.</span><span class="sxs-lookup"><span data-stu-id="cf407-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="cf407-111">Když každý úkol dokončí vyplňování oddílu, úloha signalizuje bariéru, že je připravená k pokračování, a potom počká.</span><span class="sxs-lookup"><span data-stu-id="cf407-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="cf407-112">Když všechny úlohy signalizují bariéru, odblokuje se a druhá fáze se spustí.</span><span class="sxs-lookup"><span data-stu-id="cf407-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="cf407-113">Bariéra je nezbytná, protože druhá fáze vyžaduje, aby každý úkol měl přístup ke všem datům, která byla vygenerována do tohoto bodu.</span><span class="sxs-lookup"><span data-stu-id="cf407-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="cf407-114">Bez bariéry se může první dokončený úkol pokusit přečíst z vyrovnávacích pamětí, které ještě nejsou vyplněné jinými úkoly.</span><span class="sxs-lookup"><span data-stu-id="cf407-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="cf407-115">Tímto způsobem můžete synchronizovat libovolný počet fází.</span><span class="sxs-lookup"><span data-stu-id="cf407-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf407-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf407-116">See also</span></span>

- [<span data-ttu-id="cf407-117">Datové struktury pro paralelní programování</span><span class="sxs-lookup"><span data-stu-id="cf407-117">Data Structures for Parallel Programming</span></span>](../parallel-programming/data-structures-for-parallel-programming.md)
