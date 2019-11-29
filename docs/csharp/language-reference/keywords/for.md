---
title: příkaz for – C# odkaz
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: fc6a23cabd93323cacc33dfc4388116881c1fc84
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552266"
---
# <a name="for-c-reference"></a>pro (C# referenční)

Příkaz `for` spustí příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true`.

V jakémkoli okamžiku v rámci bloku příkazu `for` lze rozdělit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) . Můžete také ukončit `for` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

## <a name="structure-of-the-for-statement"></a>Struktura příkazu `for`

Příkaz `for` definuje oddíly *inicializátoru*, *podmínky*a *iterátoru* :

```csharp
for (initializer; condition; iterator)
    body
```

Všechny tři oddíly jsou volitelné. Tělo smyčky je buď příkaz, nebo blok příkazů.

Následující příklad ukazuje příkaz `for` se všemi definovanými oddíly:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>Oddíl *inicializátoru*

Příkazy v sekci *inicializátoru* jsou spouštěny pouze jednou před vstupem do smyčky. Oddíl *inicializátoru* je jedním z následujících způsobů:

- Deklarace a inicializace proměnné lokální smyčky, k nimž nelze přicházet z vnější smyčky.

- Nula nebo více výrazů příkazů z následujícího seznamu oddělených čárkami:

  - příkaz [přiřazení](../operators/assignment-operator.md)

  - vyvolání metody

  - výraz pro [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo `i++`

  - výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například `--i` nebo `i--`

  - Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)

  - výraz [await](../operators/await.md)

Oddíl *inicializátoru* v předchozím příkladu deklaruje a inicializuje proměnnou místní smyčky `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>Oddíl *Condition*

Oddíl *podmínky* , pokud je přítomen, musí být logický výraz. Tento výraz je vyhodnocen před každou iterací smyčky. Pokud oddíl *Podmínka* není přítomen nebo je logický výraz vyhodnocen jako `true`, je provedena iterace další smyčky; v opačném případě se smyčka ukončí.

Oddíl *Condition* v předchozím příkladu určuje, zda se smyčka ukončí na základě hodnoty proměnné lokální smyčky:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>Oddíl *iterátoru*

Oddíl *iterátor* určuje, co se stane po každé iteraci těla smyčky. Oddíl *iterátoru* obsahuje nula nebo více následujících výrazů příkazu, které jsou odděleny čárkami:

- příkaz [přiřazení](../operators/assignment-operator.md)

- vyvolání metody

- výraz pro [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo `i++`

- výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například `--i` nebo `i--`

- Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)

- výraz [await](../operators/await.md)

Oddíl *iterátoru* v příkladu výše zvyšuje proměnnou místní smyčky:

```csharp
i++
```

## <a name="examples"></a>Příklady

Následující příklad znázorňuje několik méně běžných použití oddílu `for` příkazu: přiřazení hodnoty k proměnné vnější smyčky v sekci *inicializátoru* , vyvolání metody v *inicializátoru* a *iterátoru* oddíly a změny hodnot dvou proměnných v části *iterátor* . Vyberte **Spustit** a spusťte ukázkový kód. Potom můžete kód upravit a znovu spustit.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

Následující příklad definuje cyklus nekonečné `for`:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [for Statement](~/_csharplang/spec/statements.md#the-for-statement) tématu [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [foreach, in](foreach-in.md)
