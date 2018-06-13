---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6262822e0916e142c7c543d2e2546c8540cb73a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568573"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="30444-102">Postupy: Přidání funkcí ohraničování a blokování do kolekce</span><span class="sxs-lookup"><span data-stu-id="30444-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="30444-103">Tento příklad ukazuje postup přidání funkcí ohraničování a blokování do vlastní kolekce třídy implementací <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> rozhraní ve třídě a pak pomocí instance třídy jako mechanismus pro interní úložiště <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30444-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="30444-104">Další informace o funkcí ohraničování a blokování najdete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="30444-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30444-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="30444-105">Example</span></span>  
 <span data-ttu-id="30444-106">Třída vlastní kolekce je základní prioritou fronty, ve kterém jsou úroveň priority vyjádřené pole <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objekty.</span><span class="sxs-lookup"><span data-stu-id="30444-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="30444-107">Žádné další řazení se provádí v rámci každé fronty.</span><span class="sxs-lookup"><span data-stu-id="30444-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="30444-108">V kódu klienta tři úlohy spustí.</span><span class="sxs-lookup"><span data-stu-id="30444-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="30444-109">První úlohou právě zjišťuje klávesnice tahy povolit zrušení kdykoli během provádění.</span><span class="sxs-lookup"><span data-stu-id="30444-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="30444-110">V druhé úloze je proto, že vlákno; Přidá nové položky blokující kolekce a poskytuje každou položku prioritu podle náhodná hodnota.</span><span class="sxs-lookup"><span data-stu-id="30444-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="30444-111">Třetí úloh odebere položky z kolekce, jakmile budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="30444-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="30444-112">Chování aplikace můžete upravit tak, že některé z vláken rychleji probíhají rychleji než ostatní.</span><span class="sxs-lookup"><span data-stu-id="30444-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="30444-113">Pokud autor rychleji spustí, si všimnete funkci ohraničující blokující kolekce brání položky přidání Pokud již obsahuje počet položek, který je uveden v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="30444-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="30444-114">Pokud se příjemce rychleji spustí, si všimnete blokování funkce jako příjemce čeká na novou položku Přidat.</span><span class="sxs-lookup"><span data-stu-id="30444-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="30444-115">Ve výchozím nastavení úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> je <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30444-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30444-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="30444-116">See Also</span></span>  
 [<span data-ttu-id="30444-117">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="30444-117">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
