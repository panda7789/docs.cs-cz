---
title: Vytvoření zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: b88df66ef2e065d1db8d4033eb1fb0e47ebdd189
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108712"
---
# <a name="creating-a-dataview"></a>Vytvoření zobrazení dat
Existují dva způsoby, jak vytvořit <xref:System.Data.DataView>. Můžete použít **DataView** konstruktoru, nebo můžete vytvořit odkaz na <xref:System.Data.DataTable.DefaultView%2A> vlastnost <xref:System.Data.DataTable>. **DataView** konstruktor může být prázdný, nebo může trvat buď **DataTable** jako jediný argument, nebo **DataTable** spolu s kritéria filtru, kritéria řazení a řádek Filtr stavu. Další informace o další argumenty nejsou k dispozici pro použití se službou **DataView**, naleznete v tématu [řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Protože index **DataView** tvoříme tak i v případě **DataView** je vytvořen a při jejich **řazení**, **RowFilter**, nebo  **Vlastnost RowStateFilter** jsou upraveny vlastnosti Description, dosáhnout co nejlepšího výkonu tím, že poskytuje všechny počáteční řazení nebo filtrování kritéria jako argumenty konstruktoru, když vytvoříte **DataView**. Vytváření **DataView** bez zadání kritéria řazení nebo filtrování a pak nastavení **řazení**, **RowFilter**, nebo **Vlastnost RowStateFilter** Vlastnosti později způsobí, že index, který má být sestaven alespoň dvakrát: až při **DataView** je vytvořen, a znovu když některé vlastnosti řazení nebo filtrování se upraví.  
  
 Všimněte si, že pokud vytvoříte **DataView** pomocí konstruktoru, který nepřijímá žádné argumenty, nebudete moct používat **DataView** dokud nenastavíte **tabulky** vlastnost .  
  
 Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí **DataView** konstruktoru. A **RowFilter**, **řazení** sloupci a **DataViewRowState** dodávají spolu s **DataTable**.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 Následující příklad kódu ukazuje, jak získat odkaz na výchozí hodnotu **DataView** z **DataTable** pomocí **výchozí zobrazení** vlastnost tabulky.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
