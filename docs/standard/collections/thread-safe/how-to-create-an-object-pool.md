---
title: Vytvoření fondu objektů pomocí ConcurrentBag
ms.date: 05/01/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 64d91162b27eba80fba63761d0a926e441b63440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287858"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="4c1d3-102">Vytvoření fondu objektů pomocí ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="4c1d3-102">Create an object pool by using a ConcurrentBag</span></span>

<span data-ttu-id="4c1d3-103">Tento příklad ukazuje, jak použít <xref:System.Collections.Concurrent.ConcurrentBag%601> k implementaci fondu objektů.</span><span class="sxs-lookup"><span data-stu-id="4c1d3-103">This example shows how to use a <xref:System.Collections.Concurrent.ConcurrentBag%601> to implement an object pool.</span></span> <span data-ttu-id="4c1d3-104">Fondy objektů můžou zlepšit výkon aplikace v situacích, kdy požadujete více instancí třídy a že je třída nenáročná na vytvoření nebo zničení.</span><span class="sxs-lookup"><span data-stu-id="4c1d3-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="4c1d3-105">Když klientský program požádá o nový objekt, fond objektů se nejprve pokusí zadat, který již byl vytvořen a vrácen do fondu.</span><span class="sxs-lookup"><span data-stu-id="4c1d3-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="4c1d3-106">Pokud není k dispozici žádný, je vytvořen nový objekt.</span><span class="sxs-lookup"><span data-stu-id="4c1d3-106">If none is available, only then is a new object created.</span></span>

<span data-ttu-id="4c1d3-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>Slouží k uložení objektů, protože podporuje rychlé vkládání a odebírání, zejména v případě, že stejné vlákno přidává i odebírá položky.</span><span class="sxs-lookup"><span data-stu-id="4c1d3-107">The <xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="4c1d3-108">Tento příklad může být dále rozšířen tak, aby byl sestaven kolem <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> , který implementuje strukturu dat balíčku, jako do <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601> .</span><span class="sxs-lookup"><span data-stu-id="4c1d3-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

> [!TIP]
> <span data-ttu-id="4c1d3-109">Tento článek popisuje, jak napsat vlastní implementaci fondu objektů pomocí základního souběžného typu pro ukládání objektů pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="4c1d3-109">This article defines how to write your own implementation of an object pool with an underlying concurrent type to store objects for reuse.</span></span> <span data-ttu-id="4c1d3-110">Tento typ však <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> v oboru názvů již existuje <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="4c1d3-110">However, the <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type already exists under the <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="4c1d3-111">Zvažte použití dostupného typu před vytvořením vlastní implementace, která zahrnuje mnoho dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="4c1d3-111">Consider using the available type before creating your own implementation, which includes many additional features.</span></span>

## <a name="example"></a><span data-ttu-id="4c1d3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c1d3-112">Example</span></span>

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a><span data-ttu-id="4c1d3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c1d3-113">See also</span></span>

- [<span data-ttu-id="4c1d3-114">Kolekce bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="4c1d3-114">Thread-Safe Collections</span></span>](index.md)
