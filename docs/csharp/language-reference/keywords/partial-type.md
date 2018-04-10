---
title: partial (typ) (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5212984cc577ce05fc4697e0d648fb5545528562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="partial-type-c-reference"></a>partial (typ) (Referenční dokumentace jazyka C#)
Aby se daly rozdělit do několika souborů umožňují definice třídy, struktury nebo rozhraní definice částečné typu.  
  
 V File1.cs:  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 V deklaraci File2.cs:  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Rozdělení třídu, struktura nebo rozhraní typ přes několik souborů může být užitečná při práci velkých projektech nebo s automaticky generovaného kódu, například poskytnutá [Návrhář formulářů Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Částečné typ může obsahovat [částečné metoda](../../../csharp/language-reference/keywords/partial-method.md). Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)
