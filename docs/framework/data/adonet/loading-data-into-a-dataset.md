---
title: "Načítání dat do datové sady"
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
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 471a13b5d209def227bf8bc57b1551550b76a0c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="loading-data-into-a-dataset"></a>Načítání dat do datové sady
A <xref:System.Data.DataSet> objekt musí být před můžete dotazovat přes její naplněn [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Existuje několik různých způsobů k naplnění <xref:System.Data.DataSet>. Například můžete použít [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] pro dotazování databáze a načte výsledky do <xref:System.Data.DataSet>. Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Další běžné způsob, jak načíst data do <xref:System.Data.DataSet> je použití <xref:System.Data.Common.DataAdapter> třídy k načtení dat z databáze. To je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Data.Common.DataAdapter> dotazu databázi AdventureWorks prodeje informace z roku 2002 a načte výsledky do <xref:System.Data.DataSet>. Po <xref:System.Data.DataSet> naplněné, můžete psát dotazy proti ho pomocí [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. `FillDataSet` Metoda v tomto příkladu se používá v příkladů dotazů v [LINQ na DataSet příklady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Další informace najdete v tématu [dotazování datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
