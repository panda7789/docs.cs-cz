---
title: Návratové hodnoty REF (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2979359f0ffafe46a62696485bbb87b211c1704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651237"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Podpora pro odkaz návratové hodnoty (Visual Basic)

Od verze 7.0 C#, podporuje jazyka C# *odkazovat návratové hodnoty*. Jeden způsob, jak pochopit návratové hodnoty odkazu je, že jsou opak argumenty, které se předávají pomocí odkazu na třídu metodě. Při úpravě argument předaný odkazem změny se projeví v hodnotu proměnné na volajícího. Při metodu návratovou hodnotu odkazu poskytne volající, změny provedené návratovou hodnotu odkazu volající projeví v datech zavolat metodu.

Vám autor metody s odkazem na návratové hodnoty, ale neumožňuje můžete využívat návratové hodnoty referenční dokumentace jazyka Visual Basic není povoleno. Jinými slovy můžete volat metodu s návratovou hodnotou odkaz a upravit že návratová hodnota a změny návratovou hodnotu odkazu se projeví v datech zavolat metodu.

## <a name="modifying-the-ref-return-value-directly"></a>Návratové hodnoty ref přímém upravování

Pro metody, které vždy úspěšné a mají ne `ByRef` parametry, můžete upravit přímo návratovou hodnotu odkazu. To provedete přiřazením nová hodnota výrazů, které vrátí odkaz na návratovou hodnotu. 

Definuje následující příklad jazyka C# `NumericValue.IncrementValue` metodu, která zvýší interní hodnotu a vrátí ji jako odkaz vrátit hodnotu. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Odkaz na návratové hodnoty je pak upraveném volající v následujícím příkladu jazyka Visual Basic. Všimněte si, že souladu se zásadami `NumericValue.IncrementValue` volání metody nepřiřazuje hodnotu do metody. Místo toho přiřadí hodnotu vrácenou hodnotu odkazu vrácený metodou.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Pomocí Pomocná metoda

V ostatních případech přímém upravování odkaz návratovou hodnotu volání metody nemusí být vždy žádoucí. Například metoda vyhledávání, která vrací řetězec nemusí vždy najít shodu. V takovém případě budete chtít upravit návratovou hodnotu odkazu pouze v případě, že je hledání úspěšné.

Následující příklad jazyka C# znázorňuje tento scénář. Definuje `Sentence` zahrnuje třídy, které jsou napsané v C# `FindNext` metoda, která vyhledá další aplikace word ve větě, která začíná je určený dílčí řetězec. Řetězec se vrátí jako odkaz vrátí hodnotu a `Boolean` předaná odkazu na metodu proměnná Určuje, zda byla hledání úspěšné. Návratovou hodnotu odkazu označuje volající nelze číst jenom vrácená hodnota; potvrdí také ho upravit, a že změna se odrazí v data obsažená v interně `Sentence` třídy.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Hodnota v tomto případě není spolehlivá, protože volání metody, které může selhat pro vyhledání shody a vrácení první slovo ve větě přímou úpravou odkaz na vrácení. V takovém případě volající upraví nechtěně první slovo věty. To může zabránit volající vrácení `null` (nebo `Nothing` v jazyce Visual Basic). Ale v takovém případě se pokouší změnit řetězec, jehož hodnota je `Nothing` vyvolá <xref:System.NullReferenceException>. Pokud může také možné volající vrácení <xref:System.String.Empty?displayProperty=nameWithType>, ale to vyžaduje, aby volající definujte proměnnou řetězec, jehož hodnota je <xref:System.String.Empty?displayProperty=nameWithType>. Při volající můžete upravit tento řetězec, úpravy samotné slouží žádný účel, protože upravené řetězec nemá žádný vztah k slova ve větě uložené `Sentence` třídy.

Nejlepší způsob, jak u tohoto scénáře je předat návratovou hodnotu odkazu s odkazem na metodu helper. Pomocná metoda poté obsahuje logiku pro určení, zda bylo úspěšné volání metody, a pokud neodpovídala, k úpravě vrátí odkaz na hodnotu. Následující příklad uvádí možné implementace.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Viz také

[Předávání argumentů podle hodnoty a podle reference](passing-arguments-by-value-and-by-reference.md)   
[Procedury v jazyce Visual Basic](index.md)   


