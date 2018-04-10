---
title: '|| – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
