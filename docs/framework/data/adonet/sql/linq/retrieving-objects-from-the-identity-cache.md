---
title: Načítání objektů z mezipaměti identit
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033472"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="c78f2-102">Načítání objektů z mezipaměti identit</span><span class="sxs-lookup"><span data-stu-id="c78f2-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="c78f2-103">Toto téma popisuje typy LINQ na SQL dotazy, které vracejí objekt z mezipaměti identit, které spravuje <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="c78f2-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="c78f2-104">V technologii LINQ to SQL jedním ze způsobů, ve kterém <xref:System.Data.Linq.DataContext> spravuje objekty je protokolováním identit objektů do mezipaměti identity během provádění dotazů.</span><span class="sxs-lookup"><span data-stu-id="c78f2-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="c78f2-105">V některých případech LINQ to SQL se pokusí načíst objekt z mezipaměti identit před provedením dotazu v databázi.</span><span class="sxs-lookup"><span data-stu-id="c78f2-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="c78f2-106">Obecně platí dotazu LINQ to SQL má vrátit objekt z mezipaměti identit, dotaz musí být založený na primárním klíči objektu a musí vrátit jednoho objektu.</span><span class="sxs-lookup"><span data-stu-id="c78f2-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="c78f2-107">Konkrétně se dotaz musí být v jednom z obecného formuláře je uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="c78f2-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c78f2-108">Předem kompilovaných dotazy nevrátí objektů z mezipaměti identit.</span><span class="sxs-lookup"><span data-stu-id="c78f2-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="c78f2-109">Další informace o předem kompilovaných dotazy, naleznete v tématu <xref:System.Data.Linq.CompiledQuery> a [jak: Store a znovu používat dotazy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="c78f2-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="c78f2-110">Dotaz musí být v jednom z následujících forem obecné načíst objekt z mezipaměti identit:</span><span class="sxs-lookup"><span data-stu-id="c78f2-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="c78f2-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="c78f2-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="c78f2-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="c78f2-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="c78f2-113">V tyto obecné formuláře `Function1`, `Function2`, a `predicate` jsou definovány takto.</span><span class="sxs-lookup"><span data-stu-id="c78f2-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="c78f2-114">`Function1` může být kterýkoli z následujících:</span><span class="sxs-lookup"><span data-stu-id="c78f2-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="c78f2-115">`Function2` může být kterýkoli z následujících:</span><span class="sxs-lookup"><span data-stu-id="c78f2-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="c78f2-116">`predicate` musí být výraz, ve kterém je nastavena vlastnost primárního klíče objektu na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c78f2-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="c78f2-117">Pokud má objekt definován ve více než jednu vlastnost primární klíč, každá vlastnost primárního klíče musí nastavit na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c78f2-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="c78f2-118">Následují příklady formuláře `predicate` musíte provést:</span><span class="sxs-lookup"><span data-stu-id="c78f2-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="c78f2-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="c78f2-119">Example</span></span>  
 <span data-ttu-id="c78f2-120">Následující kód obsahuje příklady typů LINQ dotazy SQL, které načíst objekt z mezipaměti identit.</span><span class="sxs-lookup"><span data-stu-id="c78f2-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c78f2-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c78f2-121">See also</span></span>

- [<span data-ttu-id="c78f2-122">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="c78f2-122">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="c78f2-123">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="c78f2-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [<span data-ttu-id="c78f2-124">Základní informace</span><span class="sxs-lookup"><span data-stu-id="c78f2-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="c78f2-125">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="c78f2-125">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
