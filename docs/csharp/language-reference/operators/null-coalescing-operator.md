---
description: ?? a?? = – operátory – Referenční dokumentace jazyka C#
title: ?? a?? = – operátory – Referenční dokumentace jazyka C#
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
ms.openlocfilehash: 273bc6d3a4c65c09dc600621b435bf0d1baea9e4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118283"
---
# <a name="-and--operators-c-reference"></a>?? a?? = – operátory (Referenční dokumentace jazyka C#)

Operátor pro sjednocení hodnoty null `??` vrátí hodnotu jeho levého operandu, pokud není `null` . v opačném případě vyhodnotí operand na pravé straně a vrátí výsledek. `??`Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.

K dispozici v jazyce C# 8,0 a novějším operátor přiřazení s hodnotou null `??=` přiřadí hodnotu jeho pravého operandu k levému operandu pouze v případě, že je operand na levé straně vyhodnocen `null` . `??=`Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.

[!code-csharp[null-coalescing assignment](snippets/shared/NullCoalescingOperator.cs#Assignment)]

Levý operand `??=` operátoru musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo element [indexeru](../../programming-guide/indexers/index.md) .

V C# 7,3 a starších verzích musí být typ levého operandu `??` operátoru buď [odkazový typ](../keywords/reference-types.md) , nebo [typ hodnoty s možnou hodnotou null](../builtin-types/nullable-value-types.md). Počínaje jazykem C# 8,0 je tento požadavek nahrazen následujícím: typ levého operandu `??` `??=` operátorů a nemůže být typ hodnoty, která není null. Konkrétně počínaje jazykem C# 8,0 můžete použít operátory slučování null s neomezenými parametry typu:

[!code-csharp[unconstrained type parameter](snippets/shared/NullCoalescingOperator.cs#UnconstrainedType)]

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

`??`Operátory a `??=` můžou být užitečné v následujících scénářích:

- Ve výrazech s [operátory podmíněné hodnoty null?. a? []](member-access-operators.md#null-conditional-operators--and-)můžete použít `??` operátor k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že výsledek výrazu s hodnotami s hodnotou null je `null` :

  [!code-csharp-interactive[with null-conditional](snippets/shared/NullCoalescingOperator.cs#WithNullConditional)]

- Když pracujete s [typy hodnot s možnou hodnotou null](../builtin-types/nullable-value-types.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte `??` operátor k určení hodnoty, která má být zadána pro případ, že hodnota typu s možnou hodnotou null je `null` :

  [!code-csharp-interactive[with nullable types](snippets/shared/NullCoalescingOperator.cs#WithNullableTypes)]

  Použijte <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metodu, pokud hodnota, která se má použít, když má být hodnota typu s možnou hodnotou null `null` výchozí hodnotou základního typu hodnoty.

- Počínaje jazykem C# 7,0 můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako pravý operand `??` operátoru k zajištění přesnější kódu pro kontrolu argumentu:

  [!code-csharp[with throw expression](snippets/shared/NullCoalescingOperator.cs#WithThrowExpression)]

  Předchozí příklad také ukazuje, jak pomocí [členů Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.

- Počínaje jazykem C# 8,0 můžete použít `??=` operátor k nahrazení kódu formuláře

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

Operátory `??` a `??=` nemohou být přetíženy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace o `??` operátoru naleznete v oddílu " [slučovací operátor null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) " [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o `??=` operátoru najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)
- [?: – operátor](conditional-operator.md)
