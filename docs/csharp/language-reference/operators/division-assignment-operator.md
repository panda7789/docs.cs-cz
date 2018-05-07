---
title: /= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 1d9b918c66ce361067d906a055df5adb25a5a308
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>/= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení dělení.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `/=` operátor přiřazení, jako například  
  
```  
x /= y  
```  
  
 je ekvivalentem  
  
```  
x = x / y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [Nebo operátor](../../../csharp/language-reference/operators/division-operator.md) je předdefinovaná pro číselné typy provádět dělení.  
  
 `/=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [nebo operátor](../../../csharp/language-reference/operators/division-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Na všechny složené operátory přiřazení přetížení binární operátor implicitně přetížení ekvivalentní složeného přiřazení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
