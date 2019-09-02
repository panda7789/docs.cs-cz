---
title: Vytvoření čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203893"
---
# <a name="creating-a-datareader"></a>Vytvoření čtečky dat
<xref:System.Data.DataTable> <xref:System.Data.DataSet.Tables%2A> Třídy a <xref:System.Data.DataSet>mají metodu<xref:System.Data.DataTable.CreateDataReader%2A> , která vrací<xref:System.Data.DataSet> obsah nebo obsah kolekce objektu jako jednu nebo více sad výsledků pouze pro čtení, které jsou jen pro čtení. <xref:System.Data.DataTable>  
  
## <a name="example"></a>Příklad  
 Následující Konzolová aplikace vytvoří <xref:System.Data.DataTable> instanci. Příklad předává vyplněný <xref:System.Data.DataTable> postup, který <xref:System.Data.DataTable.CreateDataReader%2A> volá metodu, která prochází výsledky obsaženými v <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 V příkladu se zobrazí následující výstup v okně konzoly:  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [Čtečky datových tabulek](datatablereaders.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
