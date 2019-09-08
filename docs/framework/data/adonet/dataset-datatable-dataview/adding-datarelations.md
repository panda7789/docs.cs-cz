---
title: Přidání datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 8157d296636d0f8661a35af35de561f5cc49c30b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784818"
---
# <a name="adding-datarelations"></a>Přidání datových relací
V případě <xref:System.Data.DataSet> více <xref:System.Data.DataTable> objektů lze pomocí <xref:System.Data.DataRelation> objektů propojit jednu tabulku s druhou, procházet tabulky a vracet podřízené nebo nadřazené řádky ze související tabulky.  
  
 Argumenty vyžadované k vytvoření **relace DataRelation** jsou název pro vytvoření datarelationship a pole jednoho nebo více <xref:System.Data.DataColumn> odkazů na sloupce, které slouží jako nadřazené a podřízené sloupce v relaci. Po vytvoření **relace DataRelation**ji můžete použít k navigaci mezi tabulkami a k načtení hodnot.  
  
 Přidání objektu **DataRelation** do <xref:System.Data.DataSet> přidat, <xref:System.Data.UniqueConstraint> ve výchozím nastavení do nadřazené tabulky a <xref:System.Data.ForeignKeyConstraint> do podřízené tabulky. Další informace o těchto výchozích omezeních naleznete v tématu [omezení DataTable](datatable-constraints.md).  
  
 Následující příklad kódu vytvoří datovou **relaci** pomocí dvou <xref:System.Data.DataTable> objektů v <xref:System.Data.DataSet>. Každý <xref:System.Data.DataTable> obsahuje sloupec s názvem **custid**, který slouží jako propojení mezi dvěma <xref:System.Data.DataTable> objekty. Tento příklad přidá jeden objekt **DataRelation** do kolekce **Relations** v <xref:System.Data.DataSet>. První argument v příkladu určuje název **Datarelationu** , který se vytváří. Druhý argument **Nastaví nadřazený datový sloupec a** třetí argument nastaví podřízený **sloupec DataColumn**.  
  
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
  
 Objekt **DataRelation** má také **vnořenou** vlastnost, která při nastavení na **hodnotu true**způsobí, že řádky z podřízené tabulky budou vnořeny do přidruženého řádku z nadřazené tabulky při zápisu jako XML prvky pomocí <xref:System.Data.DataSet.WriteXml%2A> . Další informace naleznete v tématu [using XML in a DataSet](using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
