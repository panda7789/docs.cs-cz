---
title: '?: operátor - c# odkaz'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399516"
---
# <a name="-operator-c-reference"></a>?: operátor (odkaz C#)

Podmíněný operátor `?:`, označovaný také jako ternární podmíněný operátor, vyhodnotí logický výraz a vrátí výsledek jednoho ze dvou `true` výrazů v závislosti na tom, zda je logický výraz vyhodnocen nebo . `false`

Syntaxe podmíněného operátoru je následující:

```csharp
condition ? consequent : alternative
```

Výraz `condition` musí vyhodnotit `false`nebo `true` . Pokud `condition` je `true`vyhodnocen a výraz `consequent` je vyhodnocen a jeho výsledek se stane výsledkem operace. Pokud `condition` je `false`vyhodnocen a výraz `alternative` je vyhodnocen a jeho výsledek se stane výsledkem operace. Pouze `consequent` `alternative` nebo je vyhodnocováno.

Typ `consequent` a `alternative` musí být stejný nebo musí být implicitní převod z jednoho typu na druhý.

Podmíněný operátor je právo-asociativní, to znamená výraz formuláře

```csharp
a ? b : c ? d : e
```

je vyhodnocována jako

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Pomocí následujícího mnemotechnického zařízení si můžete zapamatovat, jak je podmíněný operátor vyhodnocován:
>
> ```text
> is this condition true ? yes : no
> ```

Následující příklad ukazuje použití podmíněného operátoru:

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Podmíněný výraz ref

Počínaje C# 7.2, [ref místní](../keywords/ref.md#ref-locals) nebo ref pouze pro čtení [místní](../keywords/ref.md#ref-readonly-locals) proměnné lze přiřadit podmíněně s podmíněným ref výraz. Podmíněný výraz ref můžete také použít jako [referenční vrácenou hodnotu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` argument metody](../keywords/ref.md#passing-an-argument-by-reference).

Syntaxe podmíněného výrazu ref je následující:

```csharp
condition ? ref consequent : ref alternative
```

Stejně jako původní podmíněný operátor vyhodnotí podmíněný ref výraz `consequent` pouze `alternative`jeden ze dvou výrazů: nebo .

V případě podmíněného ref výrazu `consequent` musí `alternative` být stejný typ a musí být stejný.

Následující příklad ukazuje použití podmíněného výrazu ref:

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Podmíněný operátor `if..else` a příkaz

Použití podmíněného operátoru namísto příkazu [if-else](../keywords/if-else.md) může mít za následek stručnější kód v případech, kdy potřebujete podmíněně vypočítat hodnotu. Následující příklad ukazuje dva způsoby klasifikace celé číslo jako negativní nebo nenegativní:

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ nemůže přetížit podmíněný operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) specifikace [jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o podmíněném výrazu ref naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [if-else prohlášení](../keywords/if-else.md)
- [?. A? [] operátory](member-access-operators.md#null-conditional-operators--and-)
- [?? A?? = operátory](null-coalescing-operator.md)
- [klíčové slovo ref](../keywords/ref.md)
