---
title: Přehled standardních operátorů dotazu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 27b144ae75054dbdc535b6ad894e4a5a0b8529e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653569"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Přehled standardních operátorů dotazu (Visual Basic)
*Standardní operátory dotazu* jsou metody, které tvoří vzoru LINQ. Většina z nich fungovat v pořadí, kde je posloupnost objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Standardní operátory dotazu zadejte možnosti dotazu, včetně filtrování, projekce, agregace, řazení a další.  
  
 Existují dvě sady LINQ standardní operátory dotazu, který funguje na objekty typu <xref:System.Collections.Generic.IEnumerable%601> a dalších, který pracuje s objekty typu <xref:System.Linq.IQueryable%601>. Metody, které tvoří každá sada jsou statické členy <xref:System.Linq.Enumerable> a <xref:System.Linq.Queryable> třídy, v uvedeném pořadí. Jsou definovány jako *rozšiřující metody* typu, které budou pracovat. To znamená, že nelze volat pomocí syntaxe statickou metodu nebo syntaxi metody instance.  
  
 Kromě toho existuje několik metod operátor standardní dotaz pracovat typy kromě těch, na základě <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Typ definuje tyto dvě metody i na objekty typu pracovat <xref:System.Collections.IEnumerable>. Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umožňují povolit kolekci-parametry nebo neobecné, chcete-li spustit dotaz ve vzoru LINQ. Je to tak, že vytvoříte silného typu kolekce objektů. <xref:System.Linq.Queryable> Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, které pracují na objekty typu <xref:System.Linq.Queryable>.  
  
 Standardní operátory dotazu se liší v načasování jejich spuštění, v závislosti na tom, jestli vrátit hodnotu singleton nebo pořadí hodnot. Tyto metody, které vrací hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) spustit okamžitě. Metody, které vracejí sekvenci odložení spuštění dotazu a vrátí vyčíslitelný objekt.  
  
 V případě metody, které působí na kolekce v paměti, který je těchto metod, které rozšiřují <xref:System.Collections.Generic.IEnumerable%601>, vrácený vyčíslitelný objekt zaznamená argumenty, které byly předány metodě. Když tento objekt je ve výčtu uvedena, zaměstnání logiku operátor dotazu a budou vráceny výsledky dotazu.  
  
 Naproti tomu jsou metody, rozšířit <xref:System.Linq.IQueryable%601> neimplementuje žádné chování dotazování, ale sestavení strom výrazu představující dotaz provést. Zpracování dotazu se zpracovává souborem zdroj <xref:System.Linq.IQueryable%601> objektu.  
  
 Volání metody dotazů možné zřetězit společně v jednom dotazu, který umožňuje dotazy se libovolně komplexní.  
  
 Následující příklad kódu ukazuje, jak standardní operátory dotazu slouží k získání informací o sekvenci.  
  
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
 Některé více často používaných standardní operátory dotazu mít vyhrazené syntaxe jazyka – klíčové slovo C# a Visual Basic umožňující volat v rámci *dotazu* *výraz*. Další informace o standardních operátorů dotazu, které mají vyhrazený klíčová slova a jejich odpovídající syntaxe najdete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozšíření standardní operátory dotazu  
 Sadu standardních operátorů dotazu lze posílení metodami vytváření specifické pro doménu, které jsou vhodné pro cílovou doménu nebo technologii. Můžete také standardní operátory dotazu nahraďte vlastní implementace, které poskytují další služby, jako je například vzdálené vyhodnocení, překlad dotazu a optimalizace. V tématu <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.  
  
## <a name="related-sections"></a>Související oddíly  
 Pomocí následujících odkazů se dostanete na témata, která obsahují další informace o různých standardních operátorů dotazu podle funkce.  
  
 [Řazení dat](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [Množinové operace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrování dat (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [Operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Operace projekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [Segmentace dat (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Připojení k operací (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [Seskupování dat (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [Generování operací (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [Operace rovnosti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [Operace s elementy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [Převádění datových typů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Operace sřetězení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Agregační operace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Úvod do LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 [Syntaxe výrazu dotazu pro standardní operátory dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [Klasifikace standardních operátorů dotazu podle metody provedení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [Rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
