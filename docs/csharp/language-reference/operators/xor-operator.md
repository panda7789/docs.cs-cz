---
title: ^ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>^ – operátor (Referenční dokumentace jazyka C#)
Binární `^` jsou operátory předdefinovány pro integrální typy a `bool`. Pro integrální typy `^` vypočítá bitový exkluzivní disjunkce OR z operandů. Pro `bool` operandy, `^` vypočítá logické exkluzivní- nebo operandů; výsledek je `true` jenom v případě právě jeden z jeho operandy je `true`.  
  
## <a name="remarks"></a>Poznámky  
 Uživatelem definované typy může přetížit `^` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Operace u celočíselných typů jsou obecně povoleny na výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 Výpočet z `0xf8 ^ 0x3f` v předchozím příkladu provede bitové exkluzivní disjunkce OR následující dvě binárních hodnot, které odpovídají hexadecimální hodnoty F8 a 3F:  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Výsledkem exkluzivní disjunkce OR je `1100 0111`, což je C7 v šestnáctkové soustavě.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
