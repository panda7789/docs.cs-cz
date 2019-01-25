---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 6ed20ea372314421e4855b1c1ad761c87bf461b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702558"
---
# <a name="top-entity-sql"></a><span data-ttu-id="edb8c-102">TOP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="edb8c-102">TOP (Entity SQL)</span></span>
<span data-ttu-id="edb8c-103">Klauzule SELECT může mít volitelné dílčí klauzule TOP následující volitelný modifikátor ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="edb8c-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="edb8c-104">Dílčí klauzule TOP Určuje, že bude vrácen pouze první sada řádků z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="edb8c-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb8c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edb8c-105">Syntax</span></span>  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="edb8c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="edb8c-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="edb8c-107">Číselný výraz, který určuje počet řádků, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="edb8c-107">The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="edb8c-108">`n` může být jeden číselný literál nebo jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="edb8c-108">`n` could be a single numeric literal or a single parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edb8c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edb8c-109">Remarks</span></span>  
 <span data-ttu-id="edb8c-110">HLAVNÍ výraz musí být jeden číselný literál nebo jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="edb8c-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="edb8c-111">Pokud se používá konstantní literál, typ literálu musí být implicitně možné zvýšit na Edm.Int64 (byte, int16, int32 nebo int64 nebo libovolný typ zprostředkovatele, který se mapuje na typ, který je možné zvýšit na Edm.Int64) a jeho hodnota musí být větší než nebo rovna hodnotě nula.</span><span class="sxs-lookup"><span data-stu-id="edb8c-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="edb8c-112">Jinak bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="edb8c-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="edb8c-113">Pokud parametr je používán jako výraz, typ parametru musí být také implicitně možné zvýšit na Edm.Int64, ale nebudou žádné ověření skutečný parametr hodnoty během kompilace vzhledem k tomu, že hodnoty parametrů jsou pozdní omezená.</span><span class="sxs-lookup"><span data-stu-id="edb8c-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>  
  
 <span data-ttu-id="edb8c-114">Následuje příklad konstantní výraz TOP:</span><span class="sxs-lookup"><span data-stu-id="edb8c-114">The following is an example of constant TOP expression:</span></span>  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="edb8c-115">Následuje příklad výrazu nejvyšší podle:</span><span class="sxs-lookup"><span data-stu-id="edb8c-115">The following is an example of parametrized TOP expression:</span></span>  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="edb8c-116">Začátek je Nedeterministický, pokud dotaz má řazení proběhnout.</span><span class="sxs-lookup"><span data-stu-id="edb8c-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="edb8c-117">Pokud budete potřebovat deterministické výsledky, použijte [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí ustanovení [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="edb8c-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="edb8c-118">TOP a SKIP/LIMIT se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="edb8c-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb8c-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="edb8c-119">Example</span></span>  
 <span data-ttu-id="edb8c-120">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá k určení nejvyšší jeden řádek, který se má vrátit z výsledku dotazu horní části.</span><span class="sxs-lookup"><span data-stu-id="edb8c-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="edb8c-121">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="edb8c-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="edb8c-122">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="edb8c-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="edb8c-123">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="edb8c-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="edb8c-124">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="edb8c-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a><span data-ttu-id="edb8c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edb8c-125">See also</span></span>
- [<span data-ttu-id="edb8c-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="edb8c-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="edb8c-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="edb8c-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [<span data-ttu-id="edb8c-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="edb8c-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [<span data-ttu-id="edb8c-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="edb8c-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [<span data-ttu-id="edb8c-130">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="edb8c-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
