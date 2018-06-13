---
title: / – operátor (Referenční dokumentace jazyka C#)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 9d0bbff1fd9f4ab3c93c879d12ccd5fde1187b44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272568"
---
# <a name="-operator-c-reference"></a>/ – operátor (Referenční dokumentace jazyka C#)
Operátor dělení (`/`) rozděluje jeho první operand podle jeho Druhý operand. Všechny číselné typy obsahuje předdefinované operátory dělení.
  
## <a name="remarks"></a>Poznámky  
 Uživatelem definované typy může přetížit `/` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Přetížení `/` operátor implicitně přetížení [/ = – operátor](division-assignment-operator.md).  
  
 Pokud budete provádět dělení dvě celá čísla, výsledkem je vždy celé číslo. Například výsledek 7 / 3 je 2. Toto je Nezaměňovat s floored dělení, jako `/` operátor zaokrouhlí směrem k nule: -7 -2 je 3.  
  
 Chcete-li získat koeficient jako racionální číslo, použijte `float`, `double`, nebo `decimal` typy. Existuje celá řada způsobů pro převod mezi [součástí číselnými typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 K určení zbývající, použijte [operátor zbytku](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
