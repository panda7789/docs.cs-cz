---
title: Navigace DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 3bd10694512e828354254588361cc009aac6602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756365"
---
# <a name="navigating-datatables"></a>Navigace DataTables
<xref:System.Data.DataTableReader> Získává obsah jedné nebo více <xref:System.Data.DataTable> objekty ve formě jednoho nebo více sad výsledků dotazu jen pro čtení, pouze pro předávání.  
  
 A <xref:System.Data.DataTableReader> může obsahovat více sad výsledků dotazu, pokud je vytvořen pomocí <xref:System.Data.DataSet.CreateDataReader%2A> metoda. Pokud je více než jednu sadu výsledků <xref:System.Data.DataTableReader.NextResult%2A> metoda Posune kurzor na další sadu výsledků dotazu. Toto je pouze pro předávání procesu. Není možné vrátit k předchozí sadu výsledků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `TestConstructor` metoda vytvoří dvě <xref:System.Data.DataTable> instance. K prokázání tohoto konstruktoru pro <xref:System.Data.DataTableReader> třída, ukázka vytvoří novou **třída DataTableReader** podle pole, které obsahuje dvě **DataTables**a provede jednoduchá operace Tisk obsahu z první málo sloupců do okna konzoly.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Čtečky datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
