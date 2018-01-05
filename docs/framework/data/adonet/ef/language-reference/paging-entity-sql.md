---
title: "Stránkování (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4aefa7bf9d70f704d24ecd60d4958c96ed412eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="paging-entity-sql"></a><span data-ttu-id="e8089-102">Stránkování (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="e8089-102">Paging (Entity SQL)</span></span>
<span data-ttu-id="e8089-103">Fyzické stránkování lze provést pomocí [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule v [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="e8089-103">Physical paging can be performed by using the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="e8089-104">K provedení fyzické stránkování nepodmíněně, měli byste použít přeskočit a LIMIT.</span><span class="sxs-lookup"><span data-stu-id="e8089-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="e8089-105">Pokud chcete omezit počet řádků ve výsledku způsobem, bez determinsitic, měli byste použít [horní](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e8089-105">If you only want to restrict the number of rows in the result in a non-determinsitic way, you should use [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span> <span data-ttu-id="e8089-106">TOP a SKIP/LIMIT se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="e8089-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="e8089-107">TOP – přehled</span><span class="sxs-lookup"><span data-stu-id="e8089-107">TOP Overview</span></span>  
 <span data-ttu-id="e8089-108">Klauzule SELECT může obsahovat volitelné nejvyšší dílčí klauzuli následující volitelné modifikátor všechna nebo DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="e8089-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="e8089-109">Dílčí klauzule TOP Určuje, že bude vrácen pouze první sadu řádků z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="e8089-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="e8089-110">Další informace najdete v tématu [horní](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e8089-110">For more information, see [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="e8089-111">Přeskočit a LIMIT – přehled</span><span class="sxs-lookup"><span data-stu-id="e8089-111">SKIP And LIMIT Overview</span></span>  
 <span data-ttu-id="e8089-112">Přeskočit a omezení jsou součástí klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="e8089-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="e8089-113">Pokud se nachází dílčí klauzuli SKIP výrazu v klauzuli ORDER BY, výsledky budou seřazeny podle specifikace řazení a sadu výsledků dotazu zahrne řádky od na další řádek hned po výrazu SKIP.</span><span class="sxs-lookup"><span data-stu-id="e8089-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="e8089-114">Například bude 5 PŘESKOČENÍ přeskočte prvních pět řádky a vrátí z šesté řádek dál.</span><span class="sxs-lookup"><span data-stu-id="e8089-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="e8089-115">Pokud dílčí klauzuli LIMIT výrazu nachází v klauzuli ORDER BY, dotaz seřadí podle specifikace řazení a výsledný počet řádků, bude omezený LIMIT výrazem.</span><span class="sxs-lookup"><span data-stu-id="e8089-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="e8089-116">Například LIMIT 5 se omezí sadu výsledků do pěti instance nebo řádků.</span><span class="sxs-lookup"><span data-stu-id="e8089-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="e8089-117">Přeskočit a LIMIT nemusí být použity současně; můžete použít jenom přeskočit nebo omezit pouze s klauzulí ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="e8089-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="e8089-118">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="e8089-118">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e8089-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="e8089-119">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [<span data-ttu-id="e8089-120">LIMIT</span><span class="sxs-lookup"><span data-stu-id="e8089-120">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [<span data-ttu-id="e8089-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="e8089-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="e8089-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8089-122">See Also</span></span>  
 [<span data-ttu-id="e8089-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e8089-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e8089-124">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e8089-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="e8089-125">Postupy: výsledky stránky prostřednictvím dotazu</span><span class="sxs-lookup"><span data-stu-id="e8089-125">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
