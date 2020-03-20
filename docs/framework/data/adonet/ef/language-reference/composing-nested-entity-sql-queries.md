---
title: Sestavování dotazů s vnořeným jazykem Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150386"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="94695-102">Sestavování dotazů s vnořeným jazykem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="94695-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="94695-103">je bohatý funkční jazyk.</span><span class="sxs-lookup"><span data-stu-id="94695-103">is a rich functional language.</span></span> <span data-ttu-id="94695-104">Stavebním kamenem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz.</span><span class="sxs-lookup"><span data-stu-id="94695-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="94695-105">Na rozdíl [!INCLUDE[esql](../../../../../../includes/esql-md.md)] od běžných SQL není omezena [!INCLUDE[esql](../../../../../../includes/esql-md.md)] na tabulkovou sadu výsledků: podporuje skládání složitých výrazů, které mohou mít literály, parametry nebo vnořené výrazy.</span><span class="sxs-lookup"><span data-stu-id="94695-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="94695-106">Hodnota ve výrazu může být parametrizována nebo složena z jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="94695-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="94695-107">Vnořené výrazy</span><span class="sxs-lookup"><span data-stu-id="94695-107">Nested Expressions</span></span>  
 <span data-ttu-id="94695-108">Vnořený výraz lze umístit kdekoli, kde je přijata hodnota typu, který vrátí.</span><span class="sxs-lookup"><span data-stu-id="94695-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="94695-109">Například:</span><span class="sxs-lookup"><span data-stu-id="94695-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="94695-110">Vnořený dotaz lze umístit do projekční klauzule.</span><span class="sxs-lookup"><span data-stu-id="94695-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="94695-111">Například:</span><span class="sxs-lookup"><span data-stu-id="94695-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="94695-112">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vnořené dotazy musí být vždy uzavřeny v závorky:</span><span class="sxs-lookup"><span data-stu-id="94695-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="94695-113">Následující příklad ukazuje, jak správně vnořit výrazy do [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: How [to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="94695-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="94695-114">Vnořené dotazy v projekci</span><span class="sxs-lookup"><span data-stu-id="94695-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="94695-115">Vnořené dotazy v klauzuli projektu může získat přeloženy do dotazů kartézského produktu na serveru.</span><span class="sxs-lookup"><span data-stu-id="94695-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="94695-116">V některých serverech back-end, včetně SQL Server, to může způsobit, že tabulka TempDB získat velmi velké, což může nepříznivě ovlivnit výkon serveru.</span><span class="sxs-lookup"><span data-stu-id="94695-116">In some backend servers, including SQL Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="94695-117">Následuje příklad takového dotazu:</span><span class="sxs-lookup"><span data-stu-id="94695-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="94695-118">Řazení vnořených dotazů</span><span class="sxs-lookup"><span data-stu-id="94695-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="94695-119">V rámci entity vnořený výraz lze umístit kdekoli v dotazu.</span><span class="sxs-lookup"><span data-stu-id="94695-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="94695-120">Protože Entity SQL umožňuje velkou flexibilitu při psaní dotazů, je možné napsat dotaz, který obsahuje řazení vnořených dotazů.</span><span class="sxs-lookup"><span data-stu-id="94695-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="94695-121">Pořadí vnořeného dotazu však není zachováno.</span><span class="sxs-lookup"><span data-stu-id="94695-121">However, the order of a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="94695-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="94695-122">See also</span></span>

- [<span data-ttu-id="94695-123">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="94695-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
