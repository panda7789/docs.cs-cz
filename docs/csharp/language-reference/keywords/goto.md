---
title: goto – příkaz C# – reference
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715276"
---
# <a name="goto-c-reference"></a>goto – příkaz (referenční dokumentace jazyka C#)

Příkaz `goto` přenáší ovládací prvek program přímo na označený příkaz.

Běžné použití `goto` je přenášet řízení na konkrétní popisek Case přepínače nebo výchozí popisek v příkazu `switch`.

Příkaz `goto` je také užitečný k získání z hluboce vnořených smyček.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `goto` v příkazu [Switch](switch.md) .

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `goto` k přerušení z vnořených smyček.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [goto – příkaz (C++)](/cpp/cpp/goto-statement-cpp)
