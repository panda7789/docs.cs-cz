---
title: + – Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: d4a269c07e0d6dc2ac6a6a101f200653c6ea7a29
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244868"
---
# <a name="-operator-c-reference"></a>+ – operátor (Referenční dokumentace jazyka C#)
`+` Operátor může fungovat jako unární nebo binární operátor.  
  
## <a name="remarks"></a>Poznámky  
 Unární `+` operátory jsou předdefinované pro všechny číselné typy. Výsledek unární `+` operace na číselný typ je hodnota operandu.  
  
 Binární `+` operátory jsou předdefinované typy číselným a řetězcovým. Pro číselné typy a vypočítá součet dvou operandů. Pokud jeden nebo oba operandy jsou typu řetězec + zřetězí řetězcové reprezentace operandy.  
  
 Typy delegátů také poskytují binární soubor `+` operátor, který provádí řetězení delegáta.  
  
 Uživatelem definované typy mohou přetížit unární `+` a binární `+` operátory. Operace interních typů jsou obecně povoleny na výčet. Další informace najdete v tématu [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [– Operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)
