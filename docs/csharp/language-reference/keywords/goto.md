---
title: goto – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa12a7547cfcd4a2076b5b0a308139f8a823f482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="goto-c-reference"></a>goto – příkaz (referenční dokumentace jazyka C#)
`goto` Příkaz přenáší prvku aplikace přímo do příkaz s popiskem.  
  
 Běžně se používají `goto` je přenos řízení na konkrétní případy switch popisek nebo výchozí štítek v `switch` příkaz.  
  
 `goto` Příkaz je také užitečné ze hluboko vložené smyčky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí `goto` v [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz.  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí `goto` pro přerušení z vnořené smyčky.  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [goto – příkaz](/cpp/cpp/goto-statement-cpp)  
 [Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)
