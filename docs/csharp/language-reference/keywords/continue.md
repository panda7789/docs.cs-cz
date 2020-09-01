---
description: Continue – příkaz – reference jazyka C#
title: Continue – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 76578b0ad7e2b969609fbf50df1f9ab7de6e5097
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128436"
---
# <a name="continue-c-reference"></a>continue (Referenční dokumentace jazyka C#)

`continue`Příkaz předá řízení následující iteraci ohraničujícího příkazu [while](./while.md), do [,](./do.md) [pro](./for.md)nebo [foreach](./foreach-in.md) , ve kterém se zobrazí.

## <a name="example"></a>Příklad

V tomto příkladu je čítač inicializován pro počítání od 1 do 10. Pomocí `continue` příkazu v kombinaci s výrazem `(i < 9)` `continue` se přeskočí příkazy mezi a koncem `for` těla.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [break – příkaz](/cpp/cpp/break-statement-cpp)
