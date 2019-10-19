---
title: Návratové hodnoty ref (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 7401fdd0fa876d21a87dbe9faf9d979e6b3bdc5c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581122"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Podpora pro návratové hodnoty odkazů (Visual Basic)

Počínaje C# 7,0 C# jazyk podporuje *návratové hodnoty odkazů*. Jedním ze způsobů, jak pochopit návratové hodnoty, je, že se jedná o opak argumentů, které jsou předány odkazem na metodu. Když je upraven argument předaný odkazem, změny se projeví v hodnotě proměnné volajícího. Když metoda poskytuje odkazovou návratovou hodnotu volajícímu, změny provedené v návratové hodnotě odkazu volajícím se projeví v datech volané metody.

Visual Basic neumožňuje vytvářet metody s návratovými hodnotami odkazů, ale umožňuje využívat návratové hodnoty odkazů. Jinými slovy, můžete zavolat metodu s návratovou hodnotou odkazu a změnit tuto návratovou hodnotu a změny návratové hodnoty odkazu se projeví v datech volané metody.

## <a name="modifying-the-ref-return-value-directly"></a>Změna návratové hodnoty REF přímo

Pro metody, které vždy úspěšné a nemají žádné parametry `ByRef`, lze návratovou hodnotu odkazu upravit přímo. Provedete to tak, že novou hodnotu přiřadíte výrazům, které vrátí návratovou hodnotu odkazu.

Následující C# příklad definuje metodu `NumericValue.IncrementValue`, která zvyšuje interní hodnotu a vrátí ji jako návratovou hodnotu odkazu.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Návratová hodnota odkazu je pak změněna volajícím v následujícím příkladu Visual Basic. Všimněte si, že řádek s voláním metody `NumericValue.IncrementValue` nepřiřazuje k metodě hodnotu. Místo toho přiřadí hodnotu návratové hodnotě odkazu vrácenou metodou.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Použití pomocné metody

V jiných případech se může stát, že změna návratové hodnoty zpětného volání metody přímo nemusí být vždy žádoucí. Například metoda hledání, která vrací řetězec, nemusí vždy najít shodu. V takovém případě je třeba změnit návratovou hodnotu odkazu pouze v případě, že je hledání úspěšné.

Následující C# příklad znázorňuje tento scénář. Definuje `Sentence` třídy napsané v C# zahrnuje metodu `FindNext`, která nalezne další slovo ve větě začínající zadaným podřetězcem. Řetězec je vrácen jako návratová hodnota odkazu a proměnná `Boolean` předaná odkazem na metodu označuje, zda bylo hledání úspěšné. Návratová hodnota odkazu označuje, že volající může číst pouze vrácenou hodnotu. může ho také upravit a tato úprava se projeví v datech, která jsou obsažena interně ve třídě `Sentence`.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Přímá změna návratové hodnoty reference v tomto případě není spolehlivá, protože volání metody může neúspěšné vyhledání shody a vrácení prvního slova ve větě. V takovém případě volající neúmyslně změní první slovo věty. To může zabránit volajícímu vracející `null` (nebo `Nothing` v Visual Basic). V takovém případě však došlo k pokusu o změnu řetězce, jehož hodnota je `Nothing` vyvolá <xref:System.NullReferenceException>. V případě, že je možné také zabránit volajícímu vracející <xref:System.String.Empty?displayProperty=nameWithType>, ale to vyžaduje, aby volající definoval řetězcovou proměnnou, jejíž hodnota je <xref:System.String.Empty?displayProperty=nameWithType>. I když volající může tento řetězec změnit, samotná změna neslouží k žádnému účelu, protože upravený řetězec nemá žádný vztah ke slovům ve větě uložené třídě `Sentence`.

Nejlepším způsobem, jak tento scénář zpracovat, je předat návratovou hodnotu odkazu odkazem na pomocnou metodu. Pomocná metoda poté obsahuje logiku pro zjištění, zda bylo volání metody úspěšné a v případě, že byla provedena, pro úpravu návratové hodnoty odkazu. Následující příklad poskytuje možnou implementaci.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Viz také:

- [Předávání argumentů podle hodnoty a odkazu](passing-arguments-by-value-and-by-reference.md)
- [Procedury v jazyce Visual Basic](index.md)
