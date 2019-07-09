---
title: Return – příkaz - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661618"
---
# <a name="return-c-reference"></a>return (Referenční dokumentace jazyka C#)

`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí řízení volající metodě. Také může vrátit nepovinnou hodnotu. Pokud je metoda `void` typ, `return` příkaz lze vynechat.

 Pokud je příkaz return uvnitř `try` bloku `finally` bloku, pokud existuje, budou spuštěny před ovládací prvek vrátí volajícímu metody.

## <a name="example"></a>Příklad

 V následujícím příkladu metoda `CalculateArea()` vrátí lokální proměnná `area` jako `double` hodnotu.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [return – příkaz](/cpp/cpp/return-statement-cpp)
