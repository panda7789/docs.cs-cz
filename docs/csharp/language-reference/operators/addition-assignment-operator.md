---
title: += – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: 5d48f2fe53a9bb6f781f8d35f1e0983bcaa30f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660174"
---
# <a name="-operator-c-reference"></a>+= – operátor (Referenční dokumentace jazyka C#)

Operátor přiřazení sčítání.

Pomocí výrazu `+=` operátorů, například

```csharp
x += y
```

je ekvivalentem

```csharp
x = x + y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.
  
Pro číselné typy [operátor sčítání](addition-operator.md) `+` kód vypočítá součet operandů. Pokud je jeden nebo oba operandy typu [řetězec](../keywords/string.md), zřetězí řetězcové reprezentace jeho operandy. Pro typy delegátů `+` operátor vrátí novou instanci delegáta, který je kombinací operandů.

Můžete také použít `+=` operátor zadat metodu obslužné rutiny události, když se přihlásíte k odběru [události](../keywords/event.md). Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

Následující příklad ukazuje použití `+=` operátor:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor sčítání](addition-operator.md) `+`, operátor přiřazení sčítání `+=` je implicitně přetížena. Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení sčítání.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) a [události přiřazení](~/_csharplang/spec/expressions.md#event-assignment) oddíly [ C# specifikace jazyka](../language-specification/index.md).
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Události](../../programming-guide/events/index.md)
- [Delegáti](../../programming-guide/delegates/index.md)
