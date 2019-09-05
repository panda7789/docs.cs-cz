---
title: Sestavování dotazů s vnořeným jazykem Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 3aa2e53b584eece9cc5e2d26791c78ffe33f9e35
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251139"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="46e4d-102">Sestavování dotazů s vnořeným jazykem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="46e4d-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="46e4d-103">je bohatě funkční jazyk.</span><span class="sxs-lookup"><span data-stu-id="46e4d-103">is a rich functional language.</span></span> <span data-ttu-id="46e4d-104">Stavební blok [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz.</span><span class="sxs-lookup"><span data-stu-id="46e4d-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="46e4d-105">Na rozdíl od konvenčního [!INCLUDE[esql](../../../../../../includes/esql-md.md)] SQL není omezení na sadu tabulkových výsledků: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje vytváření složitých výrazů, které mohou mít literály, parametry nebo vnořené výrazy.</span><span class="sxs-lookup"><span data-stu-id="46e4d-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="46e4d-106">Hodnota ve výrazu může být Parametrizovaná nebo složená z nějakého jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="46e4d-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="46e4d-107">Vnořené výrazy</span><span class="sxs-lookup"><span data-stu-id="46e4d-107">Nested Expressions</span></span>  
 <span data-ttu-id="46e4d-108">Vnořený výraz lze umístit kamkoli na libovolnou hodnotu typu, který vrátí.</span><span class="sxs-lookup"><span data-stu-id="46e4d-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="46e4d-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="46e4d-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="46e4d-110">Vnořený dotaz může být umístěn v klauzuli projekce.</span><span class="sxs-lookup"><span data-stu-id="46e4d-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="46e4d-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="46e4d-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="46e4d-112">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji musí být vnořené dotazy vždy uzavřeny v závorkách:</span><span class="sxs-lookup"><span data-stu-id="46e4d-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="46e4d-113">Následující příklad ukazuje, jak správně vnořovat výrazy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Postupy: Seřazení sjednocení dvou dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="46e4d-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="46e4d-114">Vnořené dotazy v projekci</span><span class="sxs-lookup"><span data-stu-id="46e4d-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="46e4d-115">Vnořené dotazy v klauzuli Project mohou být přeloženy do Kartézskémch dotazů na produkt na serveru.</span><span class="sxs-lookup"><span data-stu-id="46e4d-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="46e4d-116">V některých back-end serverech, včetně serveru SQL, to může způsobit, že by tabulka TempDB byla velmi velká, což může negativně ovlivnit výkon serveru.</span><span class="sxs-lookup"><span data-stu-id="46e4d-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="46e4d-117">Následuje příklad takového dotazu:</span><span class="sxs-lookup"><span data-stu-id="46e4d-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="46e4d-118">Řazení vnořených dotazů</span><span class="sxs-lookup"><span data-stu-id="46e4d-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="46e4d-119">V Entity Framework vnořený výraz může být umístěn kdekoli v dotazu.</span><span class="sxs-lookup"><span data-stu-id="46e4d-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="46e4d-120">Vzhledem k tomu, že Entity SQL umožňuje při psaní dotazů značnou flexibilitu, je možné napsat dotaz, který obsahuje řazení vnořených dotazů.</span><span class="sxs-lookup"><span data-stu-id="46e4d-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="46e4d-121">Pořadí vnořeného dotazu se ale nezachová.</span><span class="sxs-lookup"><span data-stu-id="46e4d-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46e4d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46e4d-122">See also</span></span>

- [<span data-ttu-id="46e4d-123">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="46e4d-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
