---
title: Seskupování dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: e2732c91dfff65ebb86ef45296ba369c3073a8f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="grouping-data-visual-basic"></a>Seskupování dat (Visual Basic)
Seskupení odkazuje na operaci ukládání dat do skupin tak, aby elementy v každé skupině sdílejí společný atribut.  
  
 Následující obrázek znázorňuje výsledky seskupování posloupnost znaků. Klíč pro každou skupinu je znak.  
  
 ![Operace seskupení LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 V následující části jsou uvedené metody operátor standardní dotazů, které seskupují datové prvky.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Prvky skupiny, které sdílejí společný atribut. Každá skupina je reprezentována <xref:System.Linq.IGrouping%602> objektu.|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče.|Nelze použít.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad kódu používá `Group By` klauzule na celá čísla skupinu v seznamu podle toho, zda jsou popisných.  
  
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
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klauzule Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [Postupy: seskupování souborů podle přípony (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
