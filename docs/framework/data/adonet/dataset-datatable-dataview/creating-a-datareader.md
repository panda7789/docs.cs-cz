---
title: "Vytváření DataReader –"
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
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 169f290ba41e7efe1ceb7c57f0821fdc0a886c5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datareader"></a>Vytváření DataReader –
<xref:System.Data.DataTable> a <xref:System.Data.DataSet> třídy mají <xref:System.Data.DataTable.CreateDataReader%2A> metodu, která vrátí obsah <xref:System.Data.DataTable> nebo obsah <xref:System.Data.DataSet> objektu <xref:System.Data.DataSet.Tables%2A> kolekce jako jeden nebo více sad výsledků dotazu jen pro čtení, pouze pro předávání.  
  
## <a name="example"></a>Příklad  
 Vytvoří následující konzolové aplikace <xref:System.Data.DataTable> instance. V příkladu pak předá vyplněný <xref:System.Data.DataTable> postupu, který volá <xref:System.Data.DataTable.CreateDataReader%2A> metodu, která prochází výsledky obsažené v <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 V příkladu se zobrazí následující výstup v okně konzoly:  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [Čtečky datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
