---
title: 'Příklady syntaxe dotazu založené na metodách: Operátory elementů (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: e43208d6ae524a1370b936d42508e9c7a7d196e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149504"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a>Příklady syntaxe dotazu založené na metodách: Operátory elementů (LINQ to DataSet)
Příklady v tomto tématu ukazují, <xref:System.Linq.Enumerable.ElementAt%2A> jak <xref:System.Data.DataRow> používat metody <xref:System.Data.DataSet> <xref:System.Linq.Enumerable.First%2A> a získat prvky z pomocí syntaxe výrazu dotazu.  
  
 Metoda `FillDataSet` použitá v těchto příkladech je určena v [načtení dat do datové sady](loading-data-into-a-dataset.md).  
  
 Příklady v tomto tématu používají tabulky Kontakt, Adresa, Produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu `using` / `Imports` používají následující příkazy:  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 Další informace naleznete v [tématu How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="elementat"></a>Elementat  
  
### <a name="example"></a>Příklad  
 Tento příklad <xref:System.Linq.Enumerable.ElementAt%2A> používá metodu k `PostalCode` načtení páté adresy, kde == "M4B 1V7".  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a>První  
  
### <a name="example"></a>Příklad  
 Tento příklad <xref:System.Linq.Enumerable.First%2A> používá metodu k vrácení první kontakt, jehož křestní jméno je "Brooke".  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a>Viz také

- [Načtení dat do datové sady](loading-data-into-a-dataset.md)
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
- [Standardní operátory dotazů – přehled (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standardní operátory dotazů – přehled (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
