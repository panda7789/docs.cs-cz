---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f52d1067a8aa907c8f1cf8b550eec82d1133b3f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881168"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="15320-102">Postupy: Přidání funkcí ohraničování a blokování do kolekce</span><span class="sxs-lookup"><span data-stu-id="15320-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="15320-103">Tento příklad ukazuje, jak k přidání funkcí ohraničování a blokování do vlastní třídu kolekce implementací <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> rozhraní ve třídě a pak pomocí instance třídy jako mechanismus pro interní úložiště <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="15320-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="15320-104">Další informace o funkcí ohraničování a blokování najdete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="15320-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15320-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="15320-105">Example</span></span>  
 <span data-ttu-id="15320-106">Vlastní kolekce třída je základní prioritní fronty, do které úrovně priority jsou reprezentovány ve formě pole <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objekty.</span><span class="sxs-lookup"><span data-stu-id="15320-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="15320-107">Žádné další řazení se provádí v rámci jednotlivých front.</span><span class="sxs-lookup"><span data-stu-id="15320-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="15320-108">Tři úkoly jsou spuštěny v kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="15320-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="15320-109">První úkol právě dotazuje tahy klávesnice k povolení zrušení kdykoli během provádění.</span><span class="sxs-lookup"><span data-stu-id="15320-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="15320-110">Druhá úloha je výrobce podprocesu. Přidá nové položky do blokující kolekce a poskytuje prioritu na základě náhodné hodnoty každé položky.</span><span class="sxs-lookup"><span data-stu-id="15320-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="15320-111">Třetí úloha odebere položky z kolekce, jakmile budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="15320-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="15320-112">Chování aplikace můžete upravit tak, že jedno z vláken rychleji než ten druhý.</span><span class="sxs-lookup"><span data-stu-id="15320-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="15320-113">Pokud výrobce běží rychleji, si všimnete ohraničující funkce blokující kolekce zabraňuje přidávání Pokud již obsahuje počet položek, která je určená v konstruktoru položky.</span><span class="sxs-lookup"><span data-stu-id="15320-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="15320-114">Pokud takový příjemce běží rychleji, můžete si všimnout, blokování funkce jako příjemce čeká na nové položky, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="15320-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="15320-115">Ve výchozím nastavení úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> je <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="15320-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15320-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15320-116">See also</span></span>

- [<span data-ttu-id="15320-117">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="15320-117">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
