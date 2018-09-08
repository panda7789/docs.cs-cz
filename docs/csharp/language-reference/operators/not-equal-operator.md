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
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192012"
---
# <a name="-operator-c-reference"></a>!= – operátor (Referenční dokumentace jazyka C#)
Operátor nerovnosti (`!=`) vrací hodnotu false, pokud jeho operandy jsou stejné, jinak hodnotu true. Pro všechny typy, včetně řetězce a objektu jsou předdefinované operátory nerovnost. Lze přetěžovat uživatelsky definované typy `!=` operátor.  
  
## <a name="remarks"></a>Poznámky  
 Pro předdefinované typy hodnot, operátor nerovnosti (`!=`) vrací hodnotu true, pokud jsou hodnoty jeho operandy různých, false, jinak. Pro odkaz na typy jiné než `string`, `!=` vrací true, pokud dva operandy odkazují na různé objekty. Pro `string` typ `!=` porovnává hodnoty řetězce.  
  
 Mohou přetížit typy hodnotu definovanou uživatelem `!=` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)). Proto můžete typy odkazů definované uživatelem, i když se ve výchozím nastavení `!=` chová, jak je popsáno výše u obou typů předdefinované a vlastní odkaz. Pokud `!=` je přetížena, [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) musí také být přetíženy. Operace interních typů jsou obecně povoleny na výčet.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
