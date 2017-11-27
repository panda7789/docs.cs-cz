---
title: "return (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 90c84b51c6ee57864eac552bc488c9f9c15e9394
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Return – příkaz](/cpp/cpp/return-statement-cpp)  
 [Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)
