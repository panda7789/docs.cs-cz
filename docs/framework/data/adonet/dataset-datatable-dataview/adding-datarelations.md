---
title: Přidání DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 451ee0eee466efca86345ea7112e9b178a2c66e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="adding-datarelations"></a>Přidání DataRelations
V <xref:System.Data.DataSet> s více <xref:System.Data.DataTable> objekty, můžete použít <xref:System.Data.DataRelation> objekty, které se týkají jednu tabulku do jiné, můžete procházet pomocí tabulky a vrátí řádky nadřazená nebo podřízená z tabulek v relaci.  
  
 Argumenty, které jsou nutné k vytváření **DataRelation** jsou název **DataRelation** vytváří a pole jednoho nebo více <xref:System.Data.DataColumn> odkazy na sloupce, které slouží jako nadřazené a podřízené sloupce v relaci. Po vytvoření **DataRelation**, můžete použít, přejděte mezi tabulkami a k načtení hodnoty.  
  
 Přidání **DataRelation** k <xref:System.Data.DataSet> přidá, ve výchozím nastavení, <xref:System.Data.UniqueConstraint> nadřazené tabulky a <xref:System.Data.ForeignKeyConstraint> do podřízené tabulky. Další informace o těchto výchozí omezení najdete v tématu [DataTable omezení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Následující příklad kódu vytvoří **DataRelation** pomocí dvou <xref:System.Data.DataTable> objekty v <xref:System.Data.DataSet>. Každý <xref:System.Data.DataTable> obsahuje sloupec s názvem **CustID**, který slouží jako propojení mezi těmito dvěma <xref:System.Data.DataTable> objekty. V příkladu přidáme jedné **DataRelation** k **vztahů** kolekce <xref:System.Data.DataSet>. Určuje název prvního argumentu v příkladu **DataRelation** vytváří. Druhý argument nastaví nadřazeného **DataColumn** a třetí argument nastaví podřízené **DataColumn**.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 A **DataRelation** má také **vnořené** vlastnost která, pokud nastavíte hodnotu **true**, způsobí, že řádky z tabulky podřízené být Nested v přidružené řádku, od nadřazené tabulky Když se zapisují jako elementů XML pomocí <xref:System.Data.DataSet.WriteXml%2A> . Další informace najdete v tématu [pomocí XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Viz také  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
