---
title: "Vzdálené vs. Místní spuštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c402fad49526729ba09d8f4b86a5b022ca4a12cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="2a69a-102">Vzdálené vs. Místní spuštění</span><span class="sxs-lookup"><span data-stu-id="2a69a-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="2a69a-103">Můžete se rozhodnout spustit své dotazy buď vzdáleně (to znamená, databázový stroj provede dotaz na databázi nástroje) nebo místně ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provede dotaz proti místní mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="2a69a-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="2a69a-104">Vzdálené spuštění</span><span class="sxs-lookup"><span data-stu-id="2a69a-104">Remote Execution</span></span>  
 <span data-ttu-id="2a69a-105">Vezměte v úvahu následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="2a69a-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="2a69a-106">Pokud má vaše databáze tisíce řádky objednávky, nechcete je načtou všechny zpracovat malou.</span><span class="sxs-lookup"><span data-stu-id="2a69a-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="2a69a-107">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> třída implementuje <xref:System.Linq.IQueryable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a69a-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="2a69a-108">Tento přístup zajišťuje, že takové dotazy můžete provést vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="2a69a-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="2a69a-109">Dvě hlavní výhody tok ze tento postup:</span><span class="sxs-lookup"><span data-stu-id="2a69a-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="2a69a-110">Není-li načíst nepotřebná data.</span><span class="sxs-lookup"><span data-stu-id="2a69a-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="2a69a-111">Dotaz spuštěný pro databázový stroj je často efektivní kvůli indexy databáze.</span><span class="sxs-lookup"><span data-stu-id="2a69a-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="2a69a-112">Místní spuštění</span><span class="sxs-lookup"><span data-stu-id="2a69a-112">Local Execution</span></span>  
 <span data-ttu-id="2a69a-113">V ostatních případech můžete chtít mít kompletní sadu entit v relaci v místní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2a69a-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="2a69a-114">Pro tento účel <xref:System.Data.Linq.EntitySet%601> poskytuje <xref:System.Data.Linq.EntitySet%601.Load%2A> metoda explicitně načíst všechny členy <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="2a69a-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="2a69a-115">Pokud <xref:System.Data.Linq.EntitySet%601> je již načtena, následné dotazy jsou spouštěny místně.</span><span class="sxs-lookup"><span data-stu-id="2a69a-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="2a69a-116">Tento přístup umožňuje, aby dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="2a69a-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="2a69a-117">Pokud kompletní sadu se musí použít místně nebo několikrát, se můžete vyhnout vzdálených dotazů a přidružené latenci.</span><span class="sxs-lookup"><span data-stu-id="2a69a-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="2a69a-118">Entita může serializovat jako úplnou entitu.</span><span class="sxs-lookup"><span data-stu-id="2a69a-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="2a69a-119">Následující fragment kódu ukazuje, jak místní provádění získat:</span><span class="sxs-lookup"><span data-stu-id="2a69a-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="2a69a-120">Srovnání</span><span class="sxs-lookup"><span data-stu-id="2a69a-120">Comparison</span></span>  
 <span data-ttu-id="2a69a-121">Tyto dvě možnosti poskytují výkonný kombinaci možností: vzdálené spuštění rozsáhlých kolekcí a místní spuštění pro malé kolekce nebo kde je potřeba úplnou kolekci.</span><span class="sxs-lookup"><span data-stu-id="2a69a-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="2a69a-122">Implementace vzdálené spuštění prostřednictvím <xref:System.Linq.IQueryable>a místní provádění proti v paměti <xref:System.Collections.Generic.IEnumerable%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="2a69a-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="2a69a-123">Chcete-li vynutit místní provádění (tedy <xref:System.Collections.Generic.IEnumerable%601>), najdete v části [převést typ na obecný IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="2a69a-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="2a69a-124">Dotazy na neuspořádaný sady</span><span class="sxs-lookup"><span data-stu-id="2a69a-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="2a69a-125">Všimněte si důležitý rozdíl mezi místní kolekce, která implementuje <xref:System.Collections.Generic.List%601> a kolekce, která poskytuje vzdálené dotazy prováděné vůči *neuspořádané sady* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="2a69a-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="2a69a-126"><xref:System.Collections.Generic.List%601>metody, jako jsou ty, které používají hodnoty indexu vyžadují sémantiku seznamu, který nelze obvykle získat prostřednictvím vzdálený dotaz proti neuspořádaný sady.</span><span class="sxs-lookup"><span data-stu-id="2a69a-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="2a69a-127">Z tohoto důvodu se tyto metody implicitně zatížení <xref:System.Data.Linq.EntitySet%601> umožňuje místní spuštění.</span><span class="sxs-lookup"><span data-stu-id="2a69a-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a69a-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a69a-128">See Also</span></span>  
 [<span data-ttu-id="2a69a-129">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="2a69a-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
