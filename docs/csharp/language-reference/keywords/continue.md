---
title: Continue – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 6a409fe8c7fd07342138eac11bfd1766014da1bd
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948352"
---
# <a name="continue-c-reference"></a>continue (Referenční dokumentace jazyka C#)

`continue` Příkaz předá řízení do další iterace uzavření [při](../../../csharp/language-reference/keywords/while.md), [provést](../../../csharp/language-reference/keywords/do.md), [pro](../../../csharp/language-reference/keywords/for.md), nebo [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz, ve kterém se zobrazí.

## <a name="example"></a>Příklad

V tomto příkladu je inicializovat čítače počítat od 1 do 10. Pomocí `continue` příkaz ve spojení s výraz `(i < 9)`, příkazy mezi `continue` a na konci `for` body jsou přeskočeny.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[break – příkaz](/cpp/cpp/break-statement-cpp)  
[Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)