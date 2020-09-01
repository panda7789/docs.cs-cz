---
description: goto – příkaz – reference jazyka C#
title: goto – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128423"
---
# <a name="goto-c-reference"></a>goto – příkaz (referenční dokumentace jazyka C#)

`goto`Příkaz přenáší ovládací prvek program přímo na označený příkaz.

Běžné použití aplikace `goto` je pro přenos řízení na konkrétní návěští přepínače Case nebo jako výchozí popisek v `switch` příkazu.

`goto`Příkaz je také užitečný pro získání nehluboce vnořených smyček.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `goto` příkazu v příkazu [Switch](switch.md) .

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `goto` k přerušení z vnořených smyček.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [goto – příkaz (C++)](/cpp/cpp/goto-statement-cpp)
