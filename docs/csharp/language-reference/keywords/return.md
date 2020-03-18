---
title: příkaz return - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713128"
---
# <a name="return-c-reference"></a>return (Referenční dokumentace jazyka C#)

Příkaz `return` ukončí provádění metody, ve kterém se zobrazí a vrátí ovládací prvek volající metody. Může také vrátit volitelnou hodnotu. Pokud je metoda `void` typu, `return` příkaz lze vynechat.

 Pokud návrat ový příkaz `try` je `finally` uvnitř bloku, blok, pokud existuje, bude proveden před ovládací prvek vrátí do volající metody.

## <a name="example"></a>Příklad

 V následujícím příkladu `CalculateArea()` vrátí metoda `area` místní `double` proměnnou jako hodnotu.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [return – příkaz](/cpp/cpp/return-statement-cpp)
