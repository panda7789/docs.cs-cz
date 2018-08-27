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
ms.openlocfilehash: 58e5fd72a3748e7af0894093fc461c4efb543608
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925537"
---
# <a name="-operator-c-reference"></a>|| – operátor (Referenční dokumentace jazyka C#)
Operátor podmíněného OR (`||`) provádí logický OR jeho `bool` operandy. Pokud je první operand vyhodnocen jako `true`, není vyhodnocen Druhý operand. Pokud je první operand vyhodnocen jako `false`, druhý operátor určuje, jestli jako celek výraz OR vyhodnocen `true` nebo `false`.  
  
## <a name="remarks"></a>Poznámky  
 Operace  
  
```csharp  
x || y  
```  
  
 odpovídá operaci  
  
```csharp  
x | y  
```  
  
 s výjimkou, že pokud `x` je `true`, `y` není vyhodnocen, protože operace OR `true` bez ohledu na hodnotu `y`. Tento koncept se označuje jako "zkrácené" vyhodnocení.  
  
 Operátor podmíněného OR nemůže být přetížená, ale přetíženími pravidelné logických operátorů a [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) operátorů, s určitými omezeními také považují za přetížení Podmíněné logické operátory.  
  
## <a name="example"></a>Příklad  
 V následujících příkladech, výraz, který používá `||` pouze první operand vyhodnocen jako. Výraz, který používá `|` vyhodnotí oba operandy. V druhém příkladu dojde k výjimce za běhu je-li oba operandy vyhodnocují.  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
