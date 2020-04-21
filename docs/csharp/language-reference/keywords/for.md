---
title: for statement - odkaz C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: cb83fa015eea19b156faebb5bed18cc1f0970cc1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738798"
---
# <a name="for-c-reference"></a>pro (odkaz C#)

Příkaz `for` provede příkaz nebo blok příkazů, zatímco zadaný logický `true`výraz je vyhodnocen .

V libovolném `for` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí [příkazu break](break.md) nebo krok k další iteraci ve smyčce pomocí [příkazu continue.](continue.md) `for` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)

## <a name="structure-of-the-for-statement"></a>Struktura `for` prohlášení

Příkaz `for` definuje *inicializátor*, *podmínku*a *oddíly iterátoru:*

```csharp
for (initializer; condition; iterator)
    body
```

Všechny tři části jsou volitelné. Tělo smyčky je buď příkaz nebo blok příkazů.

Následující příklad ukazuje `for` příkaz se všemi definovanými oddíly:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Inicializační* sekce

Příkazy v *inicializační* části jsou provedeny pouze jednou před vstupem do smyčky. *Inicializační* část je buď z následujících:

- Deklarace a inicializace proměnné účastnického vedení, ke které nelze získat přístup mimo smyčku.

- Nula nebo více výrazů příkazu z následujícího seznamu, oddělených čárkami:

  - [příkaz přiřazení](../operators/assignment-operator.md)

  - vyvolání metody

  - výraz [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo`i++`

  - výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo postfixu, například `--i` nebo`i--`

  - vytvoření objektu pomocí [nového](../operators/new-operator.md) operátoru

  - [await](../operators/await.md) výraz

*Inicializační* část ve výše uvedeném příkladu deklaruje a inicializuje proměnnou `i`účastnického připojení :

```csharp
int i = 0
```

### <a name="the-condition-section"></a>Část *podmínky*

Část *podmínky,* pokud je k dispozici, musí být logický výraz. Tento výraz je vyhodnocen před každou iteraci smyčky. Pokud oddíl *podmínky* není k dispozici nebo logický `true`výraz vyhodnotí , provede se další iterace smyčky; v opačném případě je smyčka ukončena.

Část *podmínky* ve výše uvedeném příkladu určuje, zda smyčka končí na základě hodnoty proměnné účastnického vedení:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>Sekce *iterátoru*

*Iterátor* část definuje, co se stane po každé iteraci těla smyčky. Sekce *iterátoru* obsahuje nulu nebo více následujících výrazů příkazu oddělených čárkami:

- [příkaz přiřazení](../operators/assignment-operator.md)

- vyvolání metody

- výraz [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo`i++`

- výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo postfixu, například `--i` nebo`i--`

- vytvoření objektu pomocí [nového](../operators/new-operator.md) operátoru

- [await](../operators/await.md) výraz

Část *iterátoru* ve výše uvedeném příkladu zintáží proměnnou účastnického vedení:

```csharp
i++
```

## <a name="examples"></a>Příklady

Následující příklad ilustruje několik méně běžných `for` použití oddílů příkazu: přiřazení hodnoty proměnné externí smyčky v části *inicializátoru,* vyvolání metody v oddílech *inicializátor* u *iterátoru* a změna hodnot dvou proměnných v části *iterátoru.* Chcete-li spustit ukázkový kód, vyberte **spustit.** Poté můžete kód upravit a znovu spustit.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

Následující příklad definuje nekonečnou `for` smyčku:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [for statement](~/_csharplang/spec/statements.md#the-for-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [foreach, in](foreach-in.md)
