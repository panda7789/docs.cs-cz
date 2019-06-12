---
title: ?? Operator - C# odkaz
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: a19b5558da36ffb11dabd1b9bec419a3623a0f17
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024990"
---
# <a name="-operator-c-reference"></a>?? – operátor (C# odkaz)

Operátoru nulového sjednocení `??` vrací hodnotu svého operandu vlevo, pokud není `null`; v opačném případě zpracovával pravý operand vyhodnotí a vrátí její výsledek. `??` Operátor nevyhodnocuje jeho zpracovával pravý operand, pokud levý operand je vyhodnocen jako nenulové.

Operátoru nulového sjednocení je asociativní zprava, to znamená, výraz ve tvaru

```csharp
a ?? b ?? c
```

je vyhodnocen jako

```csharp
a ?? (b ?? c)
```

`??` Operátor může být užitečné v následujících scénářích:

- Ve výrazech s [podmíněné operátory s null?. a?] ](member-access-operators.md#null-conditional-operators--and-), můžete poskytnout alternativní výraz k vyhodnocení v případě, že je výsledek výrazu s operacemi null podmíněného operátoru nulového sjednocení `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Při práci s [typy s možnou hodnotou](../../programming-guide/nullable-types/index.md) a je nutné zadat hodnotu podkladového typu hodnoty, zadejte hodnotu zadejte v případě, že je hodnota s možnou hodnotou Null typu pomocí operátoru nulového sjednocení `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Použití <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metoda Pokud hodnota, která má použít, pokud je hodnota s možnou hodnotou Null typu `null` musí mít výchozí hodnotu podkladového typu hodnoty.

- Počínaje C# 7.0, můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako operand pravé strany operátoru nulového sjednocení, aby byl kód kontroluje argument stručnější:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  V předchozím příkladu také ukazuje, jak používat [členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.

## <a name="operator-overloadability"></a>Overloadability – operátor

Operátoru nulového sjednocení nemohou být přetíženy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [null operátor sloučení](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [?. a? operátory]](member-access-operators.md#null-conditional-operators--and-)
- [?: – operátor](conditional-operator.md)
