---
title: Načítání objektů z mezipaměti identit
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: ef771d924d9b508c29061f75a45808b5f81abb53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963837"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="9a302-102">Načítání objektů z mezipaměti identit</span><span class="sxs-lookup"><span data-stu-id="9a302-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="9a302-103">Toto téma popisuje typy LINQ to SQL dotazů, které vracejí objekt z mezipaměti identit, která je spravována pomocí <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="9a302-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="9a302-104">V LINQ to SQL jeden ze způsobů, jak <xref:System.Data.Linq.DataContext> jsou spravovány objekty, protokolování identit objektů do mezipaměti identit při spuštění dotazů.</span><span class="sxs-lookup"><span data-stu-id="9a302-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="9a302-105">V některých případech se LINQ to SQL pokusí načíst objekt z mezipaměti identit před provedením dotazu v databázi.</span><span class="sxs-lookup"><span data-stu-id="9a302-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="9a302-106">Obecně platí, že pokud LINQ to SQL dotaz vrátí objekt z mezipaměti identity, musí být dotaz založen na primárním klíči objektu a musí vracet jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="9a302-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="9a302-107">Konkrétně musí být dotaz v jednom z obecných formulářů uvedených níže.</span><span class="sxs-lookup"><span data-stu-id="9a302-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a302-108">Předem zkompilované dotazy nebudou vracet objekty z mezipaměti identit.</span><span class="sxs-lookup"><span data-stu-id="9a302-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="9a302-109">Další informace o předem kompilovaných dotazech naleznete v <xref:System.Data.Linq.CompiledQuery> tématech [a postupy: Ukládat a znovu používat](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)dotazy.</span><span class="sxs-lookup"><span data-stu-id="9a302-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="9a302-110">Aby bylo možné načíst objekt z mezipaměti identit, musí být dotaz v jedné z následujících obecných forem:</span><span class="sxs-lookup"><span data-stu-id="9a302-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="9a302-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="9a302-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="9a302-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="9a302-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="9a302-113">V těchto obecných formulářích `Function1` `Function2`,, a `predicate` jsou definovány následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9a302-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="9a302-114">`Function1`může to být kterýkoli z následujících:</span><span class="sxs-lookup"><span data-stu-id="9a302-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="9a302-115">`Function2`může to být kterýkoli z následujících:</span><span class="sxs-lookup"><span data-stu-id="9a302-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="9a302-116">`predicate`musí být výraz, ve kterém je vlastnost primárního klíče objektu nastavena na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9a302-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="9a302-117">Pokud má objekt primární klíč definovaný více než jednou vlastností, musí být každá vlastnost primárního klíče nastavena na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9a302-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="9a302-118">Níže jsou uvedené příklady formuláře `predicate` , které musí mít:</span><span class="sxs-lookup"><span data-stu-id="9a302-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="9a302-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a302-119">Example</span></span>  
 <span data-ttu-id="9a302-120">Následující kód poskytuje příklady typů LINQ to SQL dotazů, které načítají objekt z mezipaměti identit.</span><span class="sxs-lookup"><span data-stu-id="9a302-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9a302-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a302-121">See also</span></span>

- [<span data-ttu-id="9a302-122">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="9a302-122">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="9a302-123">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="9a302-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [<span data-ttu-id="9a302-124">Základní informace</span><span class="sxs-lookup"><span data-stu-id="9a302-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="9a302-125">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="9a302-125">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
