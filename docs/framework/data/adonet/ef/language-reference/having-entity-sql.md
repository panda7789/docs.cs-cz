---
title: S (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 19da828d3c7e7763c3dd9ba0e34da8849f90cf0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155139"
---
# <a name="having-entity-sql"></a><span data-ttu-id="73d92-102">S (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73d92-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="73d92-103">Určuje podmínku hledání pro skupinu nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="73d92-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73d92-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="73d92-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="73d92-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="73d92-106">Určuje pro skupinu nebo agregace pro splnění podmínky vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="73d92-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="73d92-107">Při použití s s GROUP BY ALL v klauzuli HAVING přepíše všechny.</span><span class="sxs-lookup"><span data-stu-id="73d92-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73d92-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73d92-108">Remarks</span></span>  
 <span data-ttu-id="73d92-109">V klauzuli HAVING slouží k určení dalších podmínku filtrování pro výsledek seskupení.</span><span class="sxs-lookup"><span data-stu-id="73d92-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="73d92-110">Klauzule GROUP BY je zadaný ve výrazu dotazu, předpokládá se implicitní skupina jedné sady.</span><span class="sxs-lookup"><span data-stu-id="73d92-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73d92-111">HAVING jde použít jenom s [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="73d92-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="73d92-112">Když [Group](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) se nepoužívá, HAVING se chová jako klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="73d92-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="73d92-113">V klauzuli HAVING funguje jako klauzuli WHERE, s tím rozdílem, že se použije po provedení této operace GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="73d92-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="73d92-114">To znamená, že v klauzuli HAVING lze vytvořit pouze odkazy na seskupení aliasů a agregace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="73d92-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="73d92-115">Předchozí skupiny omezuje jenom na ty, které obsahují více než jeden produkt.</span><span class="sxs-lookup"><span data-stu-id="73d92-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73d92-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="73d92-116">Example</span></span>  
 <span data-ttu-id="73d92-117">Následující dotaz Entity SQL používá operátory HAVING a GROUP BY k zadání podmínek vyhledávání pro skupinu nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="73d92-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="73d92-118">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="73d92-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73d92-119">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="73d92-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="73d92-120">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="73d92-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="73d92-121">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="73d92-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="73d92-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73d92-122">See also</span></span>

- [<span data-ttu-id="73d92-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="73d92-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="73d92-124">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="73d92-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
