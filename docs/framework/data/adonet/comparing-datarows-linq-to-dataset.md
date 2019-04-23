---
title: Porovnání datových řádků (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 2b45a4629474c394c8e49c41a7a98fc1181e124b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077170"
---
# <a name="comparing-datarows-linq-to-dataset"></a>Porovnání datových řádků (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] definuje různé sady operátory porovnání zdrojové elementy, pokud chcete zobrazit, pokud jsou shodné. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] poskytuje následující sadu operátorů:  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 Tyto operátory porovnávají zdrojové prvky pomocí volání <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> a <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> v každé kolekci prvků metody. V případě třídy <xref:System.Data.DataRow>, proveďte tyto operátory porovnání odkaz, který není obecně ideální chování množinové operace přes tabulková data. Pro sadu operací obvykle chcete určit, zda jsou stejné hodnoty prvků a není element odkazy. Proto <xref:System.Data.DataRowComparer> třídy je přidaný do [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Tato třída slouží k porovnání hodnoty řádků.  
  
 <xref:System.Data.DataRowComparer> Třída obsahuje implementaci porovnání hodnoty <xref:System.Data.DataRow>, takže tuto třídu můžete použít sadu operací, jako <xref:System.Linq.Enumerable.Distinct%2A>. Tato třída nemůže být přímo vytvořeny instance; Místo toho <xref:System.Data.DataRowComparer.Default%2A> vlastnost je nutné použít k vrácení instance <xref:System.Data.DataRowComparer%601>. <xref:System.Data.DataRowComparer%601.Equals%2A> Metoda je volána poté a dva <xref:System.Data.DataRow> jsou objekty, který se má porovnat předaný jako vstupní parametry. <xref:System.Data.DataRowComparer%601.Equals%2A> Vrátí metoda `true` Pokud uspořádané sady sloupec hodnoty v obou <xref:System.Data.DataRow> jsou objekty stejné; jinak `false`.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Intersect` vrátit kontakty, které se zobrazují v obou tabulkách.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad porovná dva řádky a získá jejich kódů hash.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRowComparer>
- [Načtení dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
