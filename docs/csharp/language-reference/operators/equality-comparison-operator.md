---
title: == – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: f8356320817771cb559192c1ce720a80bf33bbf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>== – operátor (Referenční dokumentace jazyka C#)
Pro předdefinované typy hodnot, operátor rovnosti (`==`) vrátí hodnotu true, pokud hodnoty jejími operandy, jsou stejné, `false` jinak. Pro odkaz na typy jiné než [řetězec](../../../csharp/language-reference/keywords/string.md), `==` vrátí `true` pokud jeho dva operandy odkazují na stejný objekt. Pro `string` typu `==` porovnává hodnoty řetězce.  
  
## <a name="remarks"></a>Poznámky  
 Typy hodnotu definovanou uživatelem může přetížit `==` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Proto můžete odkaz na uživatelem definované typy, i když ve výchozím nastavení `==` chová, jak je popsáno výše pro oba typy předdefinované a vlastní odkaz. Pokud `==` je přetížena [! =](../../../csharp/language-reference/operators/not-equal-operator.md) také musí být přetížený. Operace u celočíselných typů jsou obecně povoleny na výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
