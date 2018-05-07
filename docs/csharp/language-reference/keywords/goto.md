---
title: goto – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 2dd70a30b885dcdae9637b02e8c34ac39f4879fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [ – příkaz](/cpp/cpp/goto-statement-cpp)  
 [Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)
