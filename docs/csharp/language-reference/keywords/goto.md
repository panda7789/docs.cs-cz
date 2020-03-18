---
title: příkaz goto - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715276"
---
# <a name="goto-c-reference"></a>goto – příkaz (referenční dokumentace jazyka C#)

Příkaz `goto` přenese ovládací prvek programu přímo do popiskovaného příkazu.

Běžné použití `goto` je převést řízení na konkrétní popisek switch-case `switch` nebo výchozí popisek v příkazu.

Příkaz `goto` je také užitečné se dostat z hluboce vnořené smyčky.

## <a name="example"></a>Příklad

Následující příklad ukazuje `goto` použití v [příkazu switch.](switch.md)

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `goto` použití vymanit se z vnořené smyčky.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [goto – příkaz (C++)](/cpp/cpp/goto-statement-cpp)
