---
title: Metody rozšíření – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: ce35ef4d4286310aa6c8b6e40c3a448b0d91ea7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937526"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozšíření (Průvodce programováním v C#)
Metody rozšíření umožňují „přidávat“ metody ke stávajícím typům bez vytváření nového odvozeného typu, rekompilace nebo jiné změny původního typu. Metody rozšíření jsou zvláštním druhem statické metody, jsou však volány tak, jako kdyby byly metodami instance rozšířeného typu. Pro kód klienta napsaný v jazyce C#, F# a Visual Basic neexistuje žádný zjevný rozdíl mezi voláním metody rozšíření a metodami, které jsou ve skutečnosti definovány v typu.  
  
 Nejběžnější metody rozšíření jsou linq standardní dotaz operátory, které <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> přidávají funkce dotazu na existující a typy. Chcete-li použít standardní operátory dotazu, `using System.Linq` nejprve je uvést do oboru pomocí směrnice. Pak libovolný typ, <xref:System.Collections.Generic.IEnumerable%601> který implementuje <xref:System.Linq.Enumerable.GroupBy%2A>zdá <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Average%2A>mít instance metody, jako je například , , a tak dále. Tyto další metody můžete vidět v příkazu IntelliSense dokončení, když <xref:System.Collections.Generic.IEnumerable%601> zadáte "tečka" za instanci typu, jako <xref:System.Collections.Generic.List%601> je například nebo <xref:System.Array>.  
  
 Následující příklad ukazuje, jak volat `OrderBy` metodu operátoru standardního dotazu v poli celá čísla. Výraz v závorkách je výraz lambda. Velký počet operátorů standardního dotazu používá výrazy lambda jako parametry. To však metody rozšíření nepožadují. Další informace naleznete v tématu [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Metody rozšíření jsou definovány jako statické metody, ale jsou volány pomocí syntaxe metody instance. Jejich první parametr určuje, na kterém typu metoda pracuje, a parametru předchází [tento](../../language-reference/keywords/this.md) modifikátor. Metody rozšíření jsou pouze v oboru, když explicitně importovat obor názvů do zdrojového kódu pomocí `using` směrnice.  
  
 Následující příklad ukazuje metodu rozšíření <xref:System.String?displayProperty=nameWithType> definovanou pro třídu. Tato třída je definována uvnitř nevnořené, neobecné statické třídy:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 Metoda `WordCount` rozšíření může být uvedena `using` do oblasti působnosti s touto směrnicí:  
  
```csharp  
using ExtensionMethods;  
```  
  
 A může být volána z aplikace pomocí následující syntaxe:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 V kódu je možné vyvolat metodu rozšíření pomocí syntaxe metody instance. Jazyk IL (Intermediate Language) generovaný kompilátorem však přeloží váš kód do volání statické metody. Princip zapouzdření tedy není ve skutečnosti porušen. Metody rozšíření ve skutečnosti nemají přístup k proměnným v typu, který rozšiřují.  
  
 Další informace naleznete v [tématu Jak implementovat a volat vlastní metodu rozšíření](./how-to-implement-and-call-a-custom-extension-method.md).
  
 Metody rozšíření budete pravděpodobně mnohem častěji volat, než implementovat své vlastní. Vzhledem k tomu, že metody rozšíření jsou volány pomocí syntaxe metody instance, není vyžadována žádná zvláštní znalost, abyste je mohli použít v klientském kódu. Chcete-li povolit metody rozšíření pro `using` určitý typ, stačí přidat direktivu pro obor názvů, ve kterém jsou definovány metody. Chcete-li například použít standardní operátory dotazů, přidejte tuto `using` direktivu do kódu:  
  
```csharp  
using System.Linq;  
```  
  
 (Možná budete muset také přidat odkaz na soubor System.Core.dll.) Všimněte si, že standardní operátory dotazů se nyní zobrazují <xref:System.Collections.Generic.IEnumerable%601> v aplikaci IntelliSense jako další metody, které jsou k dispozici pro většinu typů.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Vytváření vazeb na metody rozšíření v době kompilace  
 Metody rozšíření můžete použít k rozšíření třídy nebo rozhraní, nikoli však k jejich přepsání. Metoda rozšíření se stejným názvem a signaturou, jako má rozhraní nebo metoda třídy, nebude nikdy volána. V době kompilace mají metody rozšíření vždy nižší prioritu než metody instance definované v samotném typu. Jinými slovy, pokud má typ `Process(int i)`metodu s názvem a máte metodu rozšíření se stejným podpisem, kompilátor se vždy sváže s metodou instance. Pokud kompilátor narazí na vyvolání metody, nejprve vyhledá shodu v metodách instance tohoto typu. Pokud není nalezena žádná shoda, budou vyhledány jakékoli metody rozšíření, které jsou definovány pro daný typ, a budou připojeny k první vyhledané metodě rozšíření. Následující příklad znázorňuje, jakým způsobem kompilátor určuje, se kterou metodou rozšíření nebo metodou instance má vytvořit vazbu.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje pravidla, které u kompilátoru jazyka C# určují, zda vytvořit vazbu volání metody s metodou instance v rámci typu, nebo s metodou rozšíření. Statická `Extensions` třída obsahuje rozšiřující metody definované `IMyInterface`pro libovolný typ, který implementuje . `A`Třídy `B`, `C` a všechny implementovat rozhraní.  
  
 Metoda `MethodB` rozšíření je nikdy volána, protože její název a podpis přesně odpovídají metodám, které již byly implementovány třídami.  
  
 Pokud kompilátor nemůže najít metodu instance s odpovídající signaturou, vytvoří vazbu s odpovídající metodou rozšíření, je-li k dispozici.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Obecné pokyny  
 Většinou doporučujeme implementovat metody rozšíření opatrně a pouze tehdy, je-li to třeba. Kdykoli to je možné, měl by klientský kód, který musí rozšířit stávající typ, provést toto rozšíření vytvořením nového typu odvozeného ze stávajícího typu. Další informace naleznete v [tématu Dědičnost](./inheritance.md).  
  
 Pokud použijete metodu rozšíření k rozšíření typu, jehož zdrojový kód nelze změnit, podstupujete riziko, že změna implementace typu způsobí poškození metody rozšíření.  
  
 Pokud implementujete metody rozšíření pro daný typ, nezapomeňte na následující body:  
  
- Metoda rozšíření nebude nikdy volána, pokud má stejnou signaturu jako metoda definovaná v typu.  
  
- Dále jsou metody rozšíření přeneseny do rozsahu na úrovni oboru názvů. Například pokud máte více statických tříd, které obsahují `Extensions`metody rozšíření v jednom oboru `using Extensions;` názvů s názvem , budou všechny uvedeny do oboru směrnice.  
  
 Chcete-li zamezit zvýšení čísla verze sestavení, neměli byste pro implementovanou knihovnu metody rozšíření používat. Pokud chcete přidat významné funkce do knihovny, jejíž zdrojový kód vlastníte, měli byste postupovat podle standardních pokynů pro rozhraní .NET Framework pro správu verzí sestavení. Další informace naleznete v [tématu Správa verzí sestavení](../../../standard/assembly/versioning.md).  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Ukázky paralelního programování (mezi ně patří mnoho ukázkových metod rozšíření)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Lambda výrazy](../statements-expressions-operators/lambda-expressions.md)
- [Přehled standardních operátorů dotazu](../concepts/linq/standard-query-operators-overview.md)
- [Pravidla převodu parametrů instance a jejich dopad](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Metody rozšíření Interoperabilita mezi jazyky](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Rozšiřující metody a curried delegáti](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Vazby metody rozšíření a hlášení chyb](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
