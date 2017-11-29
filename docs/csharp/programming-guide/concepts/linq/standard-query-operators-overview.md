---
title: "Přehled standardních operátorů dotazu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bcf64b87eb7fa1cba863f809dc11ab0ccb68ea9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="standard-query-operators-overview-c"></a>Přehled standardních operátorů dotazu (C#)
*Standardní operátory dotazu* jsou metody, které tvoří vzoru LINQ. Většina z nich fungovat v pořadí, kde je posloupnost objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Standardní operátory dotazu zadejte možnosti dotazu, včetně filtrování, projekce, agregace, řazení a další.  
  
 Existují dvě sady LINQ standardní operátory dotazu, který funguje na objekty typu <xref:System.Collections.Generic.IEnumerable%601> a dalších, který pracuje s objekty typu <xref:System.Linq.IQueryable%601>. Metody, které tvoří každá sada jsou statické členy <xref:System.Linq.Enumerable> a <xref:System.Linq.Queryable> třídy, v uvedeném pořadí. Jsou definovány jako *rozšiřující metody* typu, které budou pracovat. To znamená, že nelze volat pomocí syntaxe statickou metodu nebo syntaxi metody instance.  
  
 Kromě toho existuje několik metod operátor standardní dotaz pracovat typy kromě těch, na základě <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Typ definuje tyto dvě metody i na objekty typu pracovat <xref:System.Collections.IEnumerable>. Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umožňují povolit kolekci-parametry nebo neobecné, chcete-li spustit dotaz ve vzoru LINQ. Je to tak, že vytvoříte silného typu kolekce objektů. <xref:System.Linq.Queryable> Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, které pracují na objekty typu <xref:System.Linq.Queryable>.  
  
 Standardní operátory dotazu se liší v načasování jejich spuštění, v závislosti na tom, jestli vrátit hodnotu singleton nebo pořadí hodnot. Tyto metody, které vrací hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) spustit okamžitě. Metody, které vracejí sekvenci odložení spuštění dotazu a vrátí vyčíslitelný objekt.  
  
 V případě metody, které působí na kolekce v paměti, který je těchto metod, které rozšiřují <xref:System.Collections.Generic.IEnumerable%601>, vrácený vyčíslitelný objekt zaznamená argumenty, které byly předány metodě. Když tento objekt je ve výčtu uvedena, zaměstnání logiku operátor dotazu a budou vráceny výsledky dotazu.  
  
 Naproti tomu jsou metody, rozšířit <xref:System.Linq.IQueryable%601> neimplementuje žádné chování dotazování, ale sestavení strom výrazu představující dotaz provést. Zpracování dotazu se zpracovává souborem zdroj <xref:System.Linq.IQueryable%601> objektu.  
  
 Volání metody dotazů možné zřetězit společně v jednom dotazu, který umožňuje dotazy se libovolně komplexní.  
  
 Následující příklad kódu ukazuje, jak standardní operátory dotazu slouží k získání informací o sekvenci.  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Některé více často používaných standardní operátory dotazu mít vyhrazené syntaxe jazyka – klíčové slovo C# a Visual Basic umožňující volat v rámci *dotazu* *výraz*. Další informace o standardních operátorů dotazu, které mají vyhrazený klíčová slova a jejich odpovídající syntaxe najdete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozšíření standardní operátory dotazu  
 Sadu standardních operátorů dotazu lze posílení metodami vytváření specifické pro doménu, které jsou vhodné pro cílovou doménu nebo technologii. Můžete také standardní operátory dotazu nahraďte vlastní implementace, které poskytují další služby, jako je například vzdálené vyhodnocení, překlad dotazu a optimalizace. V tématu <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.  
  
## <a name="related-sections"></a>Související oddíly  
 Pomocí následujících odkazů se dostanete na témata, která obsahují další informace o různých standardních operátorů dotazu podle funkce.  
  
 [Řazení dat (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [Množinové operace (C#)](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrování dat (C#)](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [Operace kvantifikátoru (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Operace projekce (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [Segmentace dat (C#)](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Připojení k operace (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [Seskupování dat (C#)](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [Generování operací (C#)](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [Operace rovnosti (C#)](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [Operace s elementy (C#)](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [Převádění datových typů (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Operace sřetězení (C#)](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Agregační operace (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Úvod do dotazů LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [Klasifikace standardních operátorů dotazu podle metody provedení (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [Metody rozšíření](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
