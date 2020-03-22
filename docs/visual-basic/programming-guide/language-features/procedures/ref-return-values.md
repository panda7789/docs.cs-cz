---
title: Ref vrácené hodnoty
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186927"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Podpora referenčních vrácené hodnoty (Visual Basic)

Počínaje C# 7.0, jazyk C# podporuje *vrácené hodnoty odkazu*. Jedním ze způsobů, jak porozumět referenčním vráceným hodnotám, je, že jsou opakem argumentů, které jsou předány odkazem na metodu. Při změně argument u koncenní, změny se projeví v hodnotě proměnné na volajícím. Pokud metoda poskytuje referenční vrácenou hodnotu volajícímu, změny provedené referenční návratovou hodnotou volajícím se projeví v datech volané metody.

Visual Basic neumožňuje vytvářet metody s referenčními vrácenými hodnotami, ale umožňuje využívat referenční vrácené hodnoty. Jinými slovy můžete volat metodu s referenční vrácenou hodnotou a upravit vrácenou hodnotu a změny referenční vrácené hodnoty se projeví v datech volané metody.

## <a name="modifying-the-ref-return-value-directly"></a>Úprava vrácené hodnoty ref přímo

Pro metody, které vždy `ByRef` úspěšné a nemají žádné parametry, můžete upravit referenční vrácená hodnota přímo. To provést přiřazením nové hodnoty výrazy, které vrátí referenční vrácenou hodnotu.

Následující příklad jazyka C# `NumericValue.IncrementValue` definuje metodu, která zintácí vnitřní hodnotu a vrátí ji jako referenční vrácenou hodnotu.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Referenční vrácená hodnota je pak upravena volajícím v následujícím příkladu jazyka Visual Basic. Všimněte si, `NumericValue.IncrementValue` že řádek s voláním metody nepřiřazuje hodnotu metodě. Místo toho přiřadí hodnotu referenční vrácené hodnotě vrácené metodou.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Použití pomocné metody

V ostatních případech nemusí být vždy žádoucí změnit referenční vrácenou hodnotu volání metody přímo. Například metoda hledání, která vrací řetězec nemusí vždy najít shodu. V takovém případě chcete změnit vrácenou hodnotu odkazu pouze v případě, že hledání je úspěšné.

Následující příklad Jazyka C# ilustruje tento scénář. Definuje třídu `Sentence` napsanou v `FindNext` C# obsahuje metodu, která najde další slovo ve větě, která začíná zadaným podřetězcem. Řetězec je vrácen jako referenční vrácená `Boolean` hodnota a proměnná předaná odkazem na metodu označuje, zda bylo hledání úspěšné. Referenční vrácená hodnota označuje, že kromě čtení vrácené hodnoty volající také upravit a že změna se projeví v datech obsažených interně ve `Sentence` třídě.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Přímo úprava vrácená hodnota odkazu v tomto případě není spolehlivé, protože volání metody může selhat najít shodu a vrátit první slovo ve větě. V takovém případě volající neúmyslně upraví první slovo věty. Tomu může být zabráněno volajícívrací `null` (nebo `Nothing` v jazyce Visual Basic). Ale v takovém případě se pokouší teme `Nothing` změnit <xref:System.NullReferenceException>řetězec, jehož hodnota je vyvolá . Pokud by také zabránit volajícího <xref:System.String.Empty?displayProperty=nameWithType>vrácení , ale to vyžaduje, aby volající <xref:System.String.Empty?displayProperty=nameWithType>definovat řetězec proměnné, jehož hodnota je . Zatímco volající může upravit tento řetězec, samotná změna neslouží žádnému účelu, protože změněný `Sentence` řetězec nemá žádný vztah ke slovům ve větě uložené třídou.

Nejlepší způsob, jak zpracovat tento scénář je předat referenční vrácenou hodnotu odkazem na pomocnou metodu. Pomocná metoda pak obsahuje logiku k určení, zda volání metody proběhlo úspěšně, a pokud ano, změnit vrácenou hodnotu odkazu. Následující příklad poskytuje možné implementace.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Viz také

- [Předávání argumentů podle hodnoty a odkazu](passing-arguments-by-value-and-by-reference.md)
- [Procedury v jazyce Visual Basic](index.md)
