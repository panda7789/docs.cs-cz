---
title: '?: Operator - C# odkaz'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 53a867e46b02793df5ad5bd9ca5ef676d0653a2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974302"
---
# <a name="-operator-c-reference"></a>?: – Operátor (referenční dokumentace jazyka C#)

Podmiňovací operátor `?:`, běžně označované jako Ternární podmiňovací operátor vyhodnocuje logický výraz a vrátí výsledek vyhodnocení výrazu jeden ze dvou výrazů v závislosti na tom, jestli logický výraz vyhodnocen jako `true` nebo `false`. Počínaje C# 7.2, [ref podmíněný výraz](#conditional-ref-expression) vrátí odkaz na výsledek jednoho ze dvou výrazů.

Syntaxe pro podmiňovací operátor je následující:

```csharp
condition ? consequent : alternative
```

`condition` Výraz se musí vyhodnotit na `true` nebo `false`. Pokud `condition` vyhodnotí jako `true`, `consequent` výraz je vyhodnocen a výsledek bude výsledek operace. Pokud `condition` vyhodnotí jako `false`, `alternative` výraz je vyhodnocen a výsledek bude výsledek operace. Pouze `consequent` nebo `alternative` vyhodnocena.

Typ `consequent` a `alternative` musí být musí být stejné nebo existovat implicitní převod z jednoho typu na druhý.

Podmíněný operátor je asociativní zprava, to znamená, výraz ve tvaru

```csharp
a ? b : c ? d : e
```

je vyhodnocen jako

```csharp
a ? b : (c ? d : e)
```

Po ruce mnemotechnická, která vám pomůže si zapamatovat, jak tento operátor vyhodnocuje je s dotazem:

```
is this condition true ? yes : no
```

s? část operátor, který funguje jako otazník pro předchozí prohlášení a následný funguje jako logické odpověď na tuto otázku.

Následující příklad ukazuje použití podmíněný operátor:

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Ref podmíněný výraz

Počínaje C# 7.2, vám pomůže ref podmíněný výraz vrátí odkaz na výsledek jednoho ze dvou výrazů. Přiřadíte tento odkaz na [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnnou, nebo jej použít jako [odkazovat na návratovou hodnotu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` – metoda Parametr](../keywords/ref.md#passing-an-argument-by-reference).

Syntaxe ref podmíněného výrazu je následujícím způsobem:

```csharp
condition ? ref consequent : ref alternative
```

Stejně jako původní podmíněný operátor ref podmíněný výraz je vyhodnocen jako pouze jeden ze dvou výrazů: buď `consequent` nebo `alternative`.

V případě ref podmíněný výraz typu `consequent` a `alternative` se musí shodovat.

Následující příklad ukazuje použití ref podmíněný výraz:

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

Další informace najdete v tématu [Poznámka návrh funkce](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="conditional-operator-and-an-ifelse-statement"></a>Podmíněný operátor a `if..else` – příkaz

Použití podmíněného operátoru přes [if-else](../keywords/if-else.md) příkaz může způsobit stručnější kód v případech, když potřebujete podmíněně k výpočtu hodnoty. Následující příklad ukazuje dva způsoby, jak klasifikovat jako záporné nebo nezáporné celé číslo:

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Podmiňovací operátor nelze přetížit.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [Podmiňovací operátor](~/_csharplang/spec/expressions.md#conditional-operator) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [if-else – příkaz](../keywords/if-else.md)
- [Operátory ?. a ?[]](null-conditional-operators.md)
- [?? – operátor](null-coalescing-operator.md)
- [ref keyword](../keywords/ref.md)
