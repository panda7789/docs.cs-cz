---
title: Filtrování dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: a673126d928a97bf522783e73fc254debe2a9de8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837440"
---
# <a name="filtering-data-visual-basic"></a>Filtrování dat (Visual Basic)
Filtrování odkazuje na operaci omezení sady výsledků do obsahovat pouze prvky, které splňují zadanou podmínku. Je také označován jako výběr.  
  
 Následující obrázek ukazuje výsledky filtrování posloupnost znaků. Predikát pro filtrování operace určuje, že znak musí být "A".  
  
 ![Diagram, který ukazuje filtrování operace LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí výběru.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OfType|Vybere hodnoty v závislosti na jejich schopnost převést na zadaný typ.|Není k dispozici.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Vybere hodnoty, které jsou založeny na funkce predikátu.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 V následujícím příkladu `Where` filtrovat z pole těchto řetězců, které mají určité délky.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Postupy: Filtrování výsledků dotazu](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [Postupy: Dotazu na Metadata sestavení s reflexí (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Postupy: Dotaz pro soubory s konkrétním atributem či názvem (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
