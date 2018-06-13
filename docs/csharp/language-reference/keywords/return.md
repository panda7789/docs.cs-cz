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
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266107"
---
# <a name="return-c-reference"></a>return (Referenční dokumentace jazyka C#)
`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí prvek volání metody. Také se může vrátit Volitelná hodnota. Pokud je metoda `void` typu, `return` příkaz lze vynechat.  
  
 Pokud je příkaz return uvnitř `try` bloku, `finally` bloku, pokud existuje, bude proveden před voláním metody vrátí ovládací prvek.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu metoda `CalculateArea()` vrátí místní proměnné `area` jako [dvojité](../../../csharp/language-reference/keywords/double.md) hodnotu.  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [return – příkaz](/cpp/cpp/return-statement-cpp)  
 [Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)
