---
title: Načtení dat do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794953"
---
# <a name="loading-data-into-a-dataset"></a>Načtení dat do datové sady
Předtím, než bude možné dotazovat na LINQ to DataSet, musí být objektnejprvevyplněn.<xref:System.Data.DataSet> Existuje několik různých způsobů, jak naplnit <xref:System.Data.DataSet>. Například můžete použít [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] k dotazování databáze a načtení výsledků <xref:System.Data.DataSet>do. Další informace najdete v tématu [LINQ to SQL](./sql/linq/index.md).  
  
 Dalším běžným způsobem načtení dat do <xref:System.Data.DataSet> je <xref:System.Data.Common.DataAdapter> použít třídu k načtení dat z databáze. To je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se <xref:System.Data.Common.DataAdapter> používá k dotazování databáze AdventureWorks na informace o prodeji z roku 2002 a výsledky se načítají <xref:System.Data.DataSet>do. Po naplnění můžete do <xref:System.Data.DataSet> něj zapisovat dotazy pomocí LINQ to DataSet. Metoda v tomto příkladu se používá v příkladech dotazů v [LINQ to DataSetch příkladech.](linq-to-dataset-examples.md) `FillDataSet` Další informace najdete v tématu [dotazování na datové sady](querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled LINQ to DataSet](linq-to-dataset-overview.md)
- [Dotazy na datové sady](querying-datasets-linq-to-dataset.md)
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
