---
title: '% – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: b906feb22aaec97e58da562b615baae01f3e0719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>% – operátor (Referenční dokumentace jazyka C#)
Operátor zbytku (`%`) vypočítá zbytek po dělení jeho první operand jeho sekundu. Všechny číselné typy obsahuje předdefinované zbývající operátory. 
  
## <a name="remarks"></a>Poznámky  
 Vzorec `a % b` vždy vrátí hodnotu v rozsahu `(-b, b)`, výhradní (nikdy může vrátit `b` nebo `-b`), udržování znaménko dělenec. Pro dělení celého čísla, operátor zbytku splňuje pravidlo `a % b = a - (a / b) * b`.
  
 Toto je Nezaměňovat s kanonický numerického zbytku, který splňuje požadavky podobné pravidlo, ale s floored dělení a vrací hodnoty v rozsahu `[0, b)`. C# nemá operátor numerického zbytku kanonickém tvaru. Chování je však pro pozitivní dividendy stejný.
  
 Uživatelem definované typy může přetížit `%` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si zaokrouhlovací chyby související s typ double.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
