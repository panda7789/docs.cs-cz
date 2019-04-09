---
title: Návratové hodnoty REF (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: d0600f7d9030324160343e800c37e0f5e68bff61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133975"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Podpora pro referenční návratové hodnoty (Visual Basic)

Počínaje C# 7.0, C# jazyk podporuje *referenční návratové hodnoty*. Jedním ze způsobů na pochopení referenční návratové hodnoty je, že jsou opakem argumenty, které jsou předány podle odkazu na metodu. Když se upraví argument předaný odkazem, změny se projeví v hodnotu proměnné na volajícího. Když je metoda nabízí návratovou hodnotu odkazu na volající, změny provedené pro návratovou hodnotu odkaz na volajícím se projeví v data volané metody.

Visual Basic se nepovoluje, vám autor metody s odkazem na návratové hodnoty, ale umožní vám využívat referenční návratové hodnoty. Jinými slovy můžete volat metodu s návratovou hodnotou odkazu a upravit tuto návratovou hodnotu a návratovou hodnotu odkazu se projeví v datech volané metody.

## <a name="modifying-the-ref-return-value-directly"></a>Úpravy návratové hodnoty ref přímo

Pro metody, které vždy úspěšné a nemají `ByRef` parametry, návratová hodnota odkazu můžete upravovat přímo. To provedete tak, že přiřadíte novou hodnotu na výrazy, které vrátí odkaz na návratovou hodnotu. 

Následující C# příklad definuje `NumericValue.IncrementValue` metodu, která zvýší interní hodnotu a vrátí jej jako odkaz vracet hodnotu. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Odkaz na návratové hodnoty je pak upravit volající v následujícím příkladu jazyka Visual Basic. Všimněte si, že řádek s `NumericValue.IncrementValue` volání metody nepřiřazuje hodnotu metody. Místo toho přiřadí hodnotu odkazu návratovou hodnotu vrácenou metodou.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Použití pomocné metody

V ostatních případech přímo úpravy odkaz vrácenou hodnotu volání metody nemusí být vždy žádoucí. Například metoda hledání, která vrací řetězec nemusí vždy najít shodu. V takovém případě budete chtít změnit referenční návratové hodnoty pouze v případě, že je hledání úspěšné.

Následující C# příklad ukazuje tento scénář. Definuje `Sentence` třídy napsané v C# zahrnuje `FindNext` metodu, která najde ve větě, která začíná zadaným podřetězcem následující slovo. Řetězec se vrátí jako odkaz vrátí hodnotu a `Boolean` proměnné, které jsou předány podle odkazu na metodu označuje, zda bylo hledání úspěšné. Odkaz návratová hodnota označuje, že volající nelze číst pouze vrácené hodnoty; uživatel můžete také upravit jej a této změny se projeví v data obsažená v interně `Sentence` třídy.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Přímou úpravou odkaz na návratové hodnoty v tomto případě není spolehlivé, protože volání metody nemusí najít shodu a vrátí první slovo ve větě. V takovém případě se volající náhodně změnit první slovo věty. To může zabránit volajícím vrátí `null` (nebo `Nothing` v jazyce Visual Basic). Ale v takovém případě se pokus upravit řetězec, jehož hodnota je `Nothing` vyvolá <xref:System.NullReferenceException>. Pokud může také moci volajícím vrátí <xref:System.String.Empty?displayProperty=nameWithType>, ale vyžaduje to, že volající definovat proměnné řetězec, jehož hodnota je <xref:System.String.Empty?displayProperty=nameWithType>. Když volající můžete upravit tento řetězec, úpravy, samotný slouží žádný účel, protože změněný řetězec nemá žádný vztah k slova ve větě ukládaná `Sentence` třídy.

Nejlepší způsob, jak postupovat v těchto případech je předat vrácenou hodnotu odkazu s odkazem na metodu helper. Pomocná metoda pak obsahuje logiku k určení, zda volání metody bylo úspěšné, a pokud udělal, chcete-li změnit odkaz vrátit hodnotu. Následující příklad uvádí možnou implementaci.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Viz také:

- [Předávání argumentů podle hodnoty a podle reference](passing-arguments-by-value-and-by-reference.md)
- [Procedury v jazyce Visual Basic](index.md)
