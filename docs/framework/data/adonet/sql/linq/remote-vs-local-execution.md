---
title: Vzdálené vs. místní spuštění
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 02d0417bc05f8585dc469d365089c8123d395f64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164512"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="cc6a7-102">Vzdálené vs. místní spuštění</span><span class="sxs-lookup"><span data-stu-id="cc6a7-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="cc6a7-103">Můžete se rozhodnout spustit dotazy buď vzdáleně (to znamená, že databázový stroj provede dotaz na databázi) nebo místně ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provede dotaz proti místní mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="cc6a7-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="cc6a7-104">Vzdálené spuštění</span><span class="sxs-lookup"><span data-stu-id="cc6a7-104">Remote Execution</span></span>  
 <span data-ttu-id="cc6a7-105">Vezměte v úvahu následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="cc6a7-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="cc6a7-106">Pokud má vaše databáze tisíce řádků objednávek, nechcete je načíst všechny malou zpracovat.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="cc6a7-107">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> implementuje třída <xref:System.Linq.IQueryable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="cc6a7-108">Tento přístup zajišťuje, že tyto dotazy mohou být provedeny vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="cc6a7-109">Tato technika tok dvě hlavní výhody:</span><span class="sxs-lookup"><span data-stu-id="cc6a7-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="cc6a7-110">Není načten nepotřebná data.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="cc6a7-111">Dotaz proveden databázový stroj je často efektivnější z důvodu indexy databáze.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="cc6a7-112">místní spuštění</span><span class="sxs-lookup"><span data-stu-id="cc6a7-112">Local Execution</span></span>  
 <span data-ttu-id="cc6a7-113">V ostatních případech můžete chtít mít v místní mezipaměti úplnou sadu souvisejících entit.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="cc6a7-114">Pro tento účel <xref:System.Data.Linq.EntitySet%601> poskytuje <xref:System.Data.Linq.EntitySet%601.Load%2A> metodu pro explicitní načtení všech členů <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="cc6a7-115">Pokud <xref:System.Data.Linq.EntitySet%601> je již načten, následující dotazy se spouštějí místně.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="cc6a7-116">Tento přístup pomáhá dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="cc6a7-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="cc6a7-117">Pokud se všechny musí využívat místně nebo více než jednou, se můžete vyhnout vzdálené dotazy a související latenci.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="cc6a7-118">Entity lze serializovat jako úplnou entitu.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="cc6a7-119">Následující fragment kódu ukazuje, jak místní spuštění lze získat:</span><span class="sxs-lookup"><span data-stu-id="cc6a7-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="cc6a7-120">Srovnání</span><span class="sxs-lookup"><span data-stu-id="cc6a7-120">Comparison</span></span>  
 <span data-ttu-id="cc6a7-121">Tyto dvě schopnosti poskytovat výkonnou kombinaci možností: vzdálené spouštění rozsáhlých kolekcí a místní spuštění pro malé kolekce nebo kde je potřeba úplnou kolekci.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="cc6a7-122">Implementace vzdálené spuštění prostřednictvím <xref:System.Linq.IQueryable>a místní spuštění proti v paměti <xref:System.Collections.Generic.IEnumerable%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="cc6a7-123">Chcete-li vynutit místní spuštění (to znamená, <xref:System.Collections.Generic.IEnumerable%601>), najdete v článku [převod typu na obecnou položku IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="cc6a7-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="cc6a7-124">Dotazy na Neseřazený sady</span><span class="sxs-lookup"><span data-stu-id="cc6a7-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="cc6a7-125">Všimněte si důležitý rozdíl mezi místní kolekci, která implementuje <xref:System.Collections.Generic.List%601> a kolekce, která poskytuje vzdálený dotazů vůči *neuspořádaná sady* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="cc6a7-126"><xref:System.Collections.Generic.List%601> metody, jako jsou ty, které používají hodnoty indexu vyžadovat seznamu sémantiku, která obvykle je nelze získat prostřednictvím vzdálený dotaz proti neuspořádanou sadu.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="cc6a7-127">Z tohoto důvodu se tyto metody implicitně načíst <xref:System.Data.Linq.EntitySet%601> umožňující místní spouštění.</span><span class="sxs-lookup"><span data-stu-id="cc6a7-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6a7-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc6a7-128">See also</span></span>

- [<span data-ttu-id="cc6a7-129">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="cc6a7-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
