---
title: '!= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e409e2a80886fd5f7f4cdbeaa9b4e3325f8a967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>!= – operátor (Referenční dokumentace jazyka C#)
Operátor nerovnosti (`!=`) vrátí hodnotu false, pokud jejími operandy, jsou stejné, jinak hodnotu true. Operátory nerovnosti jsou předdefinovány pro všechny typy, včetně řetězec a objekt. Uživatelem definované typy může přetížit `!=` operátor.  
  
## <a name="remarks"></a>Poznámky  
 Pro předdefinované typy hodnot, operátor nerovnosti (`!=`) vrátí hodnotu true, pokud jsou hodnoty jejími operandy, jiný, false, jinak hodnota. Pro odkaz na typy jiné než `string`, `!=` vrátí hodnotu true, pokud jeho dva operandy odkazovat na jiné objekty. Pro `string` typu `!=` porovnává hodnoty řetězce.  
  
 Typy hodnotu definovanou uživatelem může přetížit `!=` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Proto můžete odkaz na uživatelem definované typy, i když ve výchozím nastavení `!=` chová, jak je popsáno výše pro oba typy předdefinované a vlastní odkaz. Pokud `!=` je přetížena [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) také musí být přetížený. Operace u celočíselných typů jsou obecně povoleny na výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
