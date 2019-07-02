---
title: Načtení dat do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 26b77269b21e1b365f81746ba2df66d7df91677e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504327"
---
# <a name="loading-data-into-a-dataset"></a>Načtení dat do datové sady
A <xref:System.Data.DataSet> objekt musí být vyplněno nejprve předtím, než můžete dát dotaz na něj pomocí jazyka LINQ k datové sadě. Existuje několik různých způsobů, jak naplnit <xref:System.Data.DataSet>. Například můžete použít [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] k dotazování databáze a načte výsledky do <xref:System.Data.DataSet>. Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Dalším běžným způsobem načtení dat do <xref:System.Data.DataSet> , je použít <xref:System.Data.Common.DataAdapter> třídy k načtení dat z databáze. To je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Data.Common.DataAdapter> k dotazování databáze AdventureWorks prodejní informace v roce 2002 a načte výsledky do <xref:System.Data.DataSet>. Po <xref:System.Data.DataSet> se vyplní, můžete psát dotazy proti ho pomocí jazyka LINQ k datové sadě. `FillDataSet` Metoda v tomto příkladu se používá v příkladů dotazů v [příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Další informace najdete v tématu [dotazování datových sad](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
