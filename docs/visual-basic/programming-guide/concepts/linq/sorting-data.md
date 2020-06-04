---
title: Řazení dat
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: a5ccff745995ed7f41731cf98fb7c49d3247d994
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406791"
---
# <a name="sorting-data-visual-basic"></a>Řazení dat (Visual Basic)

Operace řazení řadí prvky sekvence na základě jednoho nebo více atributů. První kritérium řazení provede primární řazení pro prvky. Zadáním druhého kritéria řazení můžete prvky seřadit v rámci každé primární skupiny řazení.

Následující ilustrace znázorňuje výsledky abecední operace řazení na sekvenci znaků.

![Obrázek, který zobrazuje abecední operaci řazení.](./media/sorting-data/alphabetical-sort-operation.png)

Standardní metody operátoru dotazu, které řadí data, jsou uvedeny v následující části.

## <a name="methods"></a>Metody

|Název metody|Description|Visual Basic syntaxe výrazu dotazu|Další informace|
|-----------------|-----------------|------------------------------------------|----------------------|
|OrderBy|Seřadí hodnoty ve vzestupném pořadí.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|OrderByDescending|Seřadí hodnoty v sestupném pořadí.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|ThenBy|Provede sekundární řazení ve vzestupném pořadí.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|ThenByDescending|Provede sekundární řazení v sestupném pořadí.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|Reverse|Obrátí pořadí prvků v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů

### <a name="primary-sort-examples"></a>Primární příklady řazení

#### <a name="primary-ascending-sort"></a>Primární vzestupné řazení

Následující příklad ukazuje, jak použít `Order By` klauzuli v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a>Primární sestupné řazení

Další příklad ukazuje, jak použít `Order By Descending` klauzuli v dotazu LINQ k řazení řetězců podle jejich prvního písmena v sestupném pořadí.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a>Sekundární příklady řazení

#### <a name="secondary-ascending-sort"></a>Sekundární vzestupné řazení

Následující příklad ukazuje, jak použít `Order By` klauzuli v dotazu LINQ k provedení primárního a sekundárního řazení řetězců v poli. Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce, ve vzestupném pořadí.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a>Sekundární sestupné řazení

Další příklad ukazuje, jak použít `Order By Descending` klauzuli v dotazu LINQ k provedení primárního řazení ve vzestupném pořadí a sekundárního řazení v sestupném pořadí. Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce.

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Order By – klauzule](../../../language-reference/queries/order-by-clause.md)
- [Postupy: řazení výsledků dotazu](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
