---
title: Vytvoření čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 79cb2ce7ffae81aeba9aaca557e37ba566a8370c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784763"
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
- [Přehled ADO.NET](../ado-net-overview.md)
