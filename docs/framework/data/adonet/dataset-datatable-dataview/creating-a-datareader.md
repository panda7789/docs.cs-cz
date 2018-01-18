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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b603e4fad628d0bb338213420059ffa411acd432
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
