---
title: "Řazení a filtrování dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2411307623c714ae521d00dcffca05d3569a656e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-and-filtering-data"></a>Řazení a filtrování dat
<xref:System.Data.DataView> Nabízí několik způsobů řazení a filtrování dat v <xref:System.Data.DataTable>:  
  
-   Můžete použít <xref:System.Data.DataView.Sort%2A> vlastnosti a určit jeden nebo více sloupců pořadí řazení a zahrnují (vzestupně) ASC a DESC (sestupně) parametry.  
  
-   Můžete použít <xref:System.Data.DataView.ApplyDefaultSort%2A> vlastnost pro automatické vytvoření pořadí řazení, ve vzestupném pořadí, na základě sloupec primárního klíče nebo sloupců tabulky. <xref:System.Data.DataView.ApplyDefaultSort%2A>kdy se vztahuje pouze **řazení** vlastnost je odkaz s hodnotou null nebo prázdný řetězec, a pokud tabulka má definovaný primární klíč.  
  
-   Můžete použít <xref:System.Data.DataView.RowFilter%2A> vlastnosti k určení podmnožiny řádků podle jejich hodnot sloupců. Podrobnosti o platné výrazy pro **RowFilter** vlastnost, najdete v referenčních informacích pro <xref:System.Data.DataColumn.Expression%2A> vlastnost <xref:System.Data.DataColumn> třídy.  
  
     Pokud chcete vrátit výsledky konkrétní dotaz na data, a poskytuje dynamické zobrazení podmnožinu dat, použijte <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody **DataView** k dosažení nejlepšího výkonu místo nastavení **RowFilter** vlastnost. Nastavení **RowFilter** vlastnost znovu sestaví index pro data, přidávání režie k vaší aplikaci a snížení výkonu. **RowFilter** vlastnost nejlépe slouží v aplikaci vázané na data kde připojeného ovládacího prvku zobrazí filtrované výsledky. **Najít** a **FindRows** metody využít aktuální index bez nutnosti znovu sestavit index. Další informace o **najít** a **FindRows** metody, najdete v části [hledání řádky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Můžete použít <xref:System.Data.DataView.RowStateFilter%2A> vlastnosti k určení, které verze řádku zobrazíte. **DataView** implicitně spravuje které verze řádku vystavit, v závislosti na **RowState** základní řádku. Například pokud **Vlastnost RowStateFilter** je nastaven na **DataViewRowState.Deleted**, **DataView** zpřístupní **původní** verze řádku všechny **odstraněné** řádků, protože neexistuje žádný **aktuální** verze řádku. Můžete určit, které verze řádku řádku je vystavení pomocí **RowVersion** vlastnost **DataRowView**.  
  
     Následující tabulka znázorňuje možnosti pro **DataViewRowState**.  
  
    |Možnosti DataViewRowState|Popis|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Aktuální** verze řádku všech **Unchanged**, **Added**, a **změněné** řádků. Toto nastavení je výchozí.|  
    |**Přidat**|**Aktuální** verze řádku všech **Added** řádků.|  
    |**Odstranit**|**Původní** verze řádku všech **odstraněné** řádků.|  
    |**ModifiedCurrent**|**Aktuální** verze řádku všech **změněné** řádků.|  
    |**ModifiedOriginal**|**Původní** verze řádku všech **změněné** řádků.|  
    |**None**|Žádné řádky.|  
    |**OriginalRows**|**Původní** verze řádku všech **Unchanged**, **změněné**, a **odstraněné** řádků.|  
    |**Unchanged**|**Aktuální** verze řádku všech **Unchanged** řádků.|  
  
 Další informace o stavy řádků a řádek verzích najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Následující příklad kódu vytvoří zobrazení, zobrazí všechny produkty, kde počet jednotek v stock je menší než nebo rovna úrovni na změnit pořadí seřazeny nejprve podle ID dodavatele a poté podle názvu produktu.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
