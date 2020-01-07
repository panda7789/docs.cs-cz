---
title: Dotazy na více tabulek (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 8f9a538482580134fa876866dfe394c3dfc7de2a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634882"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Dotazy na více tabulek (LINQ to DataSet)
Kromě dotazování na jednu tabulku můžete také provádět dotazy na více tabulek v LINQ to DataSet. To se provádí pomocí *spojení*. Spojení je asociace objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat, například ID produktu nebo kontaktu. V objektově orientovaném programování jsou relace mezi objekty relativně snadné, protože každý objekt má člena, který odkazuje na jiný objekt. V tabulkách externích databází ale navigace relací není jednoduchá. Databázové tabulky neobsahují předdefinované relace. V těchto případech je možné použít operaci JOIN k porovnávání prvků z jednotlivých zdrojů. Například při zadání dvou tabulek, které obsahují informace o produktu a informace o prodeji, můžete použít operaci JOIN k vyhledání informací o prodeji a produktů pro stejné prodejní objednávky.  
  
 Rozhraní LINQ (Language-Integrated Query) poskytuje dva operátory spojení, <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto operátory provádějí *ekvivalentní spojení*: to znamená, že spojení se dvěma zdroji dat odpovídají pouze v případě, že jejich klíče jsou stejné. (Naopak Transact-SQL podporuje operátory JOIN kromě `equals`, jako je například operátor `less than`.)  
  
 V rámci podmínek relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení. Vnitřní spojení je typ spojení, ve kterém jsou vráceny pouze objekty, které mají shodu v opačné datové sadě.  
  
 Operátory <xref:System.Linq.Enumerable.GroupJoin%2A> neobsahují žádný přímý ekvivalent v rámci podmínek relační databáze. implementují nadmnožinu vnitřních spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí každý prvek první kolekce (vlevo), i když nemá žádné korelační prvky ve druhé kolekci.  
  
 Další informace o spojeních najdete v tématu [operace join](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).  
  
## <a name="example"></a>Příklad  
 Následující příklad provádí tradiční spojení tabulek `SalesOrderHeader` a `SalesOrderDetail` z ukázkové databáze AdventureWorks, aby získala online objednávky z měsíce srpna.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy na datové sady](querying-datasets-linq-to-dataset.md)
- [Dotazy na jednu tabulku](single-table-queries-linq-to-dataset.md)
- [Dotazy na typové datové sady](querying-typed-datasets.md)
- [Operace sjednocení](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
