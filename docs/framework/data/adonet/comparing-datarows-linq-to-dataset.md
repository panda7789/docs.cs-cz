---
title: Porovnání hodnot DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: fbd642fb3da6d664df9076b8d7576865d516727e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634895"
---
# <a name="comparing-datarows-linq-to-dataset"></a>Porovnání hodnot DataRows (LINQ to DataSet)
LINQ (Language-Integrated Query) definuje různé nastavené operátory pro porovnání zdrojových elementů, aby bylo vidět, zda jsou stejné. LINQ poskytuje následující operátory set:  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 Tyto operátory porovnávají zdrojové prvky voláním metody <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> a <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> v každé kolekci prvků. V případě <xref:System.Data.DataRow>tyto operátory provádějí porovnání odkazů, což obecně není ideální chování pro operace set přes tabulková data. Pro operace set je obvykle vhodné určit, zda jsou hodnoty prvků stejné a nikoli odkazy na prvky. Proto byla třída <xref:System.Data.DataRowComparer> přidána do LINQ to DataSet. Tato třída se dá použít k porovnání hodnot řádků.  
  
 Třída <xref:System.Data.DataRowComparer> obsahuje implementaci porovnání hodnot pro <xref:System.Data.DataRow>, takže tuto třídu lze použít pro operace set, jako je například <xref:System.Linq.Enumerable.Distinct%2A>. Tato třída nemůže být vytvořena přímo. místo toho je nutné použít vlastnost <xref:System.Data.DataRowComparer.Default%2A> k vrácení instance <xref:System.Data.DataRowComparer%601>. Pak se zavolá metoda <xref:System.Data.DataRowComparer%601.Equals%2A> a dva objekty <xref:System.Data.DataRow>, které se mají porovnat, jsou předány jako vstupní parametry. Metoda <xref:System.Data.DataRowComparer%601.Equals%2A> vrátí `true`, pokud je seřazená sada hodnot sloupců v obou <xref:System.Data.DataRow>ch objektech rovna hodnotě; v opačném případě `false`.  
  
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
