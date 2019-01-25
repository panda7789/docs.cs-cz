---
title: Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 5ad58e921b16498139abe403a45b21bb22ef895d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564315"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
Většina dotazů v úvodní Language Integrated Query ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) dokumentace jsou zapsány pomocí syntaxe deklarativní dotazů LINQ. Syntaxe dotazu však musí být převedeny do volání metod pro .NET common language runtime (CLR) při kompilaci kódu. Tato metoda volání vyvolat operátory standardního dotazu, které mají názvy, jako `Where`, `Select`, `GroupBy`, `Join`, `Max`, a `Average`. Můžete je volat přímo pomocí syntaxe metody místo syntaxe dotazu.  
  
 Syntaxe dotazů a syntaxe využívající metody jsou sémanticky identické, ale mnoho uživatelů zjišťuje syntaxe dotazu jednodušší a snadněji čitelné. Některé dotazy musí být vyjádřena jako volání metody. Například musíte použít volání metody vyjádřit dotaz, který načte počet prvků, které odpovídají zadané podmínce. Volání metody musíte použít také pro dotaz, který načte prvek, který obsahuje ve zdrojové sekvence maximální hodnotu. Referenční dokumentace pro operátory standardního dotazu v <xref:System.Linq> obor názvů používá Obecná syntaxe metody. Proto i v případě Začínáme zápis [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, je vhodné se seznámit s použití syntaxe využívající metody v dotazech a ve výrazech dotazů sami.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozšíření standardních operátorů dotazů  
 Následující příklad ukazuje jednoduchý *výrazu dotazu* a sémanticky ekvivalentní zapsán jako dotaz *založených na volání metody dotazu*.  
  
 [!code-csharp[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 Je stejný jako výstup z dva příklady. Vidíte, že je typ proměnné dotazu stejné v obou formách: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Informace o tom dotazů založených na volání metody, Podívejme se na to podrobněji. Na pravé straně výrazu, Všimněte si, že `where` klauzule nyní vyjádřený jako metodu instance na `numbers` má typ objektu, který bude odvolat při `IEnumerable<int>`. Pokud jste se seznámili s Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, víte, že nemá `Where` metody. Nicméně pokud vyvoláte seznamu doplňování technologie IntelliSense v integrovaném vývojovém prostředí sady Visual Studio, zobrazí se pouze `Where` metody, ale mnoho metod, jako `Select`, `SelectMany`, `Join`, a `Orderby`. Jedná se o všech standardních operátorů pro dotazování.  
  
 ![Operátory standardního dotazu v technologii Intellisense](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Přestože vypadá jako <xref:System.Collections.Generic.IEnumerable%601> podřízených zahrnout tyto další metody, ve skutečnosti nejedná o tento případ. Operátory standardního dotazu jsou implementovány jako nový typ metodu s názvem *rozšiřující metody*. Metody rozšíření "rozšířit" existující typ; může být volána jako kdyby byly metodami instance typu. Rozšíření standardních operátorů pro dotazování <xref:System.Collections.Generic.IEnumerable%601> a, který je proč můžete napsat `numbers.Where(...)`.  
  
 Abyste mohli začít používat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], vše, co musíte opravdu svůj přístup vědět o rozšiřujících metod je postup je převeďte do rozsahu ve vaší aplikaci s použitím správné `using` direktivy. Z vaší aplikace metody rozšíření a normální instanci metody jsou stejné.  
  
 Další informace o metodách rozšíření naleznete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Další informace o standardních operátorů pro dotazování, naleznete v tématu [přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md). Některé [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatelů, jako například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], implementovat vlastní standardních operátorů pro dotazování a další rozšiřující metody pro ostatní typy kromě <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Výrazy lambda  
 V předchozím příkladu, Všimněte si, že podmíněný výraz (`num % 2 == 0`) je předán jako argument v řádku `Where` metody: `Where(num => num % 2 == 0).` Tento výraz inline se nazývá výraz lambda. Je to pohodlný způsob, jak napsat kód, který byste jinak museli být napsány v těžkopádnější formuláře jako anonymní metody nebo obecný delegát nebo strom výrazů. V jazyce C# `=>` je operátor lambda, který je pro čtení jako "vloží do". `num` Na levé straně operátoru je vstupní proměnná, která odpovídá `num` ve výrazu dotazu. Kompilátor může odvodit typ `num` protože ví, `numbers` je obecný <xref:System.Collections.Generic.IEnumerable%601> typu. Tělo výrazu lambda je stejně jako výraz v syntaxi dotazů nebo v jiných výraz v C# nebo příkaz může obsahovat jiné komplexní logiku a volání metod. "Vrácená hodnota" je právě výsledku výrazu.  
  
 Abyste mohli začít používat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], není nutné důkladně použití výrazů lambda. Ale některé dotazy lze vyjádřit pouze v syntaxe využívající metody a některé vyžadují také výrazy lambda. Až se podrobněji seznamujete s výrazy lambda, zjistíte, že jsou výkonná a flexibilní nástroj v vaše [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sady nástrojů. Další informace najdete v tématu [výrazy Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Skládání dotazů  
 V předcházejícím příkladu, Všimněte si, že `OrderBy` pomocí operátoru tečka při volání je vyvolána metoda `Where`. `Where` Vytvoří filtrované posloupnost a potom `Orderby` funguje v této sekvenci, že je seřadíte. Protože vrátit dotazech `IEnumerable`, můžete vytvořit v syntaxe využívající metody ve zřetězení volání metod. Je to, co kompilátor provádí na pozadí při psaní dotazů pomocí syntaxe dotazu. A protože proměnné dotazu neukládá výsledky dotazu, můžete ho upravit nebo ho použít jako základ pro nový dotaz v okamžiku, přestože byl proveden.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
