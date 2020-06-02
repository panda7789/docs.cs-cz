---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 57a01726e897f4ddbf8df5ede53609c198012d80
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287871"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="269d1-102">Postupy: Přidání funkcí ohraničování a blokování do kolekce</span><span class="sxs-lookup"><span data-stu-id="269d1-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="269d1-103">Tento příklad ukazuje, jak přidat funkci ohraničování a blokování do vlastní třídy kolekce implementací <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> rozhraní ve třídě a následnou použitím instance třídy jako mechanismu interního úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="269d1-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="269d1-104">Další informace o ohraničování a blokování najdete v tématu [blokujícícollection – přehled](blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="269d1-104">For more information about bounding and blocking, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="269d1-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="269d1-105">Example</span></span>  
 <span data-ttu-id="269d1-106">Vlastní třída kolekce je základní a prioritní frontou, ve které jsou úrovně priority reprezentované jako pole <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objektů.</span><span class="sxs-lookup"><span data-stu-id="269d1-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="269d1-107">V každé frontě se neprovádí žádné další řazení.</span><span class="sxs-lookup"><span data-stu-id="269d1-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="269d1-108">V kódu klienta se spouští tři úkoly.</span><span class="sxs-lookup"><span data-stu-id="269d1-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="269d1-109">První úkol se pouze dotazuje na tahy klávesnice, aby bylo možné zrušit v jakémkoli okamžiku během provádění.</span><span class="sxs-lookup"><span data-stu-id="269d1-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="269d1-110">Druhým úkolem je vlákno producenta; přidává nové položky do blokující kolekce a dává každé položce prioritu na základě náhodné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="269d1-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="269d1-111">Třetí úkol odebere položky z kolekce, jakmile budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="269d1-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="269d1-112">Chování aplikace můžete upravit tak, že jeden z vláken běží rychleji než druhý.</span><span class="sxs-lookup"><span data-stu-id="269d1-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="269d1-113">Pokud producent pracuje rychleji, všimnete si, že funkce pro zablokování brání v přidání položek, pokud již obsahuje počet položek, které jsou zadány v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="269d1-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="269d1-114">Pokud příjemce pracuje rychleji, všimnete si, že funkce blokování přestane být přidána, protože příjemce čeká na přidání nové položky.</span><span class="sxs-lookup"><span data-stu-id="269d1-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="269d1-115">Ve výchozím nastavení je úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="269d1-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269d1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="269d1-116">See also</span></span>

- [<span data-ttu-id="269d1-117">Kolekce bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="269d1-117">Thread-Safe Collections</span></span>](index.md)
