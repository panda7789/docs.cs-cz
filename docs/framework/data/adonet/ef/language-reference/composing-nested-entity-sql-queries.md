---
title: Sestavování dotazů s vnořeným jazykem Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 4d6892e96cfbc9c5ba9d389aa03588c5133c7943
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137979"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="f74d5-102">Sestavování dotazů s vnořeným jazykem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f74d5-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f74d5-103">je bohatou jazykovou funkční.</span><span class="sxs-lookup"><span data-stu-id="f74d5-103">is a rich functional language.</span></span> <span data-ttu-id="f74d5-104">Základním pilířem pracovního [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz.</span><span class="sxs-lookup"><span data-stu-id="f74d5-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="f74d5-105">Na rozdíl od běžných SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není omezena pouze na sadu tabulkovém výsledku: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje vytváření složitých výrazů, které můžou mít literály, parametry nebo vnořené výrazy.</span><span class="sxs-lookup"><span data-stu-id="f74d5-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="f74d5-106">Hodnotu ve výrazu můžete s parametry nebo vytvořit další výrazu.</span><span class="sxs-lookup"><span data-stu-id="f74d5-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="f74d5-107">Vnořené výrazy</span><span class="sxs-lookup"><span data-stu-id="f74d5-107">Nested Expressions</span></span>  
 <span data-ttu-id="f74d5-108">Vnořený výraz může být umístěna kdekoli hodnotu typu, který vrátí je přijat.</span><span class="sxs-lookup"><span data-stu-id="f74d5-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="f74d5-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f74d5-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="f74d5-110">Vnořený dotaz je možné použít v klauzuli projekce.</span><span class="sxs-lookup"><span data-stu-id="f74d5-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="f74d5-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f74d5-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="f74d5-112">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vnořené dotazy musí být vždy uzavřen v závorkách:</span><span class="sxs-lookup"><span data-stu-id="f74d5-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="f74d5-113">Následující příklad ukazuje, jak správně vnořovat výrazy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Postupy: Pořadí sjednocení dva dotazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f74d5-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="f74d5-114">Vnořené dotazy v projekci</span><span class="sxs-lookup"><span data-stu-id="f74d5-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="f74d5-115">Vnořené dotazy v klauzuli projektu může získat přeloženy do kartézský součin dotazy na serveru.</span><span class="sxs-lookup"><span data-stu-id="f74d5-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="f74d5-116">V některých back-end serverů, včetně serveru SQL Server to může způsobit TempDB tabulka, která má být velmi rozsáhlé, což nepříznivě ovlivnit výkon serveru.</span><span class="sxs-lookup"><span data-stu-id="f74d5-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="f74d5-117">Následuje příklad tohoto dotazu:</span><span class="sxs-lookup"><span data-stu-id="f74d5-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="f74d5-118">Řazení vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="f74d5-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="f74d5-119">V rozhraní Entity Framework může být vnořený výraz umístěna kdekoli v dotazu.</span><span class="sxs-lookup"><span data-stu-id="f74d5-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="f74d5-120">Protože Entity SQL umožňuje velkou flexibilitu při psaní dotazů, je možné napsat dotaz, který obsahuje má za výsledek řazení vnořené dotazů.</span><span class="sxs-lookup"><span data-stu-id="f74d5-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="f74d5-121">Nezachová se však pořadí vnořeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="f74d5-121">However, the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f74d5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f74d5-122">See also</span></span>

- [<span data-ttu-id="f74d5-123">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f74d5-123">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
