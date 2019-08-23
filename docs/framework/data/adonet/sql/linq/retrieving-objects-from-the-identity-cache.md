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
# <a name="retrieving-objects-from-the-identity-cache"></a>Načítání objektů z mezipaměti identit
Toto téma popisuje typy LINQ to SQL dotazů, které vracejí objekt z mezipaměti identit, která je spravována pomocí <xref:System.Data.Linq.DataContext>.  
  
 V LINQ to SQL jeden ze způsobů, jak <xref:System.Data.Linq.DataContext> jsou spravovány objekty, protokolování identit objektů do mezipaměti identit při spuštění dotazů. V některých případech se LINQ to SQL pokusí načíst objekt z mezipaměti identit před provedením dotazu v databázi.  
  
 Obecně platí, že pokud LINQ to SQL dotaz vrátí objekt z mezipaměti identity, musí být dotaz založen na primárním klíči objektu a musí vracet jeden objekt. Konkrétně musí být dotaz v jednom z obecných formulářů uvedených níže.  
  
> [!NOTE]
> Předem zkompilované dotazy nebudou vracet objekty z mezipaměti identit. Další informace o předem kompilovaných dotazech naleznete v <xref:System.Data.Linq.CompiledQuery> tématech [a postupy: Ukládat a znovu používat](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)dotazy.  
  
 Aby bylo možné načíst objekt z mezipaměti identit, musí být dotaz v jedné z následujících obecných forem:  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 V těchto obecných formulářích `Function1` `Function2`,, a `predicate` jsou definovány následujícím způsobem.  
  
 `Function1`může to být kterýkoli z následujících:  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2`může to být kterýkoli z následujících:  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate`musí být výraz, ve kterém je vlastnost primárního klíče objektu nastavena na konstantní hodnotu. Pokud má objekt primární klíč definovaný více než jednou vlastností, musí být každá vlastnost primárního klíče nastavena na konstantní hodnotu. Níže jsou uvedené příklady formuláře `predicate` , které musí mít:  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Příklad  
 Následující kód poskytuje příklady typů LINQ to SQL dotazů, které načítají objekt z mezipaměti identit.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Identita objektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Identita objektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
