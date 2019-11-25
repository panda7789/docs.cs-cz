---
title: Rozšiřující metody – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 5cce8eb3ad36208c3d376bc8c94da484e9f9181e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971057"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozšíření (Průvodce programováním v C#)
Metody rozšíření umožňují „přidávat“ metody ke stávajícím typům bez vytváření nového odvozeného typu, rekompilace nebo jiné změny původního typu. Metody rozšíření jsou zvláštním druhem statické metody, jsou však volány tak, jako kdyby byly metodami instance rozšířeného typu. Pro kód klienta napsané C#v F# a Visual Basic neexistuje žádný zřejmý rozdíl mezi voláním metody rozšíření a metodami, které jsou ve skutečnosti definovány v typu.  
  
 Nejběžnější metody rozšíření jsou operátory pro dotazování [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Standard, které přidávají funkce dotazu do stávajících <xref:System.Collections.IEnumerable?displayProperty=nameWithType> a <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>ch typů. Chcete-li použít standardní operátory dotazu, nejprve je přeneste do rozsahu s `using System.Linq` direktivou. Pak jakýkoli typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>, se zobrazí jako metody instance, jako je například <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>a tak dále. Tyto další metody lze zobrazit v dokončování příkazů technologie IntelliSense, pokud zadáte "tečka" po instanci <xref:System.Collections.Generic.IEnumerable%601>ho typu, jako je <xref:System.Collections.Generic.List%601> nebo <xref:System.Array>.  
  
 Následující příklad ukazuje, jak volat standardní operátor dotazu `OrderBy` metodu v poli celých čísel. Výraz v závorkách je výraz lambda. Velký počet operátorů standardního dotazu používá výrazy lambda jako parametry. To však metody rozšíření nepožadují. Další informace naleznete v tématu [lambda výrazy](../statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Metody rozšíření jsou definovány jako statické metody, ale jsou volány pomocí syntaxe metody instance. Jejich první parametr určuje, na který typ metoda pracuje, a parametr je před [tímto](../../language-reference/keywords/this.md) modifikátorem. Metody rozšíření jsou v oboru pouze v případě, že explicitně importujete obor názvů do zdrojového kódu s direktivou `using`.  
  
 Následující příklad ukazuje metodu rozšíření definovanou pro třídu <xref:System.String?displayProperty=nameWithType>. Tato třída je definována uvnitř nevnořené, neobecné statické třídy:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 Metodu rozšíření `WordCount` lze uvést do rozsahu pomocí této `using` direktivy:  
  
```csharp  
using ExtensionMethods;  
```  
  
 A může být volána z aplikace pomocí následující syntaxe:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 V kódu je možné vyvolat metodu rozšíření pomocí syntaxe metody instance. Jazyk IL (Intermediate Language) generovaný kompilátorem však přeloží váš kód do volání statické metody. Princip zapouzdření tedy není ve skutečnosti porušen. Metody rozšíření ve skutečnosti nemají přístup k proměnným v typu, který rozšiřují.  
  
 Další informace naleznete v tématu [implementace a volání vlastní metody rozšíření](./how-to-implement-and-call-a-custom-extension-method.md).
  
 Metody rozšíření budete pravděpodobně mnohem častěji volat, než implementovat své vlastní. Vzhledem k tomu, že metody rozšíření jsou volány pomocí syntaxe metody instance, není vyžadována žádná zvláštní znalost, abyste je mohli použít v klientském kódu. Chcete-li povolit metody rozšíření pro konkrétní typ, stačí přidat direktivu `using` pro obor názvů, ve kterém jsou metody definovány. Například pro použití standardních operátorů dotazu přidejte tuto `using` direktivu do kódu:  
  
```csharp  
using System.Linq;  
```  
  
 (Je také možné, že budete muset přidat odkaz na System. Core. dll.) Všimněte si, že standardní operátory dotazu se teď zobrazují v IntelliSense jako další metody dostupné pro většinu <xref:System.Collections.Generic.IEnumerable%601>ch typů.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Vytváření vazeb na metody rozšíření v době kompilace  
 Metody rozšíření můžete použít k rozšíření třídy nebo rozhraní, nikoli však k jejich přepsání. Metoda rozšíření se stejným názvem a signaturou, jako má rozhraní nebo metoda třídy, nebude nikdy volána. V době kompilace mají metody rozšíření vždy nižší prioritu než metody instance definované v samotném typu. Jinými slovy, pokud typ obsahuje metodu s názvem `Process(int i)`a máte metodu rozšíření se stejnou signaturou, kompilátor bude vždy svázán s metodou instance. Pokud kompilátor narazí na vyvolání metody, nejprve vyhledá shodu v metodách instance tohoto typu. Pokud není nalezena žádná shoda, budou vyhledány jakékoli metody rozšíření, které jsou definovány pro daný typ, a budou připojeny k první vyhledané metodě rozšíření. Následující příklad znázorňuje, jakým způsobem kompilátor určuje, se kterou metodou rozšíření nebo metodou instance má vytvořit vazbu.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje pravidla, které u kompilátoru jazyka C# určují, zda vytvořit vazbu volání metody s metodou instance v rámci typu, nebo s metodou rozšíření. Statická třída `Extensions` obsahuje metody rozšíření definované pro libovolný typ, který implementuje `IMyInterface`. Třídy `A`, `B`a `C` všechny implementují rozhraní.  
  
 Metoda rozšíření `MethodB` se nikdy nevolá, protože její název a signatura se přesně shodují s metodami, které už jsou implementované třídami.  
  
 Pokud kompilátor nemůže najít metodu instance s odpovídající signaturou, vytvoří vazbu s odpovídající metodou rozšíření, je-li k dispozici.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Obecné pokyny  
 Většinou doporučujeme implementovat metody rozšíření opatrně a pouze tehdy, je-li to třeba. Kdykoli to je možné, měl by klientský kód, který musí rozšířit stávající typ, provést toto rozšíření vytvořením nového typu odvozeného ze stávajícího typu. Další informace najdete v tématu [Dědičnost](./inheritance.md).  
  
 Pokud použijete metodu rozšíření k rozšíření typu, jehož zdrojový kód nelze změnit, podstupujete riziko, že změna implementace typu způsobí poškození metody rozšíření.  
  
 Pokud implementujete metody rozšíření pro daný typ, mějte na paměti následující body:  
  
- Metoda rozšíření nebude nikdy volána, pokud má stejnou signaturu jako metoda definovaná v typu.  
  
- Dále jsou metody rozšíření přeneseny do rozsahu na úrovni oboru názvů. Například pokud máte více statických tříd, které obsahují metody rozšíření v jednom oboru názvů s názvem `Extensions`, budou všechny převedeny do rozsahu pomocí direktivy `using Extensions;`.  
  
 Chcete-li zamezit zvýšení čísla verze sestavení, neměli byste pro implementovanou knihovnu metody rozšíření používat. Pokud chcete přidat významné funkce do knihovny, jejíž zdrojový kód vlastníte, měli byste postupovat podle standardních pokynů pro rozhraní .NET Framework pro správu verzí sestavení. Další informace naleznete v tématu [Správa verzí sestavení](../../../standard/assembly/versioning.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Ukázky paralelního programování (zahrnuje mnoho ukázkových metod rozšíření)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Výrazy lambda](../statements-expressions-operators/lambda-expressions.md)
- [Přehled standardních operátorů dotazu](../concepts/linq/standard-query-operators-overview.md)
- [Pravidla převodu pro parametry instance a jejich dopad](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)
- [Interoperabilita metod rozšíření mezi jazyky](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)
- [Metody rozšíření a Delegáti curryfikované](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)
- [Vazba metody rozšíření a zasílání zpráv o chybách](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
