---
title: '! = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 15f1b5930117e608644a58343fb855562f36b21c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237815"
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
