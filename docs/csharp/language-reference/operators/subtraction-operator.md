---
title: '- a -= operátory - odkaz C#'
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
ms.openlocfilehash: 2017aade92e8d7ad2af7101a107122fa8d7b9e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847648"
---
# <a name="--and---operators-c-reference"></a>- a -= operátory (odkaz C#)

A `-` `-=` operátory jsou podporovány integrované [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) desetinnou a [delegací](../builtin-types/reference-types.md#the-delegate-type) typů.

Informace o operátoru `-` aritmetiky naleznete [unary plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a [odčítání operátor -](arithmetic-operators.md#subtraction-operator--) části [aritmetické operátory](arithmetic-operators.md) článku.

## <a name="delegate-removal"></a>Odebrání delegáta

Pro operandy stejného typu `-` [delegáta](../builtin-types/reference-types.md#the-delegate-type) operátor vrátí instanci delegáta, která je vypočtena takto:

- Pokud oba operandy jsou non-null a vvolací seznam pravé operand je správné souvislé podseznam seznamu vyvolání levé operand, výsledkem operace je nový seznam vyvolání, který je získán odebráním pravé operand položky ze seznamu vyvolání levého operandu. Pokud seznam pravého operandu odpovídá více sousedícím podseznamům v seznamu levostranných operandů, bude odebrán pouze odpovídající podseznam vpravo. Pokud má za následek odebrání prázdný `null`seznam, výsledek je .

  [!code-csharp-interactive[delegate removal](snippets/SubtractionOperator.cs#DelegateRemoval)]

- Pokud seznam vyvolání pravého operandu není řádným souvislým dílčím seznamem seznamu vyvolání levého operandu, je výsledkem operace levostranný operand. Například odebrání delegáta, který není součástí delegáta vícesměrového vysílání, neprovede nic a výsledkem je nezměněný delegát vícesměrového vysílání.

  [!code-csharp-interactive[delegate removal with no effect](snippets/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Předchozí příklad také ukazuje, že během delegáta odstranění delegáta instance jsou porovnány. Například delegáti, které jsou vyrobeny z vyhodnocení identické [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné. Další informace o rovnosti delegátů naleznete v části [Operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

- Pokud je `null`levostranný operand , je `null`výsledkem operace . Pokud je `null`pravostranný operand , výsledkem operace je levostranný operand.

  [!code-csharp-interactive[delegate removal and null](snippets/SubtractionOperator.cs#DelegateRemovalAndNull)]

Chcete-li kombinovat [ `+` ](addition-operator.md#delegate-combination)delegáty, použijte operátor .

Další informace o typech delegátů naleznete v tématu [Delegáti](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Operátor přiřazení odčítání -=

Výraz používající `-=` operátor, například

```csharp
x -= y
```

je ekvivalentem

```csharp
x = x - y
```

kromě `x` toho, že se vyhodnocuje pouze jednou.

Následující příklad ukazuje použití operátoru: `-=`

[!code-csharp-interactive[-= examples](snippets/SubtractionOperator.cs#SubtractAndAssign)]

Operátor můžete `-=` také použít k určení metody obslužné rutiny události, která má být odebrána při odhlášení z [odběru události](../keywords/event.md). Další informace naleznete v tématu [Jak se přihlásit k odběru a odhlásit z odběru událostí](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ může `-` [přetížit](operator-overloading.md) operátor. Když binární `-` operátor je přetížený, `-=` operátor je také implicitně přetížené. Uživatelem definovaný typ nemůže `-=` explicitně přetížit operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [unary minus operátor](~/_csharplang/spec/expressions.md#unary-minus-operator) a [odčítání operátor](~/_csharplang/spec/expressions.md#subtraction-operator) části [c# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Akce](../../programming-guide/events/index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [+ a += operátory](addition-operator.md)
