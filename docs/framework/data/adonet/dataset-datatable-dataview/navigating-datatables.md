---
title: Navigace v datových tabulkách
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 5008f8397b7d396b14fdfe8e24f1e59785c4319d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785251"
---
# <a name="navigating-datatables"></a>Navigace v datových tabulkách
Získá obsah jednoho nebo více <xref:System.Data.DataTable> objektů ve formě jedné nebo více sad výsledků pouze pro čtení, které jsou jen pro čtení. <xref:System.Data.DataTableReader>  
  
 Může obsahovat více sad výsledků, pokud je vytvořen <xref:System.Data.DataSet.CreateDataReader%2A> pomocí metody. <xref:System.Data.DataTableReader> Pokud je k dispozici více než jedna sada výsledků <xref:System.Data.DataTableReader.NextResult%2A> , metoda přesune kurzor na další sadu výsledků dotazu. Toto je proces jenom pro přeposílání. Není možné se vrátit k předchozí sadě výsledků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `TestConstructor` metoda vytvoří dvě <xref:System.Data.DataTable> instance. Aby bylo možné předvést tento konstruktor pro <xref:System.Data.DataTableReader> třídu, ukázka vytvoří novou **třídu DataTableReader** založenou na poli, které obsahuje dvě **tabulky DataTables**a provede jednoduchou operaci, vytištění obsahu z prvních několika. sloupce do okna konzoly.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Čtečky datových tabulek](datatablereaders.md)
- [Přehled ADO.NET](../ado-net-overview.md)
