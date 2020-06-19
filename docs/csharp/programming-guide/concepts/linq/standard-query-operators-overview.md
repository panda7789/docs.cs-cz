---
title: Přehled standardních operátorů dotazů (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 095a0b7a7a8265f235d28a4634ea82cdcd7a60c0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990014"
---
# <a name="standard-query-operators-overview-c"></a>Přehled standardních operátorů dotazů (C#)
*Standardní operátory dotazu* jsou metody, které tvoří vzor LINQ. Většina těchto metod pracuje na sekvencích, kde sekvence je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Standardní operátory dotazu poskytují možnosti dotazování, včetně filtrování, projekce, agregace, řazení a dalších.  
  
 Existují dvě sady operátorů dotazu LINQ Standard: jeden, který pracuje na objektech typu <xref:System.Collections.Generic.IEnumerable%601> , další, který pracuje na objektech typu <xref:System.Linq.IQueryable%601> . Metody, které tvoří každou sadu, jsou statické členy <xref:System.Linq.Enumerable> tříd a v <xref:System.Linq.Queryable> uvedeném pořadí. Jsou definovány jako *metody rozšíření* typu, na kterém pracují. Metody rozšíření mohou být volány buď pomocí syntaxe statické metody, nebo syntaxe metody instance.  
  
 Kromě toho několik metod standardních operátorů dotazů pracuje na jiných typech než těch, které jsou založeny na <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> . <xref:System.Linq.Enumerable>Typ definuje dvě takové metody, které pracují s objekty typu <xref:System.Collections.IEnumerable> . Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> a <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> umožňují povolit dotazování na kolekci, která není Parametrizovaná, nebo neobecná, aby bylo možné dotazovat ve vzorci LINQ. To dělají vytvořením silně typované kolekce objektů. <xref:System.Linq.Queryable>Třída definuje dvě podobné metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> a <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> , které pracují s objekty typu <xref:System.Linq.Queryable> .  
  
 Standardní operátory dotazu se liší v časování jejich spuštění v závislosti na tom, zda vracejí hodnotu typu Singleton nebo sekvence hodnot. Tyto metody, které vracejí hodnotu typu Singleton (například <xref:System.Linq.Enumerable.Average%2A> a), se <xref:System.Linq.Enumerable.Sum%2A> spustí okamžitě. Metody, které vracejí sekvenci, odloží provedení dotazu a vrátí vyčíslitelné objekty.  
  
 Pro metody, které pracují s kolekcemi v paměti, což znamená, že tyto metody, které rozšíření <xref:System.Collections.Generic.IEnumerable%601> , vrátí vyčíslitelné objekty argumenty, které byly předány metodě. Při vytváření výčtu tohoto objektu je vytvořena logika operátoru dotazu a jsou vráceny výsledky dotazu.  
  
 Naopak metody, které rozšiřuje, <xref:System.Linq.IQueryable%601> neimplementují žádné chování při dotazování. Vytvoří strom výrazu, který představuje dotaz, který má být proveden. Zpracování dotazu je zpracováváno zdrojovým <xref:System.Linq.IQueryable%601> objektem.  
  
 Volání metod dotazů lze zřetězit společně v jednom dotazu, který umožňuje, aby se dotazy staly libovolně složité.  
  
 Následující příklad kódu ukazuje, jak lze použít standardní operátory dotazu k získání informací o sekvenci.  
  
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
 Některé z často používaných standardních operátorů dotazů mají vyhrazená syntaxe klíčového slova jazyka C# a Visual Basic, která umožňuje jejich volání jako součást výrazu *dotazu* *expression*. Další informace o standardních operátorech dotazu, které mají vyhrazená klíčová slova a jejich odpovídajících syntaxech, naleznete v tématu [syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](./query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozšíření standardních operátorů dotazu  
 Můžete rozšířit sadu standardních operátorů dotazů vytvořením metod specifických pro doménu, které jsou vhodné pro vaši cílovou doménu nebo technologii. Standardní operátory dotazu můžete také nahradit vlastními implementacemi, které poskytují další služby, jako je vzdálené vyhodnocení, překlad dotazů a optimalizace. Příklad najdete v tématu <xref:System.Linq.Enumerable.AsEnumerable%2A> .  
  
## <a name="related-sections"></a>Související oddíly  
 Následující odkazy odkazují na články, které poskytují další informace o různých standardních dotazovacích operátorech založených na funkcích.  
  
 [Řazení dat (C#)](./sorting-data.md)  
  
 [Operace set (C#)](./set-operations.md)  
  
 [Filtrování dat (C#)](./filtering-data.md)  
  
 [Operace kvantifikátoru (C#)](./quantifier-operations.md)  
  
 [Operace projekce (C#)](./projection-operations.md)  
  
 [Dělení dat (C#)](./partitioning-data.md)  
  
 [Operace join (C#)](./join-operations.md)  
  
 [Seskupení dat (C#)](./grouping-data.md)  
  
 [Operace generování (C#)](./generation-operations.md)  
  
 [Operace rovnosti (C#)](./equality-operations.md)  
  
 [Operace elementu (C#)](./element-operations.md)  
  
 [Převod datových typů (C#)](./converting-data-types.md)  
  
 [Operace zřetězení (C#)](./concatenation-operations.md)  
  
 [Agregační operace (C#)](./aggregation-operations.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Úvod do dotazů LINQ (C#)](./introduction-to-linq-queries.md)
- [Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Klasifikace standardních operátorů dotazu podle způsobu spuštění (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Metody rozšíření](../../classes-and-structs/extension-methods.md)
