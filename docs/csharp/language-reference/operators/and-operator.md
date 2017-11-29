---
title: "&amp;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eceee8e01ba46f65c6b182a40d14e62aaba5dd53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;Operátor (referenční dokumentace jazyka C#)
& Operátor může fungovat jako unární operátor nebo binární operátor.  
  
## <a name="remarks"></a>Poznámky  
 Operátor unární & vrátí adresu jeho operand (vyžaduje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu).  
  
 Binární & operátory jsou předdefinovány pro integrální typy a `bool`. Pro integrální typy & vypočítá logické bitové operace AND z operandů. Pro `bool` operandy & výpočtů logické a operandů; výsledek je `true` Pokud jsou obě jejími operandy `true`.  
  
 `&` Operátor vyhodnotí oba operátory bez ohledu na první z nich je hodnota. Příklad:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Uživatelem definované typy může přetížit binárního souboru `&` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Operace u celočíselných typů jsou obecně povoleny na výčtu. Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
