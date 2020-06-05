---
title: Seskupování dat
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 8996eee748489c596bc5adc32f53b6b39dbfc6ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398380"
---
# <a name="grouping-data-visual-basic"></a>Seskupování dat (Visual Basic)
Seskupení odkazuje na operaci vložení dat do skupin, aby elementy v každé skupině sdílely společný atribut.  
  
 Následující ilustrace znázorňuje výsledky seskupení sekvencí znaků. Klíč pro každou skupinu je znak.  
  
 ![Diagram, který znázorňuje operaci seskupení LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 Standardní metody operátoru dotazu, které seskupují datové prvky, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Description|Visual Basic syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Seskupí prvky, které sdílejí společný atribut. Jednotlivé skupiny jsou reprezentovány <xref:System.Linq.IGrouping%602> objektem.|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Vloží prvky do <xref:System.Linq.Lookup%602> slovníku (do slovníku 1: n) na základě funkce selektoru klíče.|Neužívá se.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad kódu používá `Group By` klauzuli pro seskupení celých čísel v seznamu podle toho, zda jsou sudé nebo liché.  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Group By – klauzule](../../../language-reference/queries/group-by-clause.md)
- [Postupy: seskupování souborů podle přípony (LINQ) (Visual Basic)](how-to-group-files-by-extension-linq.md)
- [Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
