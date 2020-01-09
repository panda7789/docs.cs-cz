---
title: Continue – příkaz C# – reference
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713663"
---
# <a name="continue-c-reference"></a>continue (Referenční dokumentace jazyka C#)

Příkaz `continue` předá řízení další iteraci ohraničujícího příkazu [while](./while.md) [, do,](./do.md) [pro](./for.md)nebo [foreach](./foreach-in.md) , ve kterém se zobrazí.

## <a name="example"></a>Příklad

V tomto příkladu je čítač inicializován pro počítání od 1 do 10. Pomocí příkazu `continue` ve spojení s `(i < 9)`výrazů se příkazy mezi `continue` a koncem `for`ho textu přeskočí.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [break – příkaz](/cpp/cpp/break-statement-cpp)
