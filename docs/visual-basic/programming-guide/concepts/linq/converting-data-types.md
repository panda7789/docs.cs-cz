---
title: Převádění datových typů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: ad9594cabe0e2382ae4e19f2541eec4aa74ccd75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837049"
---
# <a name="converting-data-types-visual-basic"></a>Převádění datových typů (Visual Basic)
Převod metody změnit typ objektu, vstupu.  
  
 Převod operace v dotazech LINQ jsou užitečné pro různé aplikace. Toto jsou některé příklady:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metodu je možné skrýt vlastní implementaci typu operátoru standardního dotazu.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metody slouží k povolení neparametrizované kolekce pro dotazování na LINQ.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody je možné vynutit spuštění dotazu okamžité místo jeho odložit, dokud je vypočten dotaz.  
  
## <a name="methods"></a>Metody  
 V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.  
  
 Převod metody v této tabulce, jejichž názvy začínají písmenem "Jako" Změna statického typu zdrojové kolekce, ale není výčet. Metody, jejichž názvy začínají písmenem "Do výčet zdrojové kolekce a položky do příslušné kolekce" typu.  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Jako výčet|Vrátí zadaný jako vstup <xref:System.Collections.Generic.IEnumerable%601>.|Není k dispozici.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Převede (Obecné) <xref:System.Collections.IEnumerable> pro (obecný) <xref:System.Linq.IQueryable>.|Není k dispozici.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Změna typu|Elementy kolekce do zadaného typu přetypování.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Hodnoty v závislosti na jejich schopnost převést na zadaný typ filtrů.|Není k dispozici.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray –|Převede kolekci na pole. Tato metoda donutí provádění dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|Metody ToDictionary|Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče. Tato metoda donutí provádění dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList –|Převede kolekci <xref:System.Collections.Generic.List%601>. Tato metoda donutí provádění dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Vloží prvky do <xref:System.Linq.Lookup%602> (jeden na mnoho slovník) podle funkce selektoru klíče. Tato metoda donutí provádění dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad kódu používá `From As` klauzule přetypovat na typ podtyp před přístupem k členu, který je k dispozici pouze na podtyp.  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
