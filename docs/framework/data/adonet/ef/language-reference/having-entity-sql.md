---
title: MÁ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 76a63140668fb1f41cf9e6f901d9a43240a1d098
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936073"
---
# <a name="having-entity-sql"></a><span data-ttu-id="1880d-102">MÁ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1880d-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="1880d-103">Určuje podmínku vyhledávání pro skupinu nebo agregaci.</span><span class="sxs-lookup"><span data-stu-id="1880d-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1880d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1880d-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1880d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1880d-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="1880d-106">Určuje podmínku vyhledávání pro skupinu nebo agregaci, která má být splněna.</span><span class="sxs-lookup"><span data-stu-id="1880d-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="1880d-107">Pokud se používá s klauzulí GROUP BY ALL, klauzule HAVING přepíše vše.</span><span class="sxs-lookup"><span data-stu-id="1880d-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1880d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1880d-108">Remarks</span></span>  
 <span data-ttu-id="1880d-109">Klauzule HAVING se používá k určení dodatečné podmínky filtrování na výsledku seskupení.</span><span class="sxs-lookup"><span data-stu-id="1880d-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="1880d-110">Není-li ve výrazu dotazu zadána klauzule GROUP BY, je použita implicitní skupina s jedním množinou.</span><span class="sxs-lookup"><span data-stu-id="1880d-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1880d-111">Se dá použít jenom s příkazem [Select](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="1880d-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="1880d-112">Pokud se nepoužije [Group by](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) , chová se jako klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="1880d-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="1880d-113">Klauzule HAVING funguje podobně jako klauzule WHERE s tím rozdílem, že se používá po operaci GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1880d-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="1880d-114">To znamená, že klauzule HAVING může vytvořit pouze odkazy na aliasy seskupení a agregace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1880d-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="1880d-115">Předchozí omezí skupiny jenom na ty, které obsahují víc než jeden produkt.</span><span class="sxs-lookup"><span data-stu-id="1880d-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1880d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="1880d-116">Example</span></span>  
 <span data-ttu-id="1880d-117">Následující Entity SQL dotaz používá operátory HAVING a GROUP BY k určení podmínky vyhledávání pro skupinu nebo agregaci.</span><span class="sxs-lookup"><span data-stu-id="1880d-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="1880d-118">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1880d-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1880d-119">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="1880d-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1880d-120">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="1880d-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="1880d-121">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="1880d-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="1880d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1880d-122">See also</span></span>

- [<span data-ttu-id="1880d-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1880d-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="1880d-124">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="1880d-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
