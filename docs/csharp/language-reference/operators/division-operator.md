---
title: / – operátor (Referenční dokumentace jazyka C#)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: bddf6d234f3536ad64f0cd876cc7ade4494916d9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935157"
---
# <a name="-operator-c-reference"></a>/ – operátor (Referenční dokumentace jazyka C#)
Operátor dělení (`/`) rozděluje svůj první operand tak svým druhým operandem. Všechny číselné typy obsahuje předdefinované operátory dělení.
  
## <a name="remarks"></a>Poznámky  
 Lze přetěžovat uživatelsky definované typy `/` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Přetížení `/` implicitně přetížení operátoru [/ = – operátor](division-assignment-operator.md).  
  
 Při dělení dvou celých čísel, výsledek je vždycky celé číslo. Například výsledek 7 / 3 je 2. Toto je nezaměňovat floored dělení, jako `/` operátor zaokrouhlí směrem k nule.: -7 / 3 -2.  
  
 Chcete-li získat podíl racionální číslo as, použijte `float`, `double`, nebo `decimal` typy. Existuje mnoho způsobů, jak převést mezi [integrovaným číselné typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 Chcete-li určit zbývající, použijte [operátor zbytku](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
