---
title: continue prohlášení - C# Reference
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713663"
---
# <a name="continue-c-reference"></a>continue (Referenční dokumentace jazyka C#)

Příkaz `continue` předá řízení další iteraci ohraničující [while](./while.md), [do](./do.md), [for](./for.md)nebo [foreach](./foreach-in.md) příkaz, ve kterém se zobrazí.

## <a name="example"></a>Příklad

V tomto příkladu je inicializovánčí čítač počítat od 1 do 10. Pomocí `continue` příkazu ve spojení `(i < 9)`s výrazem `continue` jsou příkazy `for` mezi a koncem těla přeskočeny.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [break – příkaz](/cpp/cpp/break-statement-cpp)
