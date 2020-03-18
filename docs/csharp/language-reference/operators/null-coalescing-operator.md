---
title: ?? A?? = operátory - odkaz C#
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847310"
---
# <a name="-and--operators-c-reference"></a>?? A?? = operátory (odkaz C#)

Null-coalescing operátor `??` vrátí hodnotu jeho levé operand, pokud `null`není ; v opačném případě vyhodnotí pravé operand a vrátí jeho výsledek. Operátor `??` nevyhodnotí jeho pravé operand, pokud levá operand vyhodnotí na non-null.

K dispozici v C# 8.0 a novější, null-coalescing přiřazení operátor `??=` přiřadí hodnotu jeho pravé operand u jeho levé `null`operandpouze v případě, že levé operandu vyhodnotí . Operátor `??=` nevyhodnotí jeho pravé operand, pokud levá operand vyhodnotí na non-null.

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

Levá operanda operátoru `??=` musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo [indexerový](../../programming-guide/indexers/index.md) prvek.

V C# 7.3 a starší typ levé operand `??` operátor u operátoru musí být buď [typ odkazu](../keywords/reference-types.md) nebo [typ hodnoty s možnou hodnotou s hodnotou.](../builtin-types/nullable-value-types.md) Počínaje C# 8.0, tento požadavek je nahrazen následující: typ levé operand `??` `??=` a operátory nemůže být typ hodnoty s nulou. Zejména počínaje C# 8.0, můžete použít null-coalescing operátory s parametry typu bez omezení:

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

Null-coalescing operátory jsou právo asociativní. To znamená, že výrazy formuláře

```csharp
a ?? b ?? c
d ??= e ??= f
```

jsou vyhodnocovány jako

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Příklady

A `??` `??=` operátory mohou být užitečné v následujících scénářích:

- Ve výrazech s [operátory s nulovými podmínkami ?. a ?[]](member-access-operators.md#null-conditional-operators--and-)můžete použít `??` operátor k poskytnutí alternativního výrazu k vyhodnocení v případě, že výsledek výrazu s nulovými podmíněnými operacemi je `null`:

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- Při práci s [typy hodnot s možnou hodnotou s hodnotou s možnou hodnotou null](../builtin-types/nullable-value-types.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte `??` operátor k určení hodnoty, která má být poskytnuta v případě, že hodnota typu s možnou hodnotou s možnou hodnotou null je `null`:

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  Metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> použijte, pokud by hodnota, která má `null` být použita, pokud je hodnota typu s hodnotou s možnou hodnotou null, měla být výchozí hodnotou základního typu hodnoty.

- Počínaje C# 7.0, můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako pravé operand `??` operátoru, aby kód kontroly argumentů stručnější:

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  Předchozí příklad také ukazuje, jak používat [členy s výrazem k](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definování vlastnosti.

- Počínaje c# 8.0, můžete `??=` použít operátor nahradit kód formuláře

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  s následujícím kódem:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Přetížení obsluhy

Operátory `??` `??=` a nemůže být přetížena.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace o `??` operátoru naleznete v [části null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).

Další informace o `??=` operátorovi naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [?. A? [] operátory](member-access-operators.md#null-conditional-operators--and-)
- [?: operátor](conditional-operator.md)
