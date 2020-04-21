---
title: do - C# Odkaz
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 1d4323366e567dab4b27b07803d0c06e731611ce
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738910"
---
# <a name="do-c-reference"></a>do (Referenční dokumentace jazyka C#)

Příkaz `do` provede příkaz nebo blok příkazů, zatímco zadaný logický `true`výraz je vyhodnocen . Vzhledem k tomu, že tento výraz `do-while` je vyhodnocena po každém spuštění smyčky, smyčky provede jednou nebo vícekrát. To se liší od [while](while.md) smyčky, která provádí nula nebo vícekrát.

V libovolném `do` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí příkazu [break.](break.md)

Můžete krok přímo k vyhodnocení `while` výrazu pomocí [příkazu continue.](continue.md) Pokud výraz vyhodnotí `true`, spuštění pokračuje na první příkaz ve smyčce. V opačném případě provádění pokračuje na první příkaz po smyčky.

`do-while` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `do` příkazu. Chcete-li spustit ukázkový kód, vyberte **spustit.** Poté můžete kód upravit a znovu spustit.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [do prohlášení](~/_csharplang/spec/statements.md#the-do-statement) specifikace jazyka [C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [zatímco příkaz](while.md)
