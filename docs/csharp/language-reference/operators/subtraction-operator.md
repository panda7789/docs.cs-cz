---
description: '- and-= Operators-reference jazyka C#'
title: '- and-= Operators-reference jazyka C#'
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 871067d8049c66f2b8d863987b668e5287b36911
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124692"
---
# <a name="--and---operators-c-reference"></a>-and-= – operátory (Referenční dokumentace jazyka C#)

`-`Operátory a `-=` jsou podporovány integrovanými čísly [integrálu](../builtin-types/integral-numeric-types.md) a typy s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .

Informace o aritmetickém `-` operátoru naleznete v tématu [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor odčítání –](arithmetic-operators.md#subtraction-operator--) oddíly v článku [aritmetické operátory](arithmetic-operators.md) .

## <a name="delegate-removal"></a>Odebrání delegáta

Pro operandy stejného typu [delegáta](../builtin-types/reference-types.md#the-delegate-type) `-` vrátí operátor instanci delegáta, která je vypočítána takto:

- Pokud jsou oba operandy nenulové a seznam vyvolání pravého operandu je správným souvislým podseznamem seznamu vyvolání na levém operandu, výsledkem operace je nový seznam vyvolání, který se získá odebráním položek operandu na pravé straně ze seznamu vyvolání operandu na levé straně. Pokud se v seznamu operandů na pravé straně shoduje více sousedících podseznamů v seznamu operandů na levé straně, bude odebrán pouze odpovídající podseznam. Pokud je výsledkem odebrání prázdný seznam, výsledek je `null` .

  [!code-csharp-interactive[delegate removal](snippets/shared/SubtractionOperator.cs#DelegateRemoval)]

- Pokud seznam volání na pravé straně operand není správným souvislým podseznamem seznamu vyvolání na levém operandu, výsledkem operace je operand na levé straně. Například odebrání delegáta, který není součástí delegáta vícesměrového vysílání, neprovede žádnou akci a dojde ke změně nezměněného delegáta vícesměrového vysílání.

  [!code-csharp-interactive[delegate removal with no effect](snippets/shared/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Předchozí příklad také ukazuje, že během porovnání instancí delegáta pro odebrání delegáta. Například delegáty vytvořené z vyhodnocení identických [výrazů lambda](lambda-expressions.md) nejsou stejné. Další informace o rovnosti delegátů naleznete v části [operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

- Pokud je operand na levé straně `null` , výsledkem operace je `null` . Pokud je operand na pravé straně `null` , výsledkem operace je operand na levé straně.

  [!code-csharp-interactive[delegate removal and null](snippets/shared/SubtractionOperator.cs#DelegateRemovalAndNull)]

Chcete-li kombinovat delegáty, použijte [ `+` operátor](addition-operator.md#delegate-combination).

Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Operátor přiřazení odčítání-=

Výraz, který používá `-=` operátor, například

```csharp
x -= y
```

je ekvivalentem

```csharp
x = x - y
```

s výjimkou, že `x` je vyhodnocena pouze jednou.

Následující příklad ukazuje použití `-=` operátoru:

[!code-csharp-interactive[-= examples](snippets/shared/SubtractionOperator.cs#SubtractAndAssign)]

Operátor můžete také použít `-=` k určení metody obslužné rutiny události, která se má odebrat, když zrušíte odběr [události](../keywords/event.md). Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `-` operátor. Při přetížení binárního `-` operátoru `-=` je operátor také implicitně přetížený. Uživatelsky definovaný typ nemůže explicitně přetížit `-=` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v částech [unární operátor minus](~/_csharplang/spec/expressions.md#unary-minus-operator) a [odčítání](~/_csharplang/spec/expressions.md#subtraction-operator) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Události](../../programming-guide/events/index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [+ a + = – operátory](addition-operator.md)
