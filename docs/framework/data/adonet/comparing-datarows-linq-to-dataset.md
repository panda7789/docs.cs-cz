---
title: Porovnání hodnot DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 30a782f5e37e867c7a0e4dfd800f4b2c2836d070
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784936"
---
# <a name="comparing-datarows-linq-to-dataset"></a>Porovnání hodnot DataRows (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]definuje různé nastavené operátory pro porovnání zdrojových elementů, aby bylo vidět, zda jsou stejné. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]poskytuje následující operátory set:  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 Tyto operátory porovnávají zdrojové prvky voláním <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> metod <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> a u každé kolekce prvků. V případě <xref:System.Data.DataRow>, tyto operátory provádějí porovnání odkazů, což obecně není ideální chování pro operace set pro tabulková data. Pro operace set je obvykle vhodné určit, zda jsou hodnoty prvků stejné a nikoli odkazy na prvky. Proto byla třída přidána do LINQ to DataSet. <xref:System.Data.DataRowComparer> Tato třída se dá použít k porovnání hodnot řádků.  
  
 Třída obsahuje implementaci porovnání hodnot pro <xref:System.Data.DataRow>, takže tuto třídu lze použít pro operace set, jako je například <xref:System.Linq.Enumerable.Distinct%2A>. <xref:System.Data.DataRowComparer> Tato třída nemůže být vytvořena přímo. místo toho je třeba použít <xref:System.Data.DataRowComparer%601> vlastnostkvráceníinstance.<xref:System.Data.DataRowComparer.Default%2A> Metoda je pak volána a dva <xref:System.Data.DataRow> objekty, které mají být porovnány, jsou předány jako vstupní parametry. <xref:System.Data.DataRowComparer%601.Equals%2A> Metoda vrátí `true` , zda je seřazená sada hodnot sloupců v obou <xref:System.Data.DataRow> objektech shodná. v opačném `false`případě. <xref:System.Data.DataRowComparer%601.Equals%2A>  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Intersect` k vrácení kontaktů, které se zobrazí v obou tabulkách.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad Porovná dva řádky a získá své kódy hash.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRowComparer>
- [Načtení dat do datové sady](loading-data-into-a-dataset.md)
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
