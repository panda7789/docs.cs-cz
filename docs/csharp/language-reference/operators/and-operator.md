---
title: '&amp; Operátor (referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="amp-operator-c-reference"></a>&amp; Operátor (referenční dokumentace jazyka C#)
`&` Operátor může fungovat jako unární operátor nebo binární operátor.  
  
## <a name="remarks"></a>Poznámky  
 Unární `&` operátor vrátí adresu jeho operand (vyžaduje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu).  
  
 Binární `&` jsou operátory předdefinovány pro integrální typy a `bool`. Pro integrální typy & vypočítá logické bitové operace AND z operandů. Pro `bool` operandy & výpočtů logické a operandů; výsledek je `true` Pokud jsou obě jejími operandy `true`.  
  
 Binárního souboru `&` operátor vyhodnotí oba operátory bez ohledu na první z nich je hodnotu, na rozdíl od [operátor podmíněného AND](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`. Příklad:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Uživatelem definované typy může přetížit binárního souboru `&` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Operace u celočíselných typů jsou obecně povoleny na výčtu. Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
