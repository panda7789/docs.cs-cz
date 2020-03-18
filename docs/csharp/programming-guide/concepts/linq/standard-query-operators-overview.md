---
title: Standardní operátory dotazů – přehled (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 76c2c4684f33c3fb30748b5f08efd215548661ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167852"
---
# <a name="standard-query-operators-overview-c"></a>Standardní operátory dotazů – přehled (C#)
*Standardní operátory dotazu* jsou metody, které tvoří vzor LINQ. Většina těchto metod pracovat na sekvence, kde sekvence je <xref:System.Collections.Generic.IEnumerable%601> objekt, <xref:System.Linq.IQueryable%601> jehož typ implementuje rozhraní nebo rozhraní. Standardní operátory dotazů poskytují možnosti dotazu, včetně filtrování, projekce, agregace, řazení a další.  
  
 Existují dvě sady linq standardní operátory dotazu, jeden, který pracuje na objekty typu <xref:System.Collections.Generic.IEnumerable%601> a druhý, který pracuje na objekty typu <xref:System.Linq.IQueryable%601>. Metody, které tvoří každou sadu jsou <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> statické členy a třídy, resp. Jsou definovány jako *rozšiřující metody* typu, na kterém pracují. To znamená, že mohou být volány pomocí syntaxe statické metody nebo syntaxe metody instance.  
  
 Kromě toho několik standardních metod operátoru dotazu <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601>pracovat na typy než ty, které jsou založeny na nebo . Typ <xref:System.Linq.Enumerable> definuje dvě takové metody, které pracují <xref:System.Collections.IEnumerable>na objekty typu . Tyto metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>a , umožňují povolit neparametrizované nebo neobecné kolekce, které mají být dotazovány ve vzoru LINQ. To provést vytvořením kolekce silného typu objektů. Třída <xref:System.Linq.Queryable> definuje dvě podobné <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> metody <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>a , které <xref:System.Linq.Queryable>pracují s objekty typu .  
  
 Standardní operátory dotazu se liší v časování jejich provádění, v závislosti na tom, zda vrátí hodnotu singleton nebo posloupnost hodnot. Tyto metody, které vracejí hodnotu singleton (například <xref:System.Linq.Enumerable.Average%2A> a <xref:System.Linq.Enumerable.Sum%2A>) se spustí okamžitě. Metody, které vrátí pořadí odložit spuštění dotazu a vrátit výčtu objektu.  
  
 V případě metod, které pracují na in-memory kolekce, to <xref:System.Collections.Generic.IEnumerable%601>znamená, že tyto metody, které rozšiřují , vrácené výčtu objektu zachycuje argumenty, které byly předány metodě. Pokud je tento objekt výčtu, logika operátoru dotazu je zaměstnán a jsou vráceny výsledky dotazu.  
  
 Naproti tomu metody, <xref:System.Linq.IQueryable%601> které rozšiřují neimplementují žádné dotazování chování, ale vytvořit strom výraz, který představuje dotaz, který má být proveden. Zpracování dotazu je zpracována zdrojový <xref:System.Linq.IQueryable%601> objekt.  
  
 Volání metod dotazu lze zřetězit společně v jednom dotazu, který umožňuje dotazy stát libovolně složité.  
  
 Následující příklad kódu ukazuje, jak lze standardní operátory dotazu použít k získání informací o posloupnosti.  
  
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
 Některé z nejčastěji používaných operátorů standardní dotaz mají vyhrazené C# a Visual Basic jazyk syntaxe, která umožňuje jejich volání jako součást *výrazu* *dotazu* . Další informace o standardních operátorech dotazů, které mají vyhrazená klíčová slova a odpovídající syntaxe, naleznete [v tématu Syntaxe výrazu dotazu pro operátory standardních dotazů (C#).](./query-expression-syntax-for-standard-query-operators.md)  
  
## <a name="extending-the-standard-query-operators"></a>Rozšíření operátorů standardních dotazů  
 Sadu standardních operátorů dotazů můžete rozšířit vytvořením metod specifických pro doménu, které jsou vhodné pro cílovou doménu nebo technologii. Můžete také nahradit operátory standardní dotazů vlastními implementacemi, které poskytují další služby, jako je vzdálené vyhodnocení, překlad dotazů a optimalizace. Viz <xref:System.Linq.Enumerable.AsEnumerable%2A> příklad.  
  
## <a name="related-sections"></a>Související oddíly  
 Následující odkazy přejdete na témata, která poskytují další informace o různých operátorech standardnídotaz na základě funkce.  
  
 [Řazení dat (C#)](./sorting-data.md)  
  
 [Nastavit operace (C#)](./set-operations.md)  
  
 [Filtrování dat (C#)](./filtering-data.md)  
  
 [Operace kvantifikátoru (C#)](./quantifier-operations.md)  
  
 [Projekční operace (C#)](./projection-operations.md)  
  
 [Dělení dat (C#)](./partitioning-data.md)  
  
 [Operace spojení (C#)](./join-operations.md)  
  
 [Seskupování dat (C#)](./grouping-data.md)  
  
 [Operace generování (C#)](./generation-operations.md)  
  
 [Operace rovnosti (C#)](./equality-operations.md)  
  
 [Operace prvku (C#)](./element-operations.md)  
  
 [Převod datových typů (C#)](./converting-data-types.md)  
  
 [Zřetězení (C#)](./concatenation-operations.md)  
  
 [Operace agregace (C#)](./aggregation-operations.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Úvod do dotazů LINQ (C#)](./introduction-to-linq-queries.md)
- [Syntaxe výrazu dotazu pro standardní operátory dotazů (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Klasifikace operátorů standardních dotazů podle způsobu spuštění (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Metody rozšíření](../../classes-and-structs/extension-methods.md)
