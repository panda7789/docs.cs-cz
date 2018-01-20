---
title: "Sestavování dotazů SQL vnořené Entity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29f1f4f22a48aed1020b8e7ea42fe5ffd5b9f566
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="70df4-102">Sestavování dotazů SQL vnořené Entity</span><span class="sxs-lookup"><span data-stu-id="70df4-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="70df4-103">je bohaté funkční jazyk.</span><span class="sxs-lookup"><span data-stu-id="70df4-103"> is a rich functional language.</span></span> <span data-ttu-id="70df4-104">Stavební blok [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz.</span><span class="sxs-lookup"><span data-stu-id="70df4-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="70df4-105">Na rozdíl od konvenční SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není omezeno na tabulkovém výslednou sadu: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje skládání složité výrazy, které může mít literály, parametrů nebo vnořené výrazy.</span><span class="sxs-lookup"><span data-stu-id="70df4-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="70df4-106">Hodnotu ve výrazu můžete parametry nebo složené některé výrazu.</span><span class="sxs-lookup"><span data-stu-id="70df4-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="70df4-107">Vnořené výrazy</span><span class="sxs-lookup"><span data-stu-id="70df4-107">Nested Expressions</span></span>  
 <span data-ttu-id="70df4-108">Výraz vnořené můžete umístit kamkoli hodnotu typu, který vrátí byla přijata.</span><span class="sxs-lookup"><span data-stu-id="70df4-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="70df4-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="70df4-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="70df4-110">Vnořený dotaz se může v klauzuli projekce.</span><span class="sxs-lookup"><span data-stu-id="70df4-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="70df4-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="70df4-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="70df4-112">V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vnořené dotazy musí být uzavřena vždy v závorkách:</span><span class="sxs-lookup"><span data-stu-id="70df4-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="70df4-113">Následující příklad ukazuje, jak lze vnořit správně výrazy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [postupy: řazení Union z dva dotazy](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313).</span><span class="sxs-lookup"><span data-stu-id="70df4-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="70df4-114">Vnořené dotazy v projekci</span><span class="sxs-lookup"><span data-stu-id="70df4-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="70df4-115">Vnořené dotazy v klauzuli projektu, může získat přeložit na kartézský součin dotazy na serveru.</span><span class="sxs-lookup"><span data-stu-id="70df4-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="70df4-116">V některých back-end serverů, včetně serveru SQL Server to může způsobit tabulky databáze TempDB získat velký, který může nepříznivě ovlivnit výkon serveru.</span><span class="sxs-lookup"><span data-stu-id="70df4-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="70df4-117">Následuje příklad takového dotazu:</span><span class="sxs-lookup"><span data-stu-id="70df4-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="70df4-118">Řazení vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="70df4-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="70df4-119">V rozhraní Entity Framework mohou být výraz vnořené umístěny kdekoli v dotazu.</span><span class="sxs-lookup"><span data-stu-id="70df4-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="70df4-120">Protože Entity SQL umožňuje flexibilitu v zápis dotazů, je možné vytvořit dotaz, který obsahuje řazení vnořené dotazy.</span><span class="sxs-lookup"><span data-stu-id="70df4-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="70df4-121">Však není zachovávané pořadí vnořený dotaz.</span><span class="sxs-lookup"><span data-stu-id="70df4-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70df4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="70df4-122">See Also</span></span>  
 [<span data-ttu-id="70df4-123">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="70df4-123">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
