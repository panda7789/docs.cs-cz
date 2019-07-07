---
title: '- operátory a operátory-= – C# odkaz'
ms.custom: seodec18
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
ms.openlocfilehash: 80603107beb708e76a2c7446f300d71ede411570
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609858"
---
# <a name="--and---operators-c-reference"></a>– operátory a operátory-= (C# odkaz)

`-` Operátor je podporován předdefinovaných číselných typů a [delegovat](../keywords/delegate.md) typy.

Informace o aritmetické operace `-` operátoru, najdete v článku [Unární plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor odčítání -](arithmetic-operators.md#subtraction-operator--) oddíly [aritmetické operátory](arithmetic-operators.md) článku.

## <a name="delegate-removal"></a>Odebrání delegátů

Pro operandy stejného [delegovat](../keywords/delegate.md) typ, `-` operátor vrátí instanci delegáta, který se vypočítává takto:

- Pokud jsou oba operandy jinou hodnotu než null a vyvolání seznamu zpracovával pravý operand je správné souvislých podseznam seznamu vyvolání levý operand, výsledek operace se nový seznam volání, která se získá tak, že odeberete zpracovával pravý operand položky ze seznamu vyvolání levý operand. Pokud operand pravé strany seznamu odpovídá několika dílčích souvislých v seznamu levý operand, je odebrán pouze odpovídající podseznam úplně vpravo. Pokud je odebrání výsledkem je seznam prázdný, výsledkem je `null`.

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- Pokud seznam vyvolání zpracovával pravý operand není správné souvislých podseznam seznamu vyvolání levý operand, výsledek operace je levý operand. Například odebráním delegáta, který není součástí vícesměrového vysílání delegáta neprovede žádnou akci a výsledkem beze změny vícesměrového vysílání delegáta.

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Předchozí příklad ukazuje také, že během delegáta instance odebrání delegátů jsou porovnány. Například delegáty, které jsou vytvářeny ze zkušební verze identických [výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné. Další informace o delegáta rovnosti, najdete v článku [delegovat operátory rovnosti](~/_csharplang/spec/expressions.md#delegate-equality-operators) část [ C# specifikace jazyka](../language-specification/index.md).

- Pokud je levý operand `null`, je výsledek operace `null`. Pokud je operand pravé strany `null`, výsledkem operace je levý operand.

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

Chcete-li kombinování delegátů, použijte [ `+` operátor](addition-operator.md#delegate-combination).

Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Operátor odčítání a přiřazení-=

Pomocí výrazu `-=` operátorů, například

```csharp
x -= y
```

je ekvivalentem

```csharp
x = x - y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.
  
Následující příklad ukazuje použití `-=` operátor:

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Můžete také použít `-=` operátor zadat metodu obslužné rutiny události při vy nemusíte podnikat odebrat [události](../keywords/event.md). Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ může [přetížení](operator-overloading.md) `-` operátor. Když do binárního souboru `-` je operátor přetížen, `-=` je také implicitně přetížený operátor. Uživatelem definovaný typ nejde přetížit explicitně `-=` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [unární operátor minus](~/_csharplang/spec/expressions.md#unary-minus-operator) a [operátor odčítání](~/_csharplang/spec/expressions.md#subtraction-operator) oddíly [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Delegáti](../../programming-guide/delegates/index.md)
- [Události](../../programming-guide/events/index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [+ a operátory +=](addition-operator.md)
