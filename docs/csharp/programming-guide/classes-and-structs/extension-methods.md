---
title: Metody rozšíření (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: bf25ddda2c7e381f0b43798b28179b18338d71cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozšíření (Průvodce programováním v C#)
Metody rozšíření umožňují „přidávat“ metody ke stávajícím typům bez vytváření nového odvozeného typu, rekompilace nebo jiné změny původního typu. Metody rozšíření jsou zvláštním druhem statické metody, jsou však volány tak, jako kdyby byly metodami instance rozšířeného typu. Pro klienta kód napsaný v jazyce C#, F # a Visual Basic není žádný zřejmá rozdíl mezi voláním metody rozšíření a metody, které jsou ve skutečnosti definované v typu.  
  
 Nejběžnější rozšiřující metody jsou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardní operátory dotazu které přidat dotazovacích funkcí do existující <xref:System.Collections.IEnumerable?displayProperty=nameWithType> a <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typy. Chcete-li používat standardní dotaz, nejprve byla v rozsahu s `using System.Linq` – direktiva. Potom žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> zdá se, jako má instance metody <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>a tak dále. Zobrazí se tyto další metody v dokončování IntelliSense když zadáte "dot" po instanci <xref:System.Collections.Generic.IEnumerable%601> zadejte například <xref:System.Collections.Generic.List%601> nebo <xref:System.Array>.  
  
 Následující příklad ukazuje způsob volání operátor standardní dotazu `OrderBy` metoda v poli celých čísel. Výraz v závorkách je výraz lambda. Velký počet operátorů standardního dotazu používá výrazy lambda jako parametry. To však metody rozšíření nepožadují. Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]  
  
 Metody rozšíření jsou definovány jako statické metody, ale jsou volány pomocí syntaxe metody instance. Jejich první parametr určuje, který typ metoda funguje na a parametr předchází [to](../../../csharp/language-reference/keywords/this.md) modifikátor. Rozšiřující metody jsou pouze v oboru, když importujete explicitně oboru názvů do zdrojového kódu se `using` – direktiva.  
  
 Následující příklad ukazuje metody rozšíření pro definována <xref:System.String?displayProperty=nameWithType> třídy. Tato třída je definována uvnitř nevnořené, neobecné statické třídy:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]  
  
 `WordCount` Metoda rozšíření můžete začlenění do oboru s tímto `using` – direktiva:  
  
```  
using ExtensionMethods;  
```  
  
 A může být volána z aplikace pomocí následující syntaxe:  
  
```  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 V kódu je možné vyvolat metodu rozšíření pomocí syntaxe metody instance. Jazyk IL (Intermediate Language) generovaný kompilátorem však přeloží váš kód do volání statické metody. Princip zapouzdření tedy není ve skutečnosti porušen. Metody rozšíření ve skutečnosti nemají přístup k proměnným v typu, který rozšiřují.  
  
 Další informace najdete v tématu [postupy: implementace a volání vlastní metody rozšíření](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).  
  
 Metody rozšíření budete pravděpodobně mnohem častěji volat, než implementovat své vlastní. Vzhledem k tomu, že metody rozšíření jsou volány pomocí syntaxe metody instance, není vyžadována žádná zvláštní znalost, abyste je mohli použít v klientském kódu. Pokud chcete povolit rozšiřující metody pro konkrétní typ, stačí přidat `using` direktivy pro obor názvů, ve kterém jsou definovány metody. Například pokud chcete použít standardní operátory dotazu, přidejte tuto `using` direktivy kódu:  
  
```  
using System.Linq;  
```  
  
 (Budete také pravděpodobně muset přidat odkaz na knihovnu System.Core.dll.) Si všimnete, že standardní operátory dotazu se nyní zobrazí v IntelliSense jako další metody pro většinu <xref:System.Collections.Generic.IEnumerable%601> typy.  
  
> [!NOTE]
>  I když standardní operátory dotazu se nezobrazí v IntelliSense pro <xref:System.String>, jsou stále k dispozici.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Vytváření vazeb na metody rozšíření v době kompilace  
 Metody rozšíření můžete použít k rozšíření třídy nebo rozhraní, nikoli však k jejich přepsání. Metoda rozšíření se stejným názvem a signaturou, jako má rozhraní nebo metoda třídy, nebude nikdy volána. V době kompilace mají metody rozšíření vždy nižší prioritu než metody instance definované v samotném typu. Jinými slovy, pokud typ má metodu s názvem `Process(int i)`a máte metody rozšíření se stejným podpisem, kompilátor bude vždy vázat na metodu instance. Pokud kompilátor narazí na vyvolání metody, nejprve vyhledá shodu v metodách instance tohoto typu. Pokud není nalezena žádná shoda, budou vyhledány jakékoli metody rozšíření, které jsou definovány pro daný typ, a budou připojeny k první vyhledané metodě rozšíření. Následující příklad znázorňuje, jakým způsobem kompilátor určuje, se kterou metodou rozšíření nebo metodou instance má vytvořit vazbu.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje pravidla, které u kompilátoru jazyka C# určují, zda vytvořit vazbu volání metody s metodou instance v rámci typu, nebo s metodou rozšíření. Statická třída `Extensions` obsahuje rozšiřující metody, které jsou definovány pro žádný typ, který implementuje `IMyInterface`. Třídy `A`, `B`, a `C` všechny implementovat rozhraní.  
  
 `MethodB` Rozšíření metoda je volána nikdy, protože jeho název a podpis přesně shodovat metody už implementované třídy.  
  
 Pokud kompilátor nemůže najít metodu instance s odpovídající signaturou, vytvoří vazbu s odpovídající metodou rozšíření, je-li k dispozici.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]  
  
## <a name="general-guidelines"></a>Obecné pokyny  
 Většinou doporučujeme implementovat metody rozšíření opatrně a pouze tehdy, je-li to třeba. Kdykoli to je možné, měl by klientský kód, který musí rozšířit stávající typ, provést toto rozšíření vytvořením nového typu odvozeného ze stávajícího typu. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Pokud použijete metodu rozšíření k rozšíření typu, jehož zdrojový kód nelze změnit, podstupujete riziko, že změna implementace typu způsobí poškození metody rozšíření.  
  
 Pokud budete implementovat rozšiřující metody pro daný typ, mějte na paměti následující body:  
  
-   Metoda rozšíření nebude nikdy volána, pokud má stejnou signaturu jako metoda definovaná v typu.  
  
-   Dále jsou metody rozšíření přeneseny do rozsahu na úrovni oboru názvů. Například, pokud máte více statických tříd, které obsahují rozšiřující metody v jeden obor názvů s názvem `Extensions`, budou všechny přejít do oboru ve `using Extensions;` – direktiva.  
  
 Chcete-li zamezit zvýšení čísla verze sestavení, neměli byste pro implementovanou knihovnu metody rozšíření používat. Pokud chcete přidat významné funkce do knihovny, jejíž zdrojový kód vlastníte, měli byste postupovat podle standardních pokynů pro rozhraní .NET Framework pro správu verzí sestavení. Další informace najdete v tématu [Správa verzí sestavení](../../../../docs/framework/app-domains/assembly-versioning.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Paralelní programování ukázky (patří sem mnoho příklad rozšiřující metody)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)  
 [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Přehled standardních operátorů dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [Převod pravidel pro instanci parametrů a jejich dopad](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)  
 [Rozšiřující metody vzájemná funkční spolupráce mezi jazyky](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)  
 [Rozšiřující metody a Curryfikované delegáti](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)  
 [Metody rozšíření vazby a zasílání zpráv o chybách](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
