---
title: "Dotazy křížové tabulky (LINQ na DataSet)"
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
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 059dd39f3583c3b8fcf6736e514b9cc4870d3ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a>Dotazy křížové tabulky (LINQ na DataSet)
Kromě dotazování na jednotlivé tabulky, můžete také provést křížové tabulky dotazy v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. To se provádí pomocí *spojení*. Spojení je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut ve zdroji dat, jako je produkt nebo se obraťte na ID. Relace mezi objekty jsou v objektově orientované programování poměrně snadno přejít, protože každý objekt má člena, který odkazuje na jiný objekt. V tabulkách externí databáze ale navigace relací není stejně jednoduché. Databázové tabulky neobsahuje předdefinovaný vztahy. V těchto případech operace spojení lze tak, aby odpovídaly elementy z každého zdroje. Například zadány dvě tabulky, které obsahují informace o produktu a informace o prodeji, můžete použít operace spojení tak, aby odpovídaly informace o prodeji a produktů pro stejné prodeje pořadí.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework poskytuje dva operátory, připojte <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Provedení těchto operátorů *operátorem*: tedy spojení, které odpovídají dvěma datovými zdrojů, pouze když jejich klíče jsou si rovny. (Oproti tomu [!INCLUDE[tsql](../../../../includes/tsql-md.md)] podporuje připojení operátory než `equals`, například `less than` operátor.)  
  
 V podmínkách relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení. Vnitřní spojení je typ připojení ve které se vrátí pouze ty objekty, které mají odpovídající v opačné datové sady.  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A> Operátory mají ekvivalent v podmínkách relační databáze, je implementace nadmnožinou vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, která vrací každý prvek první kolekce (levém), i když nemá žádné korelační elementy v druhé kolekci.  
  
 Další informace o spojení najdete v tématu [připojení Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).  
  
## <a name="example"></a>Příklad  
 Následující příklad provádí tradiční připojení `SalesOrderHeader` a `SalesOrderDetail` tabulky z ukázkovou databázi AdventureWorks získat online objednávky z srpnu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Dotazy na jednu tabulku](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [Dotazy na typové datové sady](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [Operace sjednocení](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
