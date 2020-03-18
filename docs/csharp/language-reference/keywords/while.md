---
title: while - C# Reference
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: eb9aa2ea8d6b1c96e0be7d377f7c047194b598de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712790"
---
# <a name="while-c-reference"></a>while (Referenční dokumentace jazyka C#)

Příkaz `while` provede příkaz nebo blok příkazů, zatímco zadaný logický `true`výraz je vyhodnocen . Vzhledem k tomu, že tento výraz `while` je vyhodnocenpřed každým spuštěním smyčky, smyčka provede nula nebo vícekrát. To se liší od [smyčky do,](do.md) která se provádí jednou nebo vícekrát.

V libovolném `while` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí příkazu [break.](break.md)

Můžete krok přímo k vyhodnocení `while` výrazu pomocí [příkazu continue.](continue.md) Pokud výraz vyhodnotí `true`, spuštění pokračuje na první příkaz ve smyčce. V opačném případě provádění pokračuje na první příkaz po smyčky.

`while` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `while` příkazu. Chcete-li spustit ukázkový kód, vyberte **spustit.** Poté můžete kód upravit a znovu spustit.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [While statement](~/_csharplang/spec/statements.md#the-while-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [do příkaz](do.md)
