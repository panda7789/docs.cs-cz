---
title: Převádění datových typů
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 25d21954f0bb7555f1f5666f83fb37f4f73e2a60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354260"
---
# <a name="converting-data-types-visual-basic"></a>Převádění datových typů (Visual Basic)

Metody převodu mění typ vstupních objektů.

 Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích. Následuje několik příkladů:

- Pomocí metody <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> lze skrýt vlastní implementaci standardního operátoru dotazu.

- Metodu <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.

- Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení, dokud se dotaz nevytvoří.

## <a name="methods"></a>Metody

V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.

Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet. Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.

|Název metody|Popis|Visual Basic syntaxe výrazu dotazu|Další informace|
|-----------------|-----------------|------------------------------------------|----------------------|
|AsEnumerable|Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601>.|Není k dispozici.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Převede (Generic) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable>.|Není k dispozici.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Změna typu|Přetypování prvky kolekce na zadaný typ.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|Only|Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.|Není k dispozici.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray –|Převede kolekci na pole. Tato metoda vynutí provedení dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> na základě funkce selektoru klíče. Tato metoda vynutí provedení dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList –|Převede kolekci na <xref:System.Collections.Generic.List%601>. Tato metoda vynutí provedení dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Vloží prvky do <xref:System.Linq.Lookup%602> (slovník 1: n) na základě funkce selektoru klíče. Tato metoda vynutí provedení dotazu.|Není k dispozici.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu

Následující příklad kódu používá klauzuli `From As` pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.

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
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
