---
title: Skládání dotazů vnořené Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: b5fc39a25b5b8592117348b150da9d82454a1562
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827315"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="17191-102">Skládání dotazů vnořené Entity SQL</span><span class="sxs-lookup"><span data-stu-id="17191-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="17191-103">je bohatou jazykovou funkční.</span><span class="sxs-lookup"><span data-stu-id="17191-103">is a rich functional language.</span></span> <span data-ttu-id="17191-104">Základním pilířem pracovního [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz.</span><span class="sxs-lookup"><span data-stu-id="17191-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="17191-105">Na rozdíl od běžných SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není omezena pouze na sadu tabulkovém výsledku: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje vytváření složitých výrazů, které můžou mít literály, parametry nebo vnořené výrazy.</span><span class="sxs-lookup"><span data-stu-id="17191-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="17191-106">Hodnotu ve výrazu můžete s parametry nebo vytvořit další výrazu.</span><span class="sxs-lookup"><span data-stu-id="17191-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="17191-107">Vnořené výrazy</span><span class="sxs-lookup"><span data-stu-id="17191-107">Nested Expressions</span></span>  
 <span data-ttu-id="17191-108">Vnořený výraz může být umístěna kdekoli hodnotu typu, který vrátí je přijat.</span><span class="sxs-lookup"><span data-stu-id="17191-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="17191-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="17191-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="17191-110">Vnořený dotaz je možné použít v klauzuli projekce.</span><span class="sxs-lookup"><span data-stu-id="17191-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="17191-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="17191-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="17191-112">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vnořené dotazy musí být vždy uzavřen v závorkách:</span><span class="sxs-lookup"><span data-stu-id="17191-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="17191-113">Následující příklad ukazuje, jak správně vnořovat výrazy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Postupy: Pořadí sjednocení dva dotazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="17191-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="17191-114">Vnořené dotazy v projekci</span><span class="sxs-lookup"><span data-stu-id="17191-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="17191-115">Vnořené dotazy v klauzuli projektu může získat přeloženy do kartézský součin dotazy na serveru.</span><span class="sxs-lookup"><span data-stu-id="17191-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="17191-116">V některých back-end serverů, včetně serveru SQL Server to může způsobit TempDB tabulka, která má být velmi rozsáhlé, což nepříznivě ovlivnit výkon serveru.</span><span class="sxs-lookup"><span data-stu-id="17191-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="17191-117">Následuje příklad tohoto dotazu:</span><span class="sxs-lookup"><span data-stu-id="17191-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="17191-118">Řazení vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="17191-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="17191-119">V rozhraní Entity Framework může být vnořený výraz umístěna kdekoli v dotazu.</span><span class="sxs-lookup"><span data-stu-id="17191-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="17191-120">Protože Entity SQL umožňuje velkou flexibilitu při psaní dotazů, je možné napsat dotaz, který obsahuje má za výsledek řazení vnořené dotazů.</span><span class="sxs-lookup"><span data-stu-id="17191-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="17191-121">Nezachová se však pořadí vnořeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="17191-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17191-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17191-122">See also</span></span>
- [<span data-ttu-id="17191-123">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="17191-123">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
