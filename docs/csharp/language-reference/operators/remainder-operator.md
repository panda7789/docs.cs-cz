---
title: '% – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 477f2491e6d2efe6b5c327efb371843d0bf12c26
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723870"
---
# <a name="-operator-c-reference"></a>% – operátor (Referenční dokumentace jazyka C#)
Operátor zbytku (`%`) vypočítá zbytek po dělení svůj první operand jeho sekundu. Všechny číselné typy obsahuje předdefinované operátory zbytek. 
  
## <a name="remarks"></a>Poznámky  
 Vzorec `a % b` vždy vrátí hodnotu v rozsahu `(-b, b)`exkluzivní (nikdy může vrátit `b` nebo `-b`), vedení znaménko podíl. Operátor zbytku pro dělení celého čísla splňuje pravidlo `a % b = a - (a / b) * b`.
  
 Toto je Nezaměňovat s canonical modulus, které splňuje pravidlo podobné, ale s floored dělení a vrací hodnoty v rozsahu `[0, b)`. C# nemá operátor numerického zbytku canonical. Chování je však stejný pro pozitivní dividendy.
  
 Lze přetěžovat uživatelsky definované typy `%` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si zaokrouhlovací chyby související s typem double.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
