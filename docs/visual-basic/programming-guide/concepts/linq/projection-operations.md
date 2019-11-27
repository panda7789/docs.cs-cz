---
title: Operace projekce
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: d7efb46ccfe3208ae6c58043a64c236171d0c147
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346619"
---
# <a name="projection-operations-visual-basic"></a>Operace projekce (Visual Basic)

Projekce odkazuje na operaci transformace objektu do nového formuláře, který se často skládá pouze z těchto vlastností, které budou následně použity. Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu. Můžete promítnout vlastnost a na ní provést matematickou funkci. Původní objekt můžete také promítnout beze změny.

Standardní metody operátoru dotazu, které provádějí projekci, jsou uvedeny v následující části.

## <a name="methods"></a>Metody

|Název metody|Popis|Visual Basic syntaxe výrazu dotazu|Další informace|
|-----------------|-----------------|------------------------------------------|----------------------|
|Vybrat|Projekty hodnoty, které jsou založeny na transformační funkci.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|Operátor SelectMany|Projektuje sekvence hodnot, které jsou založeny na transformační funkci a poté jsou shrnuty do jedné sekvence.|Použít více klauzulí `From`|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů

### <a name="select"></a>Vybrat

V následujícím příkladu je použita klauzule `Select` pro projekt prvního písmene z každého řetězce v seznamu řetězců.

```vb
Dim words = New List(Of String) From {"an", "apple", "a", "day"}

Dim query = From word In words
            Select word.Substring(0, 1)

Dim sb As New System.Text.StringBuilder()
For Each letter As String In query
    sb.AppendLine(letter)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' a
' a
' a
' d
```

### <a name="selectmany"></a>Operátor SelectMany

Následující příklad používá více klauzulí `From` pro každé slovo z každého řetězce v seznamu řetězců.

```vb
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}

Dim query = From phrase In phrases
            From word In phrase.Split(" "c)
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' an
' apple
' a
' day
' the
' quick
' brown
' fox
```

## <a name="select-versus-selectmany"></a>Vybrat versus operátor SelectMany

Jak `Select()`, tak `SelectMany()` je vytvořit výslednou hodnotu (nebo hodnoty) ze zdrojových hodnot. `Select()` vytvoří jednu hodnotu výsledku pro každou zdrojovou hodnotu. Celkový výsledek je tedy kolekce, která má stejný počet prvků jako zdrojová kolekce. Naproti tomu `SelectMany()` vytváří jeden celkový výsledek, který obsahuje zřetězené dílčí kolekce z každé zdrojové hodnoty. Funkce transformace, která je předána jako argument pro `SelectMany()` musí vracet vyčíslitelné sekvence hodnot pro každou zdrojovou hodnotu. Tyto vyčíslitelné sekvence jsou poté zřetězeny `SelectMany()`, aby vytvořily jednu velkou sekvenci.

Následující dva ilustrace znázorňují koncepční rozdíl mezi akcemi těchto dvou metod. V každém případě Předpokládejme, že funkce Selector (transformace) vybere pole květů z každé zdrojové hodnoty.

Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojová kolekce.

![Obrázek, který zobrazuje akci výběru&#40;&#41;](./media/projection-operations/select-action-graphic.png)

Tento obrázek znázorňuje, jak `SelectMany()` zřetězí mezilehlé pořadí polí do jedné konečné výsledné hodnoty, která obsahuje všechny hodnoty z každého mezilehlého pole.

![Obrázek znázorňující akci operátor SelectMany&#40;&#41;](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a>Příklad kódu

Následující příklad porovnává chování `Select()` a `SelectMany()`. Kód vytvoří "kytici" květů z každého seznamu názvů květin ve zdrojové kolekci. V tomto příkladu "jednoduchá hodnota", kterou funkce transformace <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je sám kolekcí hodnot. K tomu je potřeba smyčka extra `For Each`, aby bylo možné vytvořit výčet každého řetězce v každé dílčí sekvenci.

```vb
Class Bouquet
    Public Flowers As List(Of String)
End Class

Sub SelectVsSelectMany()
    Dim bouquets = New List(Of Bouquet) From {
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}

    Dim output As New System.Text.StringBuilder

    ' Select()
    Dim query1 = bouquets.Select(Function(b) b.Flowers)

    output.AppendLine("Using Select():")
    For Each flowerList In query1
        For Each str As String In flowerList
            output.AppendLine(str)
        Next
    Next

    ' SelectMany()
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)

    output.AppendLine(vbCrLf & "Using SelectMany():")
    For Each str As String In query2
        output.AppendLine(str)
    Next

    ' Display the output
    MsgBox(output.ToString())

    ' This code produces the following output:
    '
    ' Using Select():
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

    ' Using SelectMany()
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

End Sub
```

## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md)
- [Postupy: kombinování dat pomocí spojení](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [Postupy: naplnění kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Postupy: Vrácení výsledku dotazu LINQ jako specifického typu](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [Postupy: rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
