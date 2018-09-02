---
title: goto – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: d4fd9f1f26b82b409d704c45e4bcf18cceef8282
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405813"
---
# <a name="goto-c-reference"></a>goto – příkaz (referenční dokumentace jazyka C#)

`goto` Příkaz předá řízení programu přímo na označený příkaz.

Běžně `goto` je řízení je převedeno na konkrétní popisek případu přepínače nebo výchozí popisek v `switch` příkazu.

`goto` Příkaz je také užitečné využít hluboce vnořený smyčky.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `goto` v [přepnout](switch.md) příkazu.

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `goto` rozdělit z vnořené smyčky.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [goto – příkaz (C++)](/cpp/cpp/goto-statement-cpp)  
- [Jump – příkazy](jump-statements.md)  
