---
title: příkaz return – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713128"
---
# <a name="return-c-reference"></a>return (Referenční dokumentace jazyka C#)

Příkaz `return` ukončí provádění metody, ve které se vyskytuje, a vrátí řízení volající metodě. Může také vracet volitelnou hodnotu. Pokud je metoda typu `void`, příkaz `return` lze vynechat.

 Pokud je příkaz return uvnitř bloku `try`, `finally` blok, pokud existuje, se spustí před tím, než se ovládací prvek vrátí volající metodě.

## <a name="example"></a>Příklad

 V následujícím příkladu metoda `CalculateArea()` vrátí místní proměnnou `area` jako `double`ovou hodnotu.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [return – příkaz](/cpp/cpp/return-statement-cpp)
