---
title: == – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: d9d7dcf3b38939e681fb51d6c674151cee78b3d0
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254167"
---
# <a name="-operator-c-reference"></a>== – operátor (Referenční dokumentace jazyka C#)
Pro předdefinované typy hodnot, operátor rovnosti (`==`) vrací hodnotu true, pokud jsou si rovny, hodnoty jeho operandy `false` jinak. Pro odkaz na typy jiné než [řetězec](../../../csharp/language-reference/keywords/string.md), `==` vrátí `true` Pokud dva operandy odkazují na stejný objekt. Pro `string` typ `==` porovnává hodnoty řetězce.  
  
## <a name="remarks"></a>Poznámky  
 Mohou přetížit typy hodnotu definovanou uživatelem `==` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)). Proto můžete typy odkazů definované uživatelem, i když se ve výchozím nastavení `==` chová, jak je popsáno výše u obou typů předdefinované a vlastní odkaz. Pokud `==` je přetížena, [! =](../../../csharp/language-reference/operators/not-equal-operator.md) musí také být přetíženy. Operace interních typů jsou obecně povoleny na výčet.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
