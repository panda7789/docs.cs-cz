---
title: '&amp;&amp; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388290"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; – Operátor (referenční dokumentace jazyka C#)
Podmíněným – a – operátor (`&&`) provádí logické- a jeho `bool` operandy, ale pouze vyhodnocuje svým druhým operandem, v případě potřeby.  
  
## <a name="remarks"></a>Poznámky  
 Operace  
  
```csharp  
x && y  
```  
  
 odpovídá operaci  
  
```csharp  
x & y  
```  
  
 s výjimkou, že pokud `x` je `false`, `y` není vyhodnocen, protože výsledek operace AND je `false` bez ohledu na to, jaké hodnoty `y` je. To se označuje jako "zkrácené" vyhodnocení.  
  
 Podmíněným – a operátor nemůže být přetížená, ale přetíženími pravidelné logické operátory a operátory [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) , s určitými omezeními také považují přetížení Podmíněné logické operátory.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, podmíněný výraz ve druhém `if` příkaz vyhodnocuje pouze první operand, protože operand vrací `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
