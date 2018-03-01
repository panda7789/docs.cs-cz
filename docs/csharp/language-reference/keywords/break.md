---
title: "break (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b533d325be41683ed6f56e9e63b3c11ddde9cb17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="break-c-reference"></a>break (Referenční dokumentace jazyka C#)
`break` Příkaz ukončí nejbližší nadřazených smyčky nebo [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz, ve kterém se zobrazí. Ovládací prvek předává do příkazu, který následuje ukončenou příkaz, pokud existuje.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu obsahuje příkaz podmíněného čítač, který by měl počítat od 1 do 100; ale `break` příkaz ukončí smyčky po 4 počty.  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `break` se použije příkaz k přerušení mimo smyčky vnořené vnitřní a vnější smyčky vrácení řízení.  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje použití `break` v [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz.  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 Pokud jste zadali `4`, bude výstup:  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [přepínače](../../../csharp/language-reference/keywords/switch.md)  
 [Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)  
 [Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)
