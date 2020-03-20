---
title: Vytvoření zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151335"
---
# <a name="creating-a-dataview"></a>Vytvoření zobrazení dat
Existují dva způsoby, <xref:System.Data.DataView>jak vytvořit . Můžete použít **Konstruktor DataView** nebo můžete vytvořit odkaz <xref:System.Data.DataTable.DefaultView%2A> na <xref:System.Data.DataTable>vlastnost . **Konstruktor DataView** může být prázdný nebo může trvat **datatable** jako jeden argument nebo **DataTable** spolu s kritérii filtru, kritéria řazení a filtr stavu řádku. Další informace o dalších argumentech, které jsou k dispozici pro použití s **zobrazením DataView**, naleznete v [tématu Řazení a filtrování dat](sorting-and-filtering-data.md).  
  
 Vzhledem k tomu, že index **pro DataView** je vytvořen při vytvoření **DataView** a při změně některé ho **sort**, **RowFilter**nebo **RowStateFilter** vlastnosti, můžete dosáhnout nejlepšího výkonu zadáním jakékoli počáteční pořadí řazení nebo filtrování kritéria jako argumenty konstruktoru při vytváření **DataView**. Vytvoření **dataview** bez zadání kritéria řazení nebo filtru a potom nastavení **Řazení**, **RowFilter**nebo **RowStateFilter** vlastnosti později způsobí, že index, který má být sestaven alespoň dvakrát: jednou při **dataView** a znovu při změně některé ho řazení nebo filtr vlastnosti.  
  
 Všimněte si, že pokud vytvoříte **DataView** pomocí konstruktoru, který nepřijímá žádné argumenty, nebude možné použít **DataView,** dokud jste nastavili **Table** vlastnost.  
  
 Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí **konstruktoru DataView.** **RowFilter**, **Sort** sloupec a **DataViewRowState** jsou dodávány spolu s **DataTable**.  
  
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
  
 Následující příklad kódu ukazuje, jak získat odkaz na výchozí **DataView** **datatable** pomocí **DefaultView** vlastnost tabulky.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Zobrazení dat](dataviews.md)
- [Řazení a filtrování dat](sorting-and-filtering-data.md)
- [Datové tabulky](datatables.md)
- [Přehled ADO.NET](../ado-net-overview.md)
