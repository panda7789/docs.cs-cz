---
title: "== – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>== – operátor (Referenční dokumentace jazyka C#)
Pro předdefinované typy hodnot, operátor rovnosti (`==`) vrátí hodnotu true, pokud hodnoty jejími operandy, jsou stejné, `false` jinak. Pro odkaz na typy jiné než [řetězec](../../../csharp/language-reference/keywords/string.md), `==` vrátí `true` pokud jeho dva operandy odkazují na stejný objekt. Pro `string` typu `==` porovnává hodnoty řetězce.  
  
## <a name="remarks"></a>Poznámky  
 Typy hodnotu definovanou uživatelem může přetížit `==` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Proto můžete odkaz na uživatelem definované typy, i když ve výchozím nastavení `==` chová, jak je popsáno výše pro oba typy předdefinované a vlastní odkaz. Pokud `==` je přetížena [! =](../../../csharp/language-reference/operators/not-equal-operator.md) také musí být přetížený. Operace u celočíselných typů jsou obecně povoleny na výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
