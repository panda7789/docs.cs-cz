---
title: "Načítání objektů z mezipaměti Identity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e7677f2fcfe854aad5d01c0e024955da2480c375
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="bc446-102">Načítání objektů z mezipaměti Identity</span><span class="sxs-lookup"><span data-stu-id="bc446-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="bc446-103">Toto téma popisuje typy LINQ na dotazy SQL, které vracejí objekt z mezipaměti identity, které spravuje <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="bc446-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="bc446-104">V technologii LINQ to SQL jedním ze způsobů, ve kterém <xref:System.Data.Linq.DataContext> spravuje objekty, je protokolování identit objektů do mezipaměti identity, jak jsou spouštěny dotazy.</span><span class="sxs-lookup"><span data-stu-id="bc446-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="bc446-105">V některých případech technologie LINQ to SQL se pokusí načíst objekt z mezipaměti identity před provedením dotazu v databázi.</span><span class="sxs-lookup"><span data-stu-id="bc446-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="bc446-106">Obecně platí dotazu LINQ to SQL vrátit objekt z mezipaměti identity, dotaz musí být založený na primárním klíči objektu a musí vracet jednoho objektu.</span><span class="sxs-lookup"><span data-stu-id="bc446-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="bc446-107">Dotaz na konkrétní musí být v jednom z Obecné formuláře vidíte níže.</span><span class="sxs-lookup"><span data-stu-id="bc446-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc446-108">Předem kompilovaném dotazy nevrátí objektů z mezipaměti identity.</span><span class="sxs-lookup"><span data-stu-id="bc446-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="bc446-109">Další informace o dotazech předem kompilovaném najdete v tématu <xref:System.Data.Linq.CompiledQuery> a [postup: úložiště a znovu používat dotazy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="bc446-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="bc446-110">Dotaz musí být v jednom z následujících podob obecné načíst objekt z mezipaměti identity:</span><span class="sxs-lookup"><span data-stu-id="bc446-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
-   <span data-ttu-id="bc446-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="bc446-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
-   <span data-ttu-id="bc446-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="bc446-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="bc446-113">V těchto obecné forms `Function1`, `Function2`, a `predicate` jsou definovány takto.</span><span class="sxs-lookup"><span data-stu-id="bc446-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="bc446-114">`Function1`může být jedno z následujících:</span><span class="sxs-lookup"><span data-stu-id="bc446-114">`Function1` can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="bc446-115">`Function2`může být jedno z následujících:</span><span class="sxs-lookup"><span data-stu-id="bc446-115">`Function2` can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="bc446-116">`predicate`musí být výraz, ve kterém je nastavena vlastnost primárního klíče objektu na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc446-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="bc446-117">Pokud objekt má definovaný více než jeden vlastností primární klíč, každou vlastnost primárního klíče musí nastavit na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc446-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="bc446-118">Tady jsou příklady ve formátu `predicate` vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bc446-118">The following are examples of the form `predicate` must take:</span></span>  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="bc446-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc446-119">Example</span></span>  
 <span data-ttu-id="bc446-120">Následující kód obsahuje příklady typů LINQ na dotazy SQL, které načíst objekt z mezipaměti identity.</span><span class="sxs-lookup"><span data-stu-id="bc446-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bc446-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc446-121">See Also</span></span>  
 [<span data-ttu-id="bc446-122">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="bc446-122">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="bc446-123">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="bc446-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 [<span data-ttu-id="bc446-124">Základní informace</span><span class="sxs-lookup"><span data-stu-id="bc446-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="bc446-125">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="bc446-125">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
