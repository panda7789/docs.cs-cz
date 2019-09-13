---
title: ?? a?? = operátory – C# referenční informace
ms.custom: seodec18
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
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924685"
---
# <a name="-and--operators-c-reference"></a>?? a?? = – operátoryC# (Reference)

Operátor `??` pro sjednocení hodnoty null vrátí hodnotu jeho levého operandu, pokud není `null`. v opačném případě vyhodnotí operand na pravé straně a vrátí výsledek. `??` Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.

K dispozici v C# 8,0 a novějším operátor `??=` přiřazení s hodnotou null přiřadí hodnotu jeho pravého operandu k jeho levému operandu pouze v případě, že je `null`operand na levé straně vyhodnocen. `??=` Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

Levý operand `??=` operátoru musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo element [indexeru](../../programming-guide/indexers/index.md) . Další informace o přiřazení pro slučování s hodnotou null najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

V C# 7,3 a starších verzích musí být typ levého operandu `??` operátoru buď odkazový typ, nebo [typ hodnoty s možnou hodnotou null](../../programming-guide/nullable-types/index.md). Počínaje C# 8,0 je tento požadavek nahrazen následujícím: typ levého operandu `??` operátorů a `??=` nemůže být typ hodnoty, která není null. Konkrétně můžete použít operátory slučování s hodnotou null s neomezenými parametry typu v C# 8,0 a novějším:

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

Operátory slučování s hodnotou null jsou asociativní zprava. To znamená, že výrazy ve formuláři

```csharp
a ?? b ?? c
d ??= e ??= f
```

se vyhodnotí jako

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Příklady

Operátory `??` a`??=` můžou být užitečné v následujících scénářích:

- Ve výrazech s [podmíněné operátory s null?. a ?[]](member-access-operators.md#null-conditional-operators--and-), můžete poskytnout alternativní výraz k vyhodnocení v případě, že je výsledek výrazu s operacemi null podmíněného operátoru nulového sjednocení `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Když pracujete s [typy hodnot s možnou hodnotou null](../../programming-guide/nullable-types/index.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte operátor pro sjednocení null k určení hodnoty, která se má zadat pro případ, že hodnota `null`typu s možnou hodnotou null je:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , pokud hodnota, která se má použít, když má být `null` hodnota typu s možnou hodnotou null výchozí hodnotou základního typu hodnoty.

- Počínaje C# 7,0 můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako pravý operand operátoru pro sjednocení s hodnotou null, aby byl kód pro kontrolu argumentu výstižnější:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  Předchozí příklad také ukazuje, jak pomocí [členů Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.

- Počínaje C# 8,0 můžete `??=` operátor použít k nahrazení kódu formuláře.

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

## <a name="operator-overloadability"></a>Přetížení operátoru

Operátory `??` a`??=` nemohou být přetíženy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace o `??` operátoru naleznete v části [operátor slučování null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [?. a ?[] operátory](member-access-operators.md#null-conditional-operators--and-)
- [?: – operátor](conditional-operator.md)
