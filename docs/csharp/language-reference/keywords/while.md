---
title: while – C# odkaz
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 6e485bc80a213be6a5d0da8a00c8ca718f867efb
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222933"
---
# <a name="while-c-reference"></a>while (Referenční dokumentace jazyka C#)

`while` Příkaz opakuje příkaz nebo blok příkazů během zadaný logický výraz je vyhodnocen jako `true`. Vzhledem k tomu, že tento výraz je vyhodnocen před každým provedením smyčky, `while` cyklus se opakuje nulakrát nebo vícekrát. Tím se liší od [proveďte](do.md) smyčku, která spustí jednou nebo vícekrát.

Na libovolný bod v rámci `while` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu.

Přejdete přímo na vyhodnocení `while` výrazem s použitím [pokračovat](continue.md) příkazu. Pokud je výraz vyhodnocen `true`, běh programu pokračuje prvním příkazem ve smyčce. V opačném případě běh programu pokračuje prvním příkazem za smyčky.

Také můžete ukončit `while` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `while` příkazu. Vyberte **spustit** ke spuštění příkladu kódu. Potom můžete upravit kód a potom ho spusťte znovu.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [while – příkaz](~/_csharplang/spec/statements.md#the-while-statement) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Příkazy iterace](iteration-statements.md)
- [do – příkaz](do.md)