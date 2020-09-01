---
description: v jazyce C# – referenční informace
title: v jazyce C# – referenční informace
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 97299f9ac6f2cdd6bbddf831b3ee2ad711935fbe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141865"
---
# <a name="while-c-reference"></a>while (Referenční dokumentace jazyka C#)

`while`Příkaz provede příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true` . Vzhledem k tomu, že tento výraz je vyhodnocen před každým spuštěním smyčky, `while` smyčka se provede nula nebo vícekrát. To se liší [od smyčky do, která se spouští](do.md) jednou nebo vícekrát.

V jakémkoli bodě `while` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) .

Můžete přímo Krokovat s vyhodnocením `while` výrazu pomocí příkazu [Continue](continue.md) . Pokud se výraz vyhodnotí jako `true` , vykonání pokračuje v prvním příkazu smyčky. V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.

Můžete také ukončit `while` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `while` příkazu. Vyberte **Spustit** a spusťte ukázkový kód. Potom můžete kód upravit a znovu spustit.

[!code-csharp-interactive[while loop example](snippets/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [while](~/_csharplang/spec/statements.md#the-while-statement) v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [do – příkaz](do.md)
