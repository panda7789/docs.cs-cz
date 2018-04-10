---
title: '&amp;&amp;Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp;Operátor (referenční dokumentace jazyka C#)
Podmínku – a – operátor (`&&`) provede logickou- a jeho `bool` operandy, ale pouze vyhodnotí svůj druhý operand v případě potřeby.  
  
## <a name="remarks"></a>Poznámky  
 Operaci  
  
```  
x && y  
```  
  
 odpovídá operaci  
  
```  
x & y  
```  
  
 s výjimkou, že pokud `x` je `false`, `y` není vyhodnotit, protože je výsledek operace a `false` bez ohledu na to, jaké hodnota `y` je. To se označuje jako "krátká smyčka –" vyhodnocení.  
  
 Podmínku- a operátor nemůže být přetížené, ale přetížení regulární logické operátory a operátory [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) jsou, s určitými omezeními také považovány za přetížení Podmíněné logické operátory.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, podmíněným výrazem za sekundu `if` příkaz vyhodnocuje pouze první operand, protože operand vrátí `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
