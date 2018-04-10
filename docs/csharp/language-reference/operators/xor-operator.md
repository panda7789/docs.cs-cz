---
title: ^ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4ccd32ea8abd8ca3252380083eafecad2b572ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
