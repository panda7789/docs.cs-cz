---
title: do - C# odkaz
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 4bdbd1c8efac0b7ba95d4c8d16dae3101fe6bcb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661786"
---
# <a name="do-c-reference"></a>do (Referenční dokumentace jazyka C#)

`do` Příkaz opakuje příkaz nebo blok příkazů během zadaný logický výraz je vyhodnocen jako `true`. Vzhledem k tomu, že tento výraz je vyhodnocen po každém spuštění smyčky, `do-while` cyklus se opakuje, jednou nebo vícekrát. Tím se liší od [při](while.md) smyčku, která spustí nulakrát nebo vícekrát.

Na libovolný bod v rámci `do` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu.

Přejdete přímo na vyhodnocení `while` výrazem s použitím [pokračovat](continue.md) příkazu. Pokud je výraz vyhodnocen `true`, běh programu pokračuje prvním příkazem ve smyčce. V opačném případě běh programu pokračuje prvním příkazem za smyčky.

Také můžete ukončit `do-while` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `do` příkazu. Vyberte **spustit** ke spuštění příkladu kódu. Potom můžete upravit kód a potom ho spusťte znovu.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [proveďte příkaz](~/_csharplang/spec/statements.md#the-do-statement) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Příkazy iterace](iteration-statements.md)
- [while – příkaz](while.md)
