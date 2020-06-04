---
title: Převádění datových typů
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 1394f53923ba850ae11fbc326a25c279589c3be1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410848"
---
# <a name="converting-data-types-visual-basic"></a>Převádění datových typů (Visual Basic)

Metody převodu mění typ vstupních objektů.

 Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích. Následuje několik příkladů:

- <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>Metoda může být použita ke skrytí vlastní implementace typu standardního operátoru dotazu.

- <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Metodu lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>Metody, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> , <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení až do vypsání dotazu.

## <a name="methods"></a>Metody

V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.

Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet. Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.

|Název metody|Description|Visual Basic syntaxe výrazu dotazu|Další informace|
|-----------------|-----------------|------------------------------------------|----------------------|
|AsEnumerable|Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601> .|Neužívá se.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Převede (Obecné) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable> .|Neužívá se.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Změna typu|Přetypování prvky kolekce na zadaný typ.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|Only|Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.|Neužívá se.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray –|Převede kolekci na pole. Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Vloží prvky do prvku na <xref:System.Collections.Generic.Dictionary%602> základě funkce selektoru klíče. Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList –|Převede kolekci na <xref:System.Collections.Generic.List%601> . Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Vloží prvky do <xref:System.Linq.Lookup%602> slovníku (do slovníku 1: n) na základě funkce selektoru klíče. Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu

Následující příklad kódu používá `From As` klauzuli pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.

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

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Klauzule FROM](../../../language-reference/queries/from-clause.md)
- [Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md)
