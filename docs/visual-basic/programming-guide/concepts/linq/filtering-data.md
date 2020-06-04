---
title: Filtrování dat
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: f7a1aa76dc93cc03952e55f5f8fc3f75176a3f9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383414"
---
# <a name="filtering-data-visual-basic"></a>Filtrování dat (Visual Basic)

Filtrování odkazuje na operaci omezení sady výsledků tak, aby obsahovala pouze prvky, které odpovídají zadané podmínce. Označuje se také jako výběr.

Následující ilustrace znázorňuje výsledky filtrování posloupnosti znaků. Predikát pro operaci filtrování určuje, že znak musí být "A".

![Diagram, který znázorňuje operaci filtrování LINQ](./media/filtering-data/linq-filter-operation.png)

Standardní metody operátoru dotazu, které provádějí výběr, jsou uvedeny v následující části.

## <a name="methods"></a>Metody

|Název metody|Description|Visual Basic syntaxe výrazu dotazu|Další informace|
|-----------------|-----------------|------------------------------------------|----------------------|
|Only|Vybere hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.|Neužívá se.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Kde|Vybere hodnoty, které jsou založeny na funkci predikátu.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu

Následující příklad používá `Where` k filtrování z pole tyto řetězce, které mají určitou délku.

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Klauzule WHERE](../../../language-reference/queries/where-clause.md)
- [Postupy: filtrování výsledků dotazu](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [Postupy: vytvoření dotazu na metadata sestavení s reflexí (LINQ) (Visual Basic)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Postupy: dotazování na soubory se zadaným atributem nebo názvem (Visual Basic)](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
