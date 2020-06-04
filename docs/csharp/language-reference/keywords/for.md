---
title: příkaz for – Referenční dokumentace jazyka C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: db7cecc697a9cc9e5ff6b94b78747b799ed7e505
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401898"
---
# <a name="for-c-reference"></a>for (Referenční dokumentace jazyka C#)

`for`Příkaz provede příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true` .

V jakémkoli bodě `for` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) . Můžete také ukončit `for` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

## <a name="structure-of-the-for-statement"></a>Struktura `for` příkazu

`for`Příkaz definuje oddíly *inicializátoru*, *podmínky*a *iterátoru* :

```csharp
for (initializer; condition; iterator)
    body
```

Všechny tři oddíly jsou volitelné. Tělo smyčky je buď příkaz, nebo blok příkazů.

Následující příklad ukazuje `for` příkaz se všemi definovanými oddíly:

[!code-csharp-interactive[for loop example](snippets/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>Oddíl *inicializátoru*

Příkazy v sekci *inicializátoru* jsou spouštěny pouze jednou před vstupem do smyčky. Oddíl *inicializátoru* je jedním z následujících způsobů:

- Deklarace a inicializace proměnné lokální smyčky, k nimž nelze přicházet z vnější smyčky.

- Nula nebo více výrazů příkazů z následujícího seznamu oddělených čárkami:

  - příkaz [přiřazení](../operators/assignment-operator.md)

  - vyvolání metody

  - výraz pro [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo`i++`

  - výraz pro [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například `--i` nebo`i--`

  - Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)

  - výraz [await](../operators/await.md)

Oddíl *inicializátoru* v předchozím příkladu deklaruje a inicializuje proměnnou lokální smyčky `i` :

```csharp
int i = 0
```

### <a name="the-condition-section"></a>Oddíl *Condition*

Oddíl *podmínky* , pokud je přítomen, musí být logický výraz. Tento výraz je vyhodnocen před každou iterací smyčky. Pokud oddíl *Podmínka* není přítomen nebo je logický výraz vyhodnocen jako `true` , je provedena iterace další smyčky. v opačném případě se smyčka ukončí.

Oddíl *Condition* v předchozím příkladu určuje, zda se smyčka ukončí na základě hodnoty proměnné lokální smyčky:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>Oddíl *iterátoru*

Oddíl *iterátor* určuje, co se stane po každé iteraci těla smyčky. Oddíl *iterátoru* obsahuje nula nebo více následujících výrazů příkazu, které jsou odděleny čárkami:

- příkaz [přiřazení](../operators/assignment-operator.md)

- vyvolání metody

- výraz pro [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo`i++`

- výraz pro [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například `--i` nebo`i--`

- Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)

- výraz [await](../operators/await.md)

Oddíl *iterátoru* v příkladu výše zvyšuje proměnnou místní smyčky:

```csharp
i++
```

## <a name="examples"></a>Příklady

Následující příklad znázorňuje několik méně běžných použití oddílu `for` příkazu: přiřazení hodnoty k proměnné vnější smyčky v sekci *inicializátoru* , vyvolání metody v částech *inicializátoru* a *iterátoru* a změna hodnot dvou proměnných v části *iterátor* . Vyberte **Spustit** a spusťte ukázkový kód. Potom můžete kód upravit a znovu spustit.

[!code-csharp-interactive[not typical for loop example](snippets/IterationKeywordsExamples.cs#6)]

Následující příklad definuje nekonečnou `for` smyčku:

[!code-csharp[infinite for loop example](snippets/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [for Statement](~/_csharplang/spec/statements.md#the-for-statement) tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [foreach, in](foreach-in.md)
