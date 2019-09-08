---
title: Vytvoření zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 3e1c31dac458594eee70ddd99469aca7cf63b848
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785485"
---
# <a name="creating-a-dataview"></a>Vytvoření zobrazení dat
Existují dva způsoby, jak vytvořit <xref:System.Data.DataView>. Můžete použít konstruktor **DataView** , nebo můžete vytvořit odkaz na <xref:System.Data.DataTable.DefaultView%2A> vlastnost. <xref:System.Data.DataTable> Konstruktor **DataView** může být prázdný nebo může přijmout buď **DataTable** jako jeden argument, nebo **objekt DataTable** spolu s kritérii filtru, kritérii řazení a filtrem stavu řádků. Další informace o dalších argumentech, které jsou k dispozici pro použití s **objektem DataView**, najdete v tématu [řazení a filtrování dat](sorting-and-filtering-data.md).  
  
 Vzhledem k tomu, že index pro zobrazení **dat** je sestaven při vytváření zobrazení **DataView** , a když se změní kterákoli z vlastností **Sort**, **RowFilter vyžaduje hodnotu**nebo **vlastnost RowStateFilter** , dosáhnete nejlepšího výkonu zadáním počáteční pořadí řazení nebo kritéria filtrování jako argumenty konstruktoru při vytváření zobrazení **DataView**. Vytvořením objektu **DataView** bez zadání kritérií pro řazení nebo filtrování a následným nastavením vlastností **Sort**, **RowFilter vyžaduje hodnotu**nebo **vlastnost RowStateFilter** dojde k tomu, že se index sestaví alespoň dvakrát: když je zobrazení **DataView** vytvořen a znovu po úpravě vlastnosti řazení nebo filtru.  
  
 Všimněte si, že pokud vytvoříte zobrazení **DataView** pomocí konstruktoru, který nepřijímá žádné argumenty, nebudete moci použít **objekt DataView** , dokud nenastavíte vlastnost **Table** .  
  
 Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí konstruktoru **DataView** . **RowFilter vyžaduje hodnotu**, sloupec **řazení** a **DataViewRowState** jsou zadány spolu s **objektem DataTable**.  
  
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
  
 Následující příklad kódu ukazuje, jak získat odkaz na výchozí **objekt DataView** **objektu DataTable** pomocí vlastnosti " **výchozí zobrazení** " tabulky.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Zobrazení dat](dataviews.md)
- [Řazení a filtrování dat](sorting-and-filtering-data.md)
- [Datové tabulky](datatables.md)
- [Přehled ADO.NET](../ado-net-overview.md)
