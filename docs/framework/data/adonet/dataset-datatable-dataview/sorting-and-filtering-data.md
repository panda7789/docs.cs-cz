---
title: Řazení a filtrování dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 0907aa2a66e1bf51fefc7bed8ea2612cc0c830fa
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203231"
---
# <a name="sorting-and-filtering-data"></a>Řazení a filtrování dat
Poskytuje několik způsobů řazení a filtrování dat <xref:System.Data.DataTable>v: <xref:System.Data.DataView>  
  
- <xref:System.Data.DataView.Sort%2A> Vlastnost můžete použít k určení řazení jednoho nebo více sloupců a zahrnutí parametrů ASC (vzestupně) a desc (sestupně).  
  
- <xref:System.Data.DataView.ApplyDefaultSort%2A> Vlastnost můžete použít k automatickému vytvoření pořadí řazení ve vzestupném pořadí podle sloupce primárního klíče nebo sloupce v tabulce. <xref:System.Data.DataView.ApplyDefaultSort%2A>platí pouze v případě, že vlastnost **Sort** je odkaz s hodnotou null nebo prázdný řetězec, a pokud je pro tabulku definována primární klíč.  
  
- <xref:System.Data.DataView.RowFilter%2A> Vlastnost můžete použít k určení podmnožiny řádků na základě hodnot jejich sloupců. Podrobnosti o platných výrazech pro vlastnost **RowFilter vyžaduje hodnotu** naleznete v referenčních informacích k <xref:System.Data.DataColumn.Expression%2A> vlastnosti <xref:System.Data.DataColumn> třídy.  
  
     Pokud chcete vrátit výsledky konkrétního dotazu na data, na rozdíl od poskytování dynamického zobrazení podmnožiny dat, použijte <xref:System.Data.DataView.Find%2A> metody nebo <xref:System.Data.DataView.FindRows%2A> objektu **DataView** k dosažení nejlepšího výkonu místo nastavení  **Vlastnost RowFilter vyžaduje hodnotu** Nastavením vlastnosti **RowFilter vyžaduje hodnotu** se znovu sestaví index dat, zvýší se režie do vaší aplikace a zmenší se výkon. Vlastnost **RowFilter vyžaduje hodnotu** se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky. Metody **find** a **FindRows** využívají aktuální index bez nutnosti opětovného vytvoření indexu. Další informace o metodách **find** a **FindRows** najdete v tématu [Vyhledání řádků](finding-rows.md).  
  
- <xref:System.Data.DataView.RowStateFilter%2A> Vlastnost můžete použít k určení, které verze řádků se mají zobrazit. **Objekt DataView** implicitně spravuje, která verze řádku má být vystavení v závislosti na **RowState** základního řádku. Pokud je například **vlastnost RowStateFilter** nastaveno na **DataViewRowState. Deleted**, zobrazení **DataView** zpřístupní **původní** verzi všech odstraněných řádků, protože neexistuje žádná verze **aktuálního** řádku. Můžete určit, která verze řádku řádku je zveřejněna, pomocí vlastnosti **rowversion** třídy **DataRowView**.  
  
     V následující tabulce jsou uvedeny možnosti pro **DataViewRowState**.  
  
    |DataViewRowState možnosti|Popis|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Aktuální** verze řádku všech nezměněných,přidaných a **upravených** řádků. Toto nastavení je výchozí.|  
    |**Přidat**|**Aktuální** verze řádku všech přidaných řádků.|  
    |**Odstraňování**|**Původní** verze řádků všech odstraněných řádků.|  
    |**ModifiedCurrent**|**Aktuální** verze řádků všech změněných řádků.|  
    |**ModifiedOriginal**|**Původní** verze řádků všech upravených řádků.|  
    |**Žádné**|Žádné řádky|  
    |**OriginalRows**|**Původní** verze řádku všech nezměněných, **upravených**a odstraněných řádků.|  
    |**Oproti**|**Aktuální** verze řádku všech nezměněných řádků.|  
  
 Další informace o stavech řádků a verzích řádků najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).  
  
 Následující příklad kódu vytvoří zobrazení, ve kterém se zobrazí všechny produkty, u kterých je počet jednotek v zásobách menší nebo roven úrovni přeřazení, seřazené podle prvního podle ID dodavatele a potom podle názvu produktu.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Zobrazení dat](dataviews.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
