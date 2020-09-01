---
description: Return – příkaz – reference jazyka C#
title: Return – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136995"
---
# <a name="return-c-reference"></a>return (Referenční dokumentace jazyka C#)

`return`Příkaz ukončí provádění metody, ve které se vyskytuje, a vrátí řízení volající metodě. Může také vracet volitelnou hodnotu. Pokud je metoda `void` typu, je `return` možné příkaz vynechat.

 Pokud je příkaz return uvnitř bloku, `try` `finally` blok, pokud existuje, bude proveden před tím, než se ovládací prvek vrátí volající metodě.

## <a name="example"></a>Příklad

 V následujícím příkladu metoda `CalculateArea()` vrátí místní proměnnou `area` jako `double` hodnotu.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Return – příkaz](/cpp/cpp/return-statement-cpp)
