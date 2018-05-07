---
title: '|| – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: ce0834874f9c5b4c5154a798492600d6ac45a4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>|| – operátor (Referenční dokumentace jazyka C#)
Operátor podmíněného OR (`||`) provede logickou funkcí – nebo jeho `bool` operandy. Pokud je výsledkem první operand `true`, druhý operand, nebude hodnocen. Pokud je výsledkem první operand `false`, druhý operátor určuje, zda výraz OR jako celek vyhodnotí `true` nebo `false`.  
  
## <a name="remarks"></a>Poznámky  
 Operaci  
  
```  
x || y  
```  
  
 odpovídá operaci  
  
```  
x | y  
```  
  
 s výjimkou, že pokud `x` je `true`, `y` není vyhodnotit, protože operace nebo je `true` bez ohledu na hodnotu `y`. Tento koncept se označuje jako "krátká smyčka –" vyhodnocení.  
  
 Operátor podmíněného OR nemohou být přetíženy, ale přetížení regulární logických operátorů a [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) operátory se s určitými omezeními také považuje za přetížení Podmíněné logické operátory.  
  
## <a name="example"></a>Příklad  
 V následujících příkladech výraz, který používá `||` vyhodnotí pouze první operand. Výraz, který používá `|` vyhodnotí oba operandy. V druhém příkladu došlo k výjimce běhu Pokud oba operandy, jsou vyhodnoceny.  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
