---
title: Metody rozšíření (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 80ecca30b534591ffb2633ade961425f694403f7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192194"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozšíření (Průvodce programováním v C#)
Metody rozšíření umožňují „přidávat“ metody ke stávajícím typům bez vytváření nového odvozeného typu, rekompilace nebo jiné změny původního typu. Metody rozšíření jsou zvláštním druhem statické metody, jsou však volány tak, jako kdyby byly metodami instance rozšířeného typu. Klientský kód napsaný v jazyce C#, F # a Visual Basic neexistuje žádný zjevný rozdíl mezi voláním metody rozšíření a metody, které jsou ve skutečnosti definovány v rámci typu.  
  
 Nejběžnějšími metodami rozšíření jsou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operátory standardního dotazu, které přidávají funkce dotazu ke stávající <xref:System.Collections.IEnumerable?displayProperty=nameWithType> a <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typy. Pokud chcete použít operátory standardního dotazu, nejdříve je převeďte do rozsahu pomocí `using System.Linq` směrnice. Poté bude libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> zřejmě má metody instance <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>, a tak dále. Zobrazí se tyto další metody v doplňování příkazů IntelliSense po zadání "tečky" za instanci typu <xref:System.Collections.Generic.IEnumerable%601> jako <xref:System.Collections.Generic.List%601> nebo <xref:System.Array>.  
  
 Následující příklad ukazuje, jak volat operátor standardního dotazu `OrderBy` metodu na pole celých čísel. Výraz v závorkách je výraz lambda. Velký počet operátorů standardního dotazu používá výrazy lambda jako parametry. To však metody rozšíření nepožadují. Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]  
  
 Metody rozšíření jsou definovány jako statické metody, ale jsou volány pomocí syntaxe metody instance. První parametr určuje, jakým typem metoda pracuje, a parametru předchází [to](../../../csharp/language-reference/keywords/this.md) modifikátor. Rozšiřující metody jsou pouze v rozsahu, kdy explicitně importujete obor názvů do zdrojového kódu s `using` směrnice.  
  
 Následující příklad ukazuje metodu rozšíření definovanou pro <xref:System.String?displayProperty=nameWithType> třídy. Tato třída je definována uvnitř nevnořené, neobecné statické třídy:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]  
  
 `WordCount` – Metoda rozšíření může být přenesena do rozsahu pomocí této `using` – direktiva:  
  
```csharp  
using ExtensionMethods;  
```  
  
 A může být volána z aplikace pomocí následující syntaxe:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 V kódu je možné vyvolat metodu rozšíření pomocí syntaxe metody instance. Jazyk IL (Intermediate Language) generovaný kompilátorem však přeloží váš kód do volání statické metody. Princip zapouzdření tedy není ve skutečnosti porušen. Metody rozšíření ve skutečnosti nemají přístup k proměnným v typu, který rozšiřují.  
  
 Další informace najdete v tématu [postupy: implementace a volání vlastní metody rozšíření](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).  
  
 Metody rozšíření budete pravděpodobně mnohem častěji volat, než implementovat své vlastní. Vzhledem k tomu, že metody rozšíření jsou volány pomocí syntaxe metody instance, není vyžadována žádná zvláštní znalost, abyste je mohli použít v klientském kódu. Pokud chcete povolit rozšíření metod pro konkrétní typ, stačí přidat elementy `using` direktivu pro obor názvů, ve kterém jsou definovány metody. Například pokud chcete použít operátory standardního dotazu, přidejte tuto `using` direktiv kódu:  
  
```csharp  
using System.Linq;  
```  
  
 (Budete také pravděpodobně muset přidat odkaz na knihovnu System.Core.dll.) Všimnete si, že operátory standardního dotazu se nyní zobrazí v IntelliSense jako další metody dostupné pro většinu <xref:System.Collections.Generic.IEnumerable%601> typy.  
  
> [!NOTE]
>  Ačkoli standardní operátory dotazu se nezobrazí v technologii IntelliSense pro <xref:System.String>, jsou stále k dispozici.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Vytváření vazeb na metody rozšíření v době kompilace  
 Metody rozšíření můžete použít k rozšíření třídy nebo rozhraní, nikoli však k jejich přepsání. Metoda rozšíření se stejným názvem a signaturou, jako má rozhraní nebo metoda třídy, nebude nikdy volána. V době kompilace mají metody rozšíření vždy nižší prioritu než metody instance definované v samotném typu. Jinými slovy, pokud typ nemá pojmenovanou metodu `Process(int i)`a máte rozšiřující metodu se stejnou signaturou, kompilátor vytvoří vždy vazbu na metodu instance. Pokud kompilátor narazí na vyvolání metody, nejprve vyhledá shodu v metodách instance tohoto typu. Pokud není nalezena žádná shoda, budou vyhledány jakékoli metody rozšíření, které jsou definovány pro daný typ, a budou připojeny k první vyhledané metodě rozšíření. Následující příklad znázorňuje, jakým způsobem kompilátor určuje, se kterou metodou rozšíření nebo metodou instance má vytvořit vazbu.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje pravidla, které u kompilátoru jazyka C# určují, zda vytvořit vazbu volání metody s metodou instance v rámci typu, nebo s metodou rozšíření. Statická třída `Extensions` obsahuje metody rozšíření definované pro každý typ, který implementuje `IMyInterface`. Třídy `A`, `B`, a `C` implementují rozhraní.  
  
 `MethodB` – Metoda rozšíření se nikdy nevolá, protože jeho název a signaturu přesně shodují s metodami již implementovanými třídami.  
  
 Pokud kompilátor nemůže najít metodu instance s odpovídající signaturou, vytvoří vazbu s odpovídající metodou rozšíření, je-li k dispozici.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]  
  
## <a name="general-guidelines"></a>Obecné pokyny  
 Většinou doporučujeme implementovat metody rozšíření opatrně a pouze tehdy, je-li to třeba. Kdykoli to je možné, měl by klientský kód, který musí rozšířit stávající typ, provést toto rozšíření vytvořením nového typu odvozeného ze stávajícího typu. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Pokud použijete metodu rozšíření k rozšíření typu, jehož zdrojový kód nelze změnit, podstupujete riziko, že změna implementace typu způsobí poškození metody rozšíření.  
  
 Pokud implementujete metody rozšíření pro daný typ, mějte na paměti následující body:  
  
-   Metoda rozšíření nebude nikdy volána, pokud má stejnou signaturu jako metoda definovaná v typu.  
  
-   Dále jsou metody rozšíření přeneseny do rozsahu na úrovni oboru názvů. Například, pokud máte větší počet statických tříd, které obsahují rozšiřující metody do jednoho oboru názvů s názvem `Extensions`, se budou všechny přeneseny do rozsahu pomocí `using Extensions;` směrnice.  
  
 Chcete-li zamezit zvýšení čísla verze sestavení, neměli byste pro implementovanou knihovnu metody rozšíření používat. Pokud chcete přidat významné funkce do knihovny, jejíž zdrojový kód vlastníte, měli byste postupovat podle standardních pokynů pro rozhraní .NET Framework pro správu verzí sestavení. Další informace najdete v tématu [Správa verzí sestavení](../../../../docs/framework/app-domains/assembly-versioning.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Ukázky paralelního programování (včetně mnoha příkladů metod rozšíření)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)  
- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Přehled standardních operátorů dotazu](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Pravidla převodu pro instanci parametrů a jejich dopad](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)  
- [Interoperabilita metod rozšíření mezi jazyky](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)  
- [Metody rozšíření a Curryfikované delegáty](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)  
- [Rozšiřující metoda vazby a hlášení chyb](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
