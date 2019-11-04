---
title: odkaz na C#
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 08f964b1e5c78a429dc50f81398d840f58ec4b13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422841"
---
# <a name="do-c-reference"></a>do (Referenční dokumentace jazyka C#)

Příkaz `do` spustí příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true`. Vzhledem k tomu, že tento výraz je vyhodnocen po každém spuštění smyčky, spustí se `do-while` cyklus jednou nebo vícekrát. To se liší od smyčky [while](while.md) , která se spouští nula nebo vícekrát.

V jakémkoli okamžiku v rámci bloku příkazu `do` lze rozdělit smyčku pomocí příkazu [Break](break.md) .

Můžete krokovat přímo s vyhodnocením výrazu `while` pomocí příkazu [Continue](continue.md) . Pokud se výraz vyhodnotí jako `true`, vykonání pokračuje v prvním příkazu smyčky. V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.

Můžete také ukončit `do-while` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje použití příkazu `do`. Vyberte **Spustit** a spusťte ukázkový kód. Potom můžete kód upravit a znovu spustit.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části do [příkazu](~/_csharplang/spec/statements.md#the-do-statement) do ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [while – příkaz](while.md)
