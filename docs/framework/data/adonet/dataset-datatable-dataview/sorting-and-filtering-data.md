---
title: Řazení a filtrování dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: ade08deca909b32090b7d2d7cf8c6ba9ce9e7679
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480571"
---
# <a name="sorting-and-filtering-data"></a>Řazení a filtrování dat
<xref:System.Data.DataView> Poskytuje několik možností, jak řazení a filtrování dat v <xref:System.Data.DataTable>:  
  
-   Můžete použít <xref:System.Data.DataView.Sort%2A> vlastnosti a určit jeden nebo více sloupců, pořadí řazení a zahrnují (vzestupně) ASC a DESC (sestupně) parametry.  
  
-   Můžete použít <xref:System.Data.DataView.ApplyDefaultSort%2A> automaticky vytvořit pořadí řazení ve vzestupném pořadí, nastavenou na sloupec primárního klíče nebo sloupců v tabulce. <xref:System.Data.DataView.ApplyDefaultSort%2A> platí, jen když **řazení** vlastnost je odkaz s hodnotou null nebo prázdný řetězec, a pokud tabulka má definován primární klíč.  
  
-   Můžete použít <xref:System.Data.DataView.RowFilter%2A> vlastnosti a určit tak podmnožiny řádků podle jejich hodnoty sloupce. Další informace o zobrazení platných výrazů pro **RowFilter** vlastnost, naleznete v tématu referenční informace pro <xref:System.Data.DataColumn.Expression%2A> vlastnost <xref:System.Data.DataColumn> třídy.  
  
     Pokud chcete vrátit výsledky konkrétní dotaz na data, na rozdíl od poskytují dynamický náhled na podmnožinu dat, může použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody **DataView** k dosažení nejlepšího výkonu dosáhnete spíše než nastavení **RowFilter** vlastnost. Nastavení **RowFilter** vlastnost znovu sestaví index pro data, přidání režie pro vaši aplikaci a snížit výkon. **RowFilter** vlastnost je nejvhodnější v aplikace vázané na data kde vázaného ovládacího prvku zobrazí filtrované výsledky. **Najít** a **FindRows** metody využívat bez nutnosti index znovu sestavit aktuální index. Další informace o **najít** a **FindRows** metody, naleznete v tématu [vyhledání řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Můžete použít <xref:System.Data.DataView.RowStateFilter%2A> vlastnosti a určit, jaké verze řádků k zobrazení. **DataView** implicitně spravuje verzi řádku, která se má zveřejnit, v závislosti na **RowState** základní řádku. Například pokud **Vlastnost RowStateFilter** je nastavena na **DataViewRowState.Deleted**, **DataView** zpřístupňuje **původní** verze řádku všechny **odstraněné** řádky, protože neexistuje žádný **aktuální** verze řádku. Můžete určit, kterou verzi řádku řádku je vystaven pomocí **RowVersion** vlastnost **DataRowView**.  
  
     V následující tabulce jsou uvedeny možnosti **DataViewRowState**.  
  
    |Hodnota DataViewRowState možnosti|Popis|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Aktuální** verze řádku všech **Unchanged**, **přidané**, a **změněné** řádků. Toto nastavení je výchozí.|  
    |**Přidat**|**Aktuální** verze řádku všech **přidané** řádků.|  
    |**Odstranit**|**Původní** verze řádku všech **odstraněné** řádků.|  
    |**ModifiedCurrent**|**Aktuální** verze řádku všech **změněné** řádků.|  
    |**ModifiedOriginal**|**Původní** verze řádku všech **změněné** řádků.|  
    |**None**|Žádné řádky.|  
    |**OriginalRows**|**Původní** verze řádku všech **Unchanged**, **změněné**, a **odstraněné** řádků.|  
    |**beze změny**|**Aktuální** verze řádku všech **Unchanged** řádků.|  
  
 Další informace o stavy řádků a verze řádků, naleznete v tématu [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Následující příklad kódu vytvoří zobrazení, zobrazí všechny produkty, kde počet jednotek v zásobách je menší než nebo rovna úrovni přesunout v pořadí řazení nejprve podle ID dodavatele a poté podle názvu produktu.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
