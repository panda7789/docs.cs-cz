---
title: Porovnání DataRows (LINQ na DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 79fc91092badfd871a1409e2ee602272f3eae100
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comparing-datarows-linq-to-dataset"></a>Porovnání DataRows (LINQ na DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] definuje různé operátory set k porovnání zdrojové elementy, které chcete zobrazit, pokud jsou stejné. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] poskytuje následující sadu operátory:  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 Tyto operátory porovnání zdrojové elementy voláním <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> a <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody pro každou kolekci elementů. U <xref:System.Data.DataRow>, proveďte tyto operátory porovnání odkaz, který není obecně ideální chování množinové operace přes tabulková data. Pro sadu operací obvykle chcete určit, jestli jsou stejné hodnoty elementu a není odkazuje element. Proto <xref:System.Data.DataRowComparer> třída byla přidána do [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Tato třída slouží k porovnání hodnot řádků.  
  
 <xref:System.Data.DataRowComparer> Třída obsahuje implementace porovnání hodnota <xref:System.Data.DataRow>, takže tato třída slouží pro sadu operací, jako <xref:System.Linq.Enumerable.Distinct%2A>. Tato třída nemůže být přímo vytvořeny instance; Místo toho <xref:System.Data.DataRowComparer.Default%2A> vlastnost je nutné použít vrátit instanci <xref:System.Data.DataRowComparer%601>. <xref:System.Data.DataRowComparer%601.Equals%2A> Metoda je volána poté a dvě <xref:System.Data.DataRow> předávání objektů, který se má porovnat v jako vstupní parametry. <xref:System.Data.DataRowComparer%601.Equals%2A> Metoda vrátí `true` Pokud sadu seřazený sloupec hodnoty v obou <xref:System.Data.DataRow> objekty jsou stejné, jinak hodnota `false`.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Intersect` vrátit kontakty, které se zobrazují v obou tabulkách.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad porovná dva řádky a získá jejich hash.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataRowComparer>  
 [Načtení dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
