---
title: Převádění datových typů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 9821b2d6caad8feeac856185b92518c25de88da3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643745"
---
# <a name="converting-data-types-visual-basic"></a>Převádění datových typů (Visual Basic)
Převod metody změnit typ vstupní objektů.  
  
 Převod operace v dotazech LINQ jsou užitečné v různých aplikací. Následuje několik příkladů:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda slouží ke skrytí vlastní implementaci typ operátoru standardní dotaz.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda slouží k povolení-parametry kolekce pro dotazy LINQ.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody slouží k vynucení spuštění okamžitou dotazu místo ho odložit, dokud není dotaz zpracován.  
  
## <a name="methods"></a>Metody  
 Následující tabulka uvádí metody operátor standardní dotazů, které provádět převody datových typů.  
  
 Převod metody v této tabulce, jejichž název začíná "Jako" změnit statický typ kolekce zdroj ale není výčet. Typ metody, jejichž název začíná "Na výčet zdrojové kolekci a umístí do příslušné kolekce položek".  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Jako výčet|Vrátí zadané jako vstup <xref:System.Collections.Generic.IEnumerable%601>.|Nelze použít.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Převede (Obecné) <xref:System.Collections.IEnumerable> k (Obecné) <xref:System.Linq.IQueryable>.|Nelze použít.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Změna typu|Vrhá prvky kolekce do zadaného typu.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Hodnoty, v závislosti na jejich schopnost převést na zadaný typ filtrování.|Nelze použít.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Převede kolekci na pole. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Vloží elementy do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|Převede kolekci na <xref:System.Collections.Generic.List%601>. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad kódu používá `From As` přetypovat typ k podtypem před přístupem k člena, který je dostupná jen pro dílčí klauzuli.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Postupy: dotazu na ArrayList pomocí LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
