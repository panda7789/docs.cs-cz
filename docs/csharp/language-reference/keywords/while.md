---
title: while (Referenční dokumentace jazyka C#)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: e3e9493b5371fbd6f53a779ba73743efc6d6e05b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514057"
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

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [while – příkaz (C++)](/cpp/cpp/while-statement-cpp)  
- [Příkazy iterace](iteration-statements.md)  
- [do – příkaz](do.md)  
