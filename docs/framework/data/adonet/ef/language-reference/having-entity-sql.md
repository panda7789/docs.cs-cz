---
title: S (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a64bc0c9b5e1358046e78429780af796f60e404e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="having-entity-sql"></a><span data-ttu-id="ce15a-102">S (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="ce15a-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="ce15a-103">Určuje podmínku vyhledávání pro skupinu nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="ce15a-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce15a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce15a-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce15a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ce15a-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="ce15a-106">Určuje podmínku vyhledávání pro skupiny nebo agregace splnění.</span><span class="sxs-lookup"><span data-stu-id="ce15a-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="ce15a-107">Při HAVING se používá s GROUP BY ALL, klauzule HAVING přepíše všechny.</span><span class="sxs-lookup"><span data-stu-id="ce15a-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce15a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce15a-108">Remarks</span></span>  
 <span data-ttu-id="ce15a-109">V klauzuli HAVING slouží k určení další podmínku filtrování na výsledek seskupení.</span><span class="sxs-lookup"><span data-stu-id="ce15a-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="ce15a-110">Pokud ve výrazu dotazu je zadána klauzule GROUP BY, předpokládá se skupinu implicitní single-set.</span><span class="sxs-lookup"><span data-stu-id="ce15a-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce15a-111">HAVING lze použít pouze s [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="ce15a-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="ce15a-112">Když [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) se nepoužívá, HAVING chová jako klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="ce15a-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="ce15a-113">V klauzuli HAVING funguje jako klauzule WHERE, s tím rozdílem, že se použije po operaci GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="ce15a-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="ce15a-114">To znamená, že v klauzuli HAVING lze vytvořit pouze odkazy na seskupení aliasy a agregace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ce15a-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="ce15a-115">Předchozí omezuje skupiny jenom na ty, které obsahují více produktů.</span><span class="sxs-lookup"><span data-stu-id="ce15a-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce15a-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce15a-116">Example</span></span>  
 <span data-ttu-id="ce15a-117">Následující dotaz Entity SQL používá operátory HAVING a GROUP BY k zadání podmínek vyhledávání pro skupinu nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="ce15a-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="ce15a-118">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ce15a-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ce15a-119">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ce15a-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ce15a-120">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ce15a-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="ce15a-121">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="ce15a-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="ce15a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce15a-122">See Also</span></span>  
 [<span data-ttu-id="ce15a-123">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="ce15a-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="ce15a-124">Výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="ce15a-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
