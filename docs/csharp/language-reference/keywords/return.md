---
title: return (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 1b6a1ce2a8587c8630fece3d5c9a2186fbbc9c22
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001473"
---
# <a name="return-c-reference"></a>return (Referenční dokumentace jazyka C#)
`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí řízení volající metodě. Také může vrátit nepovinnou hodnotu. Pokud je metoda `void` typ, `return` příkaz lze vynechat.  
  
 Pokud je příkaz return uvnitř `try` bloku `finally` bloku, pokud existuje, budou spuštěny před ovládací prvek vrátí volajícímu metody.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu metoda `CalculateArea()` vrátí lokální proměnná `area` jako [double](../../../csharp/language-reference/keywords/double.md) hodnotu.  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [return – příkaz](/cpp/cpp/return-statement-cpp)  
- [Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)
