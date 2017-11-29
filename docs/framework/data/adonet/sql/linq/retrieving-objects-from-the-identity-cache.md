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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d078476e881c3823d7772a9db4cdbdb23dac8bb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Načítání objektů z mezipaměti Identity
Toto téma popisuje typy LINQ na dotazy SQL, které vracejí objekt z mezipaměti identity, které spravuje <xref:System.Data.Linq.DataContext>.  
  
 V technologii LINQ to SQL jedním ze způsobů, ve kterém <xref:System.Data.Linq.DataContext> spravuje objekty, je protokolování identit objektů do mezipaměti identity, jak jsou spouštěny dotazy. V některých případech technologie LINQ to SQL se pokusí načíst objekt z mezipaměti identity před provedením dotazu v databázi.  
  
 Obecně platí dotazu LINQ to SQL vrátit objekt z mezipaměti identity, dotaz musí být založený na primárním klíči objektu a musí vracet jednoho objektu. Dotaz na konkrétní musí být v jednom z Obecné formuláře vidíte níže.  
  
> [!NOTE]
>  Předem kompilovaném dotazy nevrátí objektů z mezipaměti identity. Další informace o dotazech předem kompilovaném najdete v tématu <xref:System.Data.Linq.CompiledQuery> a [postup: úložiště a znovu používat dotazy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Dotaz musí být v jednom z následujících podob obecné načíst objekt z mezipaměti identity:  
  
-   <xref:System.Data.Linq.Table%601>`.Function1(``predicate``)`  
  
-   <xref:System.Data.Linq.Table%601>`.Function1(``predicate``).Function2()`  
  
 V těchto obecné forms `Function1`, `Function2`, a `predicate` jsou definovány takto.  
  
 `Function1`může být jedno z následujících:  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2`může být jedno z následujících:  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate`musí být výraz, ve kterém je nastavena vlastnost primárního klíče objektu na konstantní hodnotu. Pokud objekt má definovaný více než jeden vlastností primární klíč, každou vlastnost primárního klíče musí nastavit na konstantní hodnotu. Tady jsou příklady ve formátu `predicate` vyžaduje:  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje příklady typů LINQ na dotazy SQL, které načíst objekt z mezipaměti identity.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazu](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Identity – objekt](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Identity – objekt](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
