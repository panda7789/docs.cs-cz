---
title: Přidání datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 9cefc97e571f315a6a644e0a058d4283168ecb9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034508"
---
# <a name="adding-datarelations"></a>Přidání datových relací
V <xref:System.Data.DataSet> s několika <xref:System.Data.DataTable> objekty, můžete použít <xref:System.Data.DataRelation> objekty k jedné tabulky do druhé, procházení tabulky a vrátí podřízeného nebo nadřazeného řádky ze související tabulky.  
  
 Argumenty potřebné k vytvoření **DataRelation** jsou název **DataRelation** vytváří a pole jednoho nebo víc <xref:System.Data.DataColumn> odkazy na sloupce, které slouží jako nadřazené a podřízené sloupce v relaci. Po vytvoření **DataRelation**, slouží k navigaci mezi tabulkami a k načítání hodnot.  
  
 Přidávání **DataRelation** k <xref:System.Data.DataSet> přidá ve výchozím nastavení, <xref:System.Data.UniqueConstraint> do nadřazené tabulky a <xref:System.Data.ForeignKeyConstraint> podřízené tabulky. Další informace o těchto výchozích omezeních najdete v tématu [omezení datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Následující příklad kódu vytvoří **DataRelation** pomocí dvou <xref:System.Data.DataTable> objekty v <xref:System.Data.DataSet>. Každý <xref:System.Data.DataTable> obsahuje sloupec s názvem **CustID**, který slouží jako propojení mezi těmito dvěma <xref:System.Data.DataTable> objekty. Příklad přidá jeden **DataRelation** k **vztahy** kolekce <xref:System.Data.DataSet>. Určuje název prvního argumentu v příkladu **DataRelation** vytváří. Druhý argument nastaví nadřazeného **DataColumn** a třetí argument nastaví podřízené **DataColumn**.  
  
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
  
 A **DataRelation** má také **vnořené** vlastnost, která pokud je nastavena na **true**, způsobí, že řádky z podřízených tabulka, která má být vnořen v rámci řádku přidružené z nadřazené tabulky Při zápisu jako elementů XML pomocí <xref:System.Data.DataSet.WriteXml%2A> . Další informace najdete v tématu [použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
