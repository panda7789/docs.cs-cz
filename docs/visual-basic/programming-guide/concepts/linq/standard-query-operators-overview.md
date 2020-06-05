---
title: Přehled standardních operátorů dotazu
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 7c229a576f6695282473352d6253d2c699c76604
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406778"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Přehled standardních operátorů dotazů (Visual Basic)

*Standardní operátory dotazu* jsou metody, které tvoří vzor LINQ. Většina těchto metod pracuje na sekvencích, kde sekvence je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Standardní operátory dotazu poskytují možnosti dotazování, včetně filtrování, projekce, agregace, řazení a dalších.

Existují dvě sady standardních operátorů dotazů LINQ, jeden, který pracuje na objektech typu <xref:System.Collections.Generic.IEnumerable%601> a druhý, který pracuje s objekty typu <xref:System.Linq.IQueryable%601> . Metody, které tvoří každou sadu, jsou statické členy <xref:System.Linq.Enumerable> tříd a v <xref:System.Linq.Queryable> uvedeném pořadí. Jsou definovány jako *metody rozšíření* typu, na kterém pracují. To znamená, že mohou být volány buď pomocí syntaxe statické metody, nebo syntaxe metody instance.

Kromě toho několik metod standardních operátorů dotazů pracuje na jiných typech než těch, které jsou založeny na <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> . <xref:System.Linq.Enumerable>Typ definuje dvě takové metody, které pracují s objekty typu <xref:System.Collections.IEnumerable> . Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> umožňují povolit dotazování na kolekci, která není Parametrizovaná, nebo neobecná, aby bylo možné dotazovat ve vzorci LINQ. To dělají vytvořením silně typované kolekce objektů. <xref:System.Linq.Queryable>Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> , které pracují s objekty typu <xref:System.Linq.Queryable> .

Standardní operátory dotazu se liší v časování jejich spuštění v závislosti na tom, zda vracejí hodnotu typu Singleton nebo sekvence hodnot. Tyto metody, které vracejí hodnotu typu Singleton (například <xref:System.Linq.Enumerable.Average%2A> a), se <xref:System.Linq.Enumerable.Sum%2A> spustí okamžitě. Metody, které vracejí sekvenci, odloží provedení dotazu a vrátí vyčíslitelné objekty.

V případě metod, které pracují s kolekcemi v paměti, což znamená, že tyto metody, které rozšíření <xref:System.Collections.Generic.IEnumerable%601> , vrátí vyčíslitelné objekty argumenty, které byly předány metodě. Při vytváření výčtu tohoto objektu je vytvořena logika operátoru dotazu a jsou vráceny výsledky dotazu.

Naproti tomu metody, které rozšiřuje, <xref:System.Linq.IQueryable%601> neimplementují žádné dotazy, ale sestaví strom výrazu, který představuje dotaz, který má být proveden. Zpracování dotazu je zpracováváno zdrojovým <xref:System.Linq.IQueryable%601> objektem.

Volání metod dotazů lze zřetězit společně v jednom dotazu, který umožňuje, aby se dotazy staly libovolně složité.

Následující příklad kódu ukazuje, jak lze použít standardní operátory dotazu k získání informací o sekvenci.

```vb
Dim sentence = "the quick brown fox jumps over the lazy dog"
' Split the string into individual words to create a collection.
Dim words = sentence.Split(" "c)

Dim query = From word In words
            Group word.ToUpper() By word.Length Into gr = Group
            Order By Length _
            Select Length, GroupedWords = gr

Dim output As New System.Text.StringBuilder
For Each obj In query
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))
    For Each word As String In obj.GroupedWords
        output.AppendLine(word)
    Next
Next

'Display the output
MsgBox(output.ToString())

' This code example produces the following output:
'
' Words of length 3:
' THE
' FOX
' THE
' DOG
' Words of length 4:
' OVER
' LAZY
' Words of length 5:
' QUICK
' BROWN
' JUMPS
```

## <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu

Některé z často používaných standardních operátorů dotazů mají vyhrazená syntaxe klíčového slova jazyka C# a Visual Basic, která umožňuje jejich volání jako součást výrazu *dotazu* *expression*. Další informace o standardních operátorech dotazu, které mají vyhrazená klíčová slova a jejich odpovídajících syntaxech, naleznete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).

## <a name="extending-the-standard-query-operators"></a>Rozšíření standardních operátorů dotazu

Můžete rozšířit sadu standardních operátorů dotazů vytvořením metod specifických pro doménu, které jsou vhodné pro vaši cílovou doménu nebo technologii. Standardní operátory dotazu můžete také nahradit vlastními implementacemi, které poskytují další služby, jako je vzdálené vyhodnocení, překlad dotazů a optimalizace. Příklad najdete v tématu <xref:System.Linq.Enumerable.AsEnumerable%2A> .

## <a name="related-sections"></a>Související oddíly

Následující odkazy odkazují na témata, která poskytují další informace o různých standardních dotazovacích operátorech na základě funkcí.

- [Řazení dat](sorting-data.md)

- [Operace set (Visual Basic)](set-operations.md)

- [Filtrování dat (Visual Basic)](filtering-data.md)

- [Operace kvantifikátoru (Visual Basic)](quantifier-operations.md)

- [Operace projekce (Visual Basic)](projection-operations.md)

- [Dělení dat (Visual Basic)](partitioning-data.md)

- [Operace join (Visual Basic)](join-operations.md)

- [Seskupování dat (Visual Basic)](grouping-data.md)

- [Operace generování (Visual Basic)](generation-operations.md)

- [Operace rovnosti (Visual Basic)](equality-operations.md)

- [Operace elementu (Visual Basic)](element-operations.md)

- [Převádění datových typů (Visual Basic)](converting-data-types.md)

- [Operace zřetězení (Visual Basic)](concatenation-operations.md)

- [Agregační operace (Visual Basic)](aggregation-operations.md)

## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Úvod do LINQ (Visual Basic)](introduction-to-linq.md)
- [Syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](query-expression-syntax-for-standard-query-operators.md)
- [Klasifikace standardních operátorů dotazu podle způsobu provedení (Visual Basic)](classification-of-standard-query-operators-by-manner-of-execution.md)
- [Metody rozšíření](../../language-features/procedures/extension-methods.md)
