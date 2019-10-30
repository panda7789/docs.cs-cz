---
title: Vytvoření čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 696eb4dfc334390e1968dd317d441f3c987a1f77
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040112"
---
# <a name="creating-a-datareader"></a>Vytvoření čtečky dat
Třídy <xref:System.Data.DataTable> a <xref:System.Data.DataSet> mají metodu <xref:System.Data.DataTable.CreateDataReader%2A>, která vrací obsah <xref:System.Data.DataTable> nebo obsah <xref:System.Data.DataSet> kolekce objektu <xref:System.Data.DataSet.Tables%2A> jako jednu nebo více sad výsledků, které jsou jen pro čtení a pouze pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující Konzolová aplikace vytvoří instanci <xref:System.Data.DataTable>. Příklad předává vyplněný <xref:System.Data.DataTable> proceduře, která volá metodu <xref:System.Data.DataTable.CreateDataReader%2A>, která prochází výsledky obsaženými v <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 V příkladu se zobrazí následující výstup v okně konzoly:  
  
```output  
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
