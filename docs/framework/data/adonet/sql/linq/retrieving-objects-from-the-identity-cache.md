---
title: Načítání objektů z mezipaměti identit
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: dceda9dce794e0a08cc9cd7905cf3cd0685898d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569151"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Načítání objektů z mezipaměti identit
Toto téma popisuje typy LINQ na SQL dotazy, které vracejí objekt z mezipaměti identit, které spravuje <xref:System.Data.Linq.DataContext>.  
  
 V technologii LINQ to SQL jedním ze způsobů, ve kterém <xref:System.Data.Linq.DataContext> spravuje objekty je protokolováním identit objektů do mezipaměti identity během provádění dotazů. V některých případech LINQ to SQL se pokusí načíst objekt z mezipaměti identit před provedením dotazu v databázi.  
  
 Obecně platí dotazu LINQ to SQL má vrátit objekt z mezipaměti identit, dotaz musí být založený na primárním klíči objektu a musí vrátit jednoho objektu. Konkrétně se dotaz musí být v jednom z obecného formuláře je uvedeno níže.  
  
> [!NOTE]
>  Předem kompilovaných dotazy nevrátí objektů z mezipaměti identit. Další informace o předem kompilovaných dotazy, naleznete v tématu <xref:System.Data.Linq.CompiledQuery> a [jak: Store a znovu používat dotazy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Dotaz musí být v jednom z následujících forem obecné načíst objekt z mezipaměti identit:  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 V tyto obecné formuláře `Function1`, `Function2`, a `predicate` jsou definovány takto.  
  
 `Function1` může být kterýkoli z následujících:  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` může být kterýkoli z následujících:  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` musí být výraz, ve kterém je nastavena vlastnost primárního klíče objektu na konstantní hodnotu. Pokud má objekt definován ve více než jednu vlastnost primární klíč, každá vlastnost primárního klíče musí nastavit na konstantní hodnotu. Následují příklady formuláře `predicate` musíte provést:  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje příklady typů LINQ dotazy SQL, které načíst objekt z mezipaměti identit.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Identita objektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Identita objektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
