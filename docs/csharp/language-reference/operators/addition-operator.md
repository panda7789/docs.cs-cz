---
title: "+ Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b15d5d1a304569b92b2f811a9ea714e4b30d60d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>+ – operátor (Referenční dokumentace jazyka C#)
`+` Operátor může fungovat jako unární operátor nebo binární operátor.  
  
## <a name="remarks"></a>Poznámky  
 Unární `+` jsou operátory předdefinovány pro všechny číselné typy. Výsledek unární operátor `+` je právě hodnota operand operace na číselného typu.  
  
 Binární `+` jsou operátory předdefinovány pro typy číselný a řetězec. Pro číselné typy + vypočítá součet jeho dva operandy. Pokud jeden nebo oba operandy jsou typu řetězec + zřetězí řetězcové vyjádření operandy.  
  
 Typy delegáta také poskytují binární `+` operátor, který provádí zřetězení delegáta.  
  
 Uživatelem definované typy může přetížit unární `+` a binární `+` operátory. Operace u celočíselných typů jsou obecně povoleny na výčtu. Další informace najdete v tématu [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)
