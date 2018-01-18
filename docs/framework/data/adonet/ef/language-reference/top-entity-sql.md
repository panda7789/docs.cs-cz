---
title: "HORNÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 10967ac87fa8f8504dc9a6a29be99401e620085e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="top-entity-sql"></a><span data-ttu-id="664ab-102">HORNÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="664ab-102">TOP (Entity SQL)</span></span>
<span data-ttu-id="664ab-103">Klauzule SELECT může obsahovat volitelné nejvyšší dílčí klauzuli následující volitelné modifikátor všechna nebo DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="664ab-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="664ab-104">Dílčí klauzule TOP Určuje, že bude vrácen pouze první sadu řádků z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="664ab-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="664ab-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="664ab-105">Syntax</span></span>  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="664ab-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="664ab-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="664ab-107">Číselný výraz, který určuje počet řádků, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="664ab-107">The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="664ab-108">`n`může být jeden číselný literál nebo jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="664ab-108">`n` could be a single numeric literal or a single parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="664ab-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="664ab-109">Remarks</span></span>  
 <span data-ttu-id="664ab-110">Výraz TOP musí být jeden číselný literál nebo jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="664ab-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="664ab-111">Pokud se použije konstantní literál, musí být typu literálu implicitně možné zvýšit na Edm.Int64 (bajtů, int16, int32 nebo int64 nebo žádný typ zprostředkovatele, který se mapuje na typ, který je možné zvýšit na Edm.Int64) a jeho hodnota musí být větší než nebo rovna hodnotě nula.</span><span class="sxs-lookup"><span data-stu-id="664ab-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="664ab-112">V opačném případě bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="664ab-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="664ab-113">Pokud parametr je použit jako výraz, typ parametru musí být také implicitně možné zvýšit na Edm.Int64, ale nebude žádné ověření skutečný parametr hodnoty během kompilace vzhledem k tomu, že jsou hodnoty parametru pozdní vázaný.</span><span class="sxs-lookup"><span data-stu-id="664ab-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>  
  
 <span data-ttu-id="664ab-114">Následuje příklad konstantní výraz TOP:</span><span class="sxs-lookup"><span data-stu-id="664ab-114">The following is an example of constant TOP expression:</span></span>  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="664ab-115">Následuje příklad umožňující jako výraz TOP:</span><span class="sxs-lookup"><span data-stu-id="664ab-115">The following is an example of parametrized TOP expression:</span></span>  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="664ab-116">HORNÍ je Nedeterministický, pokud je seřazen dotazu.</span><span class="sxs-lookup"><span data-stu-id="664ab-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="664ab-117">Pokud budete potřebovat výsledku deterministický, použijte [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule v [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="664ab-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="664ab-118">TOP a SKIP/LIMIT se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="664ab-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="664ab-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="664ab-119">Example</span></span>  
 <span data-ttu-id="664ab-120">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá horní k určení nejvyšší jeden řádek, který se má vrátit z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="664ab-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="664ab-121">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="664ab-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="664ab-122">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="664ab-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="664ab-123">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="664ab-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="664ab-124">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="664ab-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a><span data-ttu-id="664ab-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="664ab-125">See Also</span></span>  
 [<span data-ttu-id="664ab-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="664ab-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="664ab-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="664ab-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="664ab-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="664ab-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="664ab-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="664ab-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="664ab-130">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="664ab-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
