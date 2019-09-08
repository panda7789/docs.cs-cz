---
title: Vzdálené vs. místní spuštění
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a21d5bbffdb1a78d3062929a1ca384a750af59a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781166"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="e150f-102">Vzdálené vs. místní spuštění</span><span class="sxs-lookup"><span data-stu-id="e150f-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="e150f-103">Můžete se rozhodnout spustit dotazy buď vzdáleně (to znamená, že databázový stroj provede dotaz na databázi) nebo lokálně ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí dotaz na místní mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="e150f-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="e150f-104">Vzdálené spuštění</span><span class="sxs-lookup"><span data-stu-id="e150f-104">Remote Execution</span></span>  
 <span data-ttu-id="e150f-105">Vezměte v úvahu následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="e150f-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="e150f-106">Pokud má vaše databáze tisíce řádků objednávek, nechcete je načíst pro zpracování malé podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="e150f-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="e150f-107">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ,<xref:System.Data.Linq.EntitySet%601> třída implementuje<xref:System.Linq.IQueryable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e150f-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="e150f-108">Tento přístup zajišťuje, že tyto dotazy mohou být spouštěny vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="e150f-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="e150f-109">Dva hlavní výhody plynoucí z této techniky:</span><span class="sxs-lookup"><span data-stu-id="e150f-109">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="e150f-110">Nepovedlo se načíst nepotřebná data.</span><span class="sxs-lookup"><span data-stu-id="e150f-110">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="e150f-111">Dotaz spuštěný databázovým strojem je často efektivnější z důvodu indexů databáze.</span><span class="sxs-lookup"><span data-stu-id="e150f-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="e150f-112">místní spuštění</span><span class="sxs-lookup"><span data-stu-id="e150f-112">Local Execution</span></span>  
 <span data-ttu-id="e150f-113">V jiných situacích možná budete chtít mít kompletní sadu souvisejících entit v místní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e150f-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="e150f-114">Pro tento účel <xref:System.Data.Linq.EntitySet%601> <xref:System.Data.Linq.EntitySet%601.Load%2A> poskytuje metodu pro explicitní načtení <xref:System.Data.Linq.EntitySet%601>všech členů.</span><span class="sxs-lookup"><span data-stu-id="e150f-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="e150f-115"><xref:System.Data.Linq.EntitySet%601> Pokud je již načten, následné dotazy jsou spouštěny místně.</span><span class="sxs-lookup"><span data-stu-id="e150f-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="e150f-116">Tento přístup pomáhá dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="e150f-116">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="e150f-117">Pokud se úplná sada musí používat místně nebo víckrát, můžete se vyhnout vzdáleným dotazům a přidruženým latencím.</span><span class="sxs-lookup"><span data-stu-id="e150f-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="e150f-118">Entita může být serializována jako kompletní entita.</span><span class="sxs-lookup"><span data-stu-id="e150f-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="e150f-119">Následující fragment kódu ukazuje, jak lze získat místní spuštění:</span><span class="sxs-lookup"><span data-stu-id="e150f-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="e150f-120">Srovnání</span><span class="sxs-lookup"><span data-stu-id="e150f-120">Comparison</span></span>  
 <span data-ttu-id="e150f-121">Tyto dvě funkce poskytují výkonnou kombinaci možností: vzdálené spuštění velkých kolekcí a místní spouštění pro malé kolekce, nebo kde je potřeba kompletní kolekce.</span><span class="sxs-lookup"><span data-stu-id="e150f-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="e150f-122">Implementujete vzdálené spouštění prostřednictvím <xref:System.Linq.IQueryable>a místní spuštění proti kolekci v paměti. <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="e150f-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="e150f-123">Chcete-li vynutit místní spuštění ( <xref:System.Collections.Generic.IEnumerable%601>tj.), přečtěte si téma [převod typu na obecné rozhraní IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="e150f-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="e150f-124">Dotazy na neuspořádané sady</span><span class="sxs-lookup"><span data-stu-id="e150f-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="e150f-125">Všimněte si důležitého rozdílu mezi místní kolekcí, <xref:System.Collections.Generic.List%601> která implementuje, a kolekcí, která poskytuje vzdálené dotazy spouštěné proti *neuspořádaným sadám* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="e150f-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="e150f-126"><xref:System.Collections.Generic.List%601>metody, jako jsou například ty, které používají hodnoty indexu, vyžadují sémantiku seznamu, což obvykle nelze získat pomocí vzdáleného dotazu proti neuspořádané sadě.</span><span class="sxs-lookup"><span data-stu-id="e150f-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="e150f-127">Z tohoto důvodu tyto metody implicitně načtou <xref:System.Data.Linq.EntitySet%601> a umožňují místní spuštění.</span><span class="sxs-lookup"><span data-stu-id="e150f-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e150f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e150f-128">See also</span></span>

- [<span data-ttu-id="e150f-129">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="e150f-129">Query Concepts</span></span>](query-concepts.md)
