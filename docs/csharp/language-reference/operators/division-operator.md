---
title: "/ – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/ – operátor (Referenční dokumentace jazyka C#)
Operátor dělení (`/`) rozděluje jeho první operand podle jeho Druhý operand. Všechny číselné typy obsahuje předdefinované operátory dělení.  
  
## <a name="remarks"></a>Poznámky  
 Uživatelem definované typy může přetížit `/` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Přetížení `/` operátor implicitně přetížení [/ = – operátor](division-assignment-operator.md).  
  
 Pokud budete provádět dělení dvě celá čísla, výsledkem je vždy celé číslo. Například výsledek 7 / 3 je 2. Chcete-li zjistit zbytek 7 / 3, použijte operátor zbytku ([%](../../../csharp/language-reference/operators/modulus-operator.md)). Pro získání podílu jako racionální číslo nebo zlomek, získat typ dělenec nebo dělitel `float` nebo typ `double`. Typ můžete přiřadit implicitně Pokud express dělenec nebo dělitel jako datový typ decimal umístěním číslice na pravé straně od desetinné čárky, jak ukazuje následující příklad.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
